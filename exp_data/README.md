File names:
- histograms_1n_00087.root
- histograms_1n_000923.root
- histograms_1n_00175.root

Information:
- Reaction: 124Sn + 208Pb ---> 123Sn + 208Pb + n
- Beam energy: 904 MeV/u
- Beam energy at the target: 883 MeV/u
- Outgoing neutron energy: 30 MeV (at fragment reference frame)
- Saturation factor:
    * 0.00087
    * 0.000923
    * 0.00175

PhaseSpaceGenerator code:
```cpp
auto gen = std::make_unique<R3BPhaseSpaceGenerator>();
gen->Beam.SetEnergyDistribution(R3BDistribution1D::Delta(883.));
gen->SetErelDistribution(R3BDistribution1D::Flat(0.,10000.));
// at least two particles are required; it will add their energy
// and make an InitVec(0,0,0,TotE_GeV) - this information is needed
// for SetDecay()
gen->AddParticle(50,123);
gen->AddParticle(2112);
// Dump the User settings
primGen->AddGenerator(gen.release());
```
