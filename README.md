<div align="center">

# ⚡ Power Electronics & High Voltage

**LTspice studies of high-voltage generation — voltage doublers and cascaded test transformers — the HV side of my power-electronics work.**

![LTspice](https://img.shields.io/badge/sim-LTspice-0072C6)
![HV](https://img.shields.io/badge/topic-high%20voltage-e0af68)
![Power](https://img.shields.io/badge/topic-power%20electronics-9ece6a)

</div>

> **RU:** Моделирование высоковольтных схем в LTspice: удвоитель напряжения и каскадный испытательный трансформатор (курс «Техника высоких напряжений», KTÜ).
> **TR:** LTspice'ta yüksek gerilim devreleri: gerilim katlayıcı ve kaskad test transformatörü (Yüksek Gerilim Tekniği dersi, KTÜ).

## 🔬 Circuits

| File | Circuit | Simulation |
|---|---|---|
| [`AC_DC_doubler_voltage.asc`](circuits_ltspice/AC_DC_doubler_voltage.asc) | 10 V / 50 Hz source → 1:5 step-up transformer → 2× 1N4007 + 2× 2200 µF voltage doubler → 1 kΩ load | `.tran 0.5 s` |
| [`cascade_hv_transformer.asc`](circuits_ltspice/cascade_hv_transformer.asc) | 3-stage cascaded HV test transformer, 10 mH : 1 H per stage, secondaries in series-aiding | `.tran 0.2 s` + `.meas` of V<sub>pp</sub>, V<sub>rms</sub>, I<sub>rms</sub> |

**Doubler:** each half-cycle charges one capacitor to the peak, so the DC output is ideally
$V_{DC} \approx 2\,\hat V_{sec} - 2V_F$, with ripple $\Delta V \approx I_{load}/(f\,C)$.

**Cascade:** stage $k$ is fed from the tertiary of stage $k-1$, so the output is ideally $V_{out} \approx N\cdot V_{stage}$ for $N$ stages.
Insulation of each stage is only rated for one stage voltage — that is why test transformers are cascaded.

Open the `.asc` files in LTspice and run.

## 🛣️ Next
- [ ] Cockcroft–Walton (Greinacher) multiplier: ripple and voltage drop vs. number of stages
- [ ] Impulse voltage generator (Marx), 1.2/50 µs waveform
- [ ] Gate drive and switching losses of an IGBT half-bridge (link to my EMS levitation driver)
