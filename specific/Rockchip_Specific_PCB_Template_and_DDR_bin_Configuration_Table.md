# Rockchip_Specific_PCB_Template_and_DDR_bin_Configuration_Table.md
### RK3326

| PCB Template                                                | DDRBIN                                       | Note                                                         |
| ----------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------ |
| RK3326_Template_LP3Q296P132SS414_<br/>V10_20251226_1048_JZY | rk3326_ddr_296ball_lp3_<br/>333MHz_vx.xx.bin | 除了DDRBIN需要特殊替换外，还需要额外修改kernel里px30-dram-default-timing.dtsi 配置。 |

kernel 里额外修改补丁如下：

```c
diff --git a/arch/arm64/boot/dts/rockchip/px30-dram-default-timing.dtsi b/arch/arm64/boot/dts/rockchip/px30-dram-default-timing.dtsi
index 99fb02048c82..c1ac70ece66e 100644
--- a/arch/arm64/boot/dts/rockchip/px30-dram-default-timing.dtsi
+++ b/arch/arm64/boot/dts/rockchip/px30-dram-default-timing.dtsi
@@ -54,10 +54,10 @@ ddr_timing: ddr_timing {
                lpddr3_odt_dis_freq = <400>;
                phy_lpddr3_odt_dis_freq = <400>;
                lpddr3_drv = <LP3_DS_40ohm>;
-               lpddr3_odt = <LP3_ODT_240ohm>;
-               phy_lpddr3_ca_drv = <PHY_DDR4_LPDDR3_2_RON_RTT_34ohm>;
-               phy_lpddr3_ck_drv = <PHY_DDR4_LPDDR3_2_RON_RTT_43ohm>;
-               phy_lpddr3_dq_drv = <PHY_DDR4_LPDDR3_2_RON_RTT_34ohm>;
+               lpddr3_odt = <LP3_ODT_120ohm>;
+               phy_lpddr3_ca_drv = <PHY_DDR4_LPDDR3_2_RON_RTT_48ohm>;
+               phy_lpddr3_ck_drv = <PHY_DDR4_LPDDR3_2_RON_RTT_48ohm>;
+               phy_lpddr3_dq_drv = <PHY_DDR4_LPDDR3_2_RON_RTT_48ohm>;
                phy_lpddr3_odt = <PHY_DDR4_LPDDR3_2_RON_RTT_240ohm>;

                lpddr4_odt_dis_freq = <800>;
```

------

### RK3566

| PCB Template                                                 | DDRBIN                                         | Note                                                         |
| ------------------------------------------------------------ | ---------------------------------------------- | ------------------------------------------------------------ |
| RK3566_Template_LP3D178P232DD414_43R0X25R0_<br/>666MHZ_1056MHZ_H1R6_V10_20251125SQJ | rk3566_ddr_2x178ball_lp3_<br/>666MHz_vx.xx.bin | DDRBIN默认666MHz(1333Mbps)，当仅贴1颗LP3时最高可通过ddrbin_tool修改到1056MHz(颗粒也需要支持1056MHz) |



------

### RK3562

| PCB Template                                                 | DDRBIN                                       | Note                                                         |
| ------------------------------------------------------------ | -------------------------------------------- | ------------------------------------------------------------ |
| RK3562_Template_LP3Q296P164SS61346_<br/>38R7x30R3_1066Mbps_H1R6_V10_20251204 | rk3562_ddr_296ball_lp3_<br/>528MHz_vx.xx.bin |                                                              |
| RK3562_Template_LP3D178P232DD414_38R0X25R0<br/>_1332Mbps_2112Mbps_H1R6_V10_20251217SQJ | rk3562_ddr_296ball_lp3_<br/>528MHz_vx.xx.bin | DDRBIN默认528MHz(1056Mbps)，当贴2颗LP3时可通过ddrbin_tool修改到666MHz，贴1颗时最高可修改到1056MHz(颗粒也需要支持1056MHz) |

------

