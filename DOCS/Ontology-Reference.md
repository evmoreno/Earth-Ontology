# Earth #

## Classes
- Earth: The planet we live on.
- Atmosphere: The layer of gases that surrounds the Earth.
- Lithosphere: The solid, outermost layer of the Earth.
- Hydrosphere: The water on the Earth's surface and in the atmosphere.
- Biosphere: All living things on Earth and their interactions with the other spheres.

## Properties
- hasAtmosphere: Relates the Earth to its atmosphere.
- hasLithosphere: Relates the Earth to its lithosphere.
- hasHydrosphere: Relates the Earth to its hydrosphere.
- hasBiosphere: Relates the Earth to its biosphere.

## Subclasses
- Troposphere: The lowest layer of the Earth's atmosphere, where weather occurs.
- Stratosphere: The layer above the troposphere where the ozone layer is located.
- Mesosphere: The layer above the stratosphere where meteors burn up.
- Thermosphere: The layer above the mesosphere where the Northern and Southern Lights occur.
- Exosphere: The outermost layer of the atmosphere, where gases gradually thin out and merge with space.
- Crust: The outermost layer of the lithosphere.
- Mantle: The layer of the Earth between the crust and the core.
- Core: The innermost layer of the Earth, consisting of a solid inner core and a liquid outer core.
- Ocean: A large body of saltwater that covers most of the Earth's surface.
- Lake: A body of water surrounded by land.
- River: A natural waterway that flows towards the ocean.
- Glacier: A large mass of ice that moves slowly over land.
- Forest: A large area covered in trees and undergrowth.
- Grassland: An area covered in grass and other non-woody plants.
- Desert: A dry, arid region with little precipitation.
- Mountain: A large landform that rises steeply above its surroundings.

## Relationships
- isPartOf: Relates a subclass to its superclass.
- isLocatedIn: Relates a subclass to its location within the Earth.
- interactsWith: Relates the biosphere to the other spheres of the Earth.


# Atmosphere

## Classes
- Atmosphere: The layer of gases that surrounds the Earth.
- Troposphere: The lowest layer of the atmosphere, where weather occurs.
- Stratosphere: The layer above the troposphere where the ozone layer is located.
- Mesosphere: The layer above the stratosphere where meteors burn up.
- Thermosphere: The layer above the mesosphere where the Northern and Southern Lights occur.
- Exosphere: The outermost layer of the atmosphere, where gases gradually thin out and merge with space.
- Air: A mixture of gases that makes up the atmosphere.
- Oxygen: A gas that makes up about 21% of the atmosphere and is necessary for life.
- Nitrogen: A gas that makes up about 78% of the atmosphere.
- Carbon Dioxide: A greenhouse gas that makes up a small but significant portion of the atmosphere.
- Ozone: A gas that makes up a small but important portion of the atmosphere and helps to protect life on Earth from harmful ultraviolet radiation.
- Water Vapor: The gaseous form of water that makes up a variable amount of the atmosphere.

## Properties
- hasTroposphere: Relates the atmosphere to its troposphere.
- hasStratosphere: Relates the atmosphere to its stratosphere.
- hasMesosphere: Relates the atmosphere to its mesosphere.
- hasThermosphere: Relates the atmosphere to its thermosphere.
- hasExosphere: Relates the atmosphere to its exosphere.
- hasAir: Relates the atmosphere to the mixture of gases that make it up.
- hasOxygen: Relates the atmosphere to the gas oxygen.
- hasNitrogen: Relates the atmosphere to the gas nitrogen.
- hasCarbonDioxide: Relates the atmosphere to the gas carbon dioxide.
- hasOzone: Relates the atmosphere to the gas ozone.
- hasWaterVapor: Relates the atmosphere to the gas water vapor.

## Relationships
- isPartOf: Relates a subclass to its superclass.
- isLocatedIn: Relates a subclass to its location within the Earth.


# Lithosphere

## Classes
- Lithosphere: The solid, outermost layer of the Earth.
- Crust: The outermost layer of the lithosphere.
- Mantle: The layer of the Earth between the crust and the core.
- Core: The innermost layer of the Earth, consisting of a solid inner core and a liquid outer core.
- IgneousRock: A type of rock that forms from the solidification of molten material.
- SedimentaryRock: A type of rock that forms from the accumulation and cementation of sediment.
- MetamorphicRock: A type of rock that forms from the alteration of pre-existing rock due to heat, pressure, or chemical processes.
- Mineral: A naturally occurring inorganic substance with a characteristic chemical composition and crystal structure.
- Soil: The upper layer of the Earth's crust, composed of a mixture of organic and inorganic materials and capable of supporting plant life.
- Plate: A rigid, flat section of the Earth's lithosphere that moves relative to other plates.

## Properties
- hasCrust: Relates the lithosphere to its crust.
- hasMantle: Relates the lithosphere to its mantle.
- hasCore: Relates the lithosphere to its core.
- hasIgneousRock: Relates the lithosphere to igneous rock.
- hasSedimentaryRock: Relates the lithosphere to sedimentary rock.
- hasMetamorphicRock: Relates the lithosphere to metamorphic rock.
- hasMineral: Relates the lithosphere to minerals.
- hasSoil: Relates the lithosphere to soil.
- hasPlate: Relates the lithosphere to tectonic plates.

## Subclasses
- OceanicCrust: The portion of the Earth's crust that lies beneath the oceans.
- ContinentalCrust: The portion of the Earth's crust that makes up the continents.
UpperMantle: The upper portion of the Earth's mantle.
- LowerMantle: The lower portion of the Earth's mantle.
- OuterCore: The liquid outer layer of the Earth's core.
- InnerCore: The solid inner layer of the Earth's core.

## Relationships
- isPartOf: Relates a subclass to its superclass.
- isLocatedIn: Relates a subclass to its location within the Earth.

# Biosphere
## Classes
- Biosphere: All living things on Earth and their interactions with the other spheres.
- Organism: Any living entity, including plants, animals, and microorganisms.
- Ecosystem: A community of living and non-living components interacting in a particular area.
- Habitat: The natural environment where an organism lives.
- Biome: A large, naturally occurring community of flora and fauna occupying a major habitat.
- FoodChain: The sequence of organisms in an ecosystem that eat and are eaten by each other.
Biodiversity: The variety of life forms in an ecosystem.
- Extinction: The permanent disappearance of a species from the Earth.

## Properties
- hasOrganism: Relates the biosphere to organisms.
- hasEcosystem: Relates the biosphere to ecosystems.
- hasHabitat: Relates an organism to its habitat.
- hasBiome: Relates an ecosystem to its biome.
- hasFoodChain: Relates an ecosystem to its food chain.
- hasBiodiversity: Relates an ecosystem to its biodiversity.
- hasExtinction: Relates the biosphere to extinction events.

## Subclasses
- Plant: A photosynthetic organism that synthesizes its own food.
- Animal: A heterotrophic organism that feeds on other organisms.
- Microorganism: An organism that is too small to be seen with the naked eye.
- Predator: An animal that hunts and kills other animals for food.
- Prey: An animal that is hunted and killed by other animals for food.
- Herbivore: An animal that feeds primarily on plants.
- Carnivore: An animal that feeds primarily on other animals.
- Omnivore: An animal that feeds on both plants and animals.
- EndangeredSpecies: A species that is at risk of becoming extinct.
- KeystoneSpecies: A species that plays a critical role in the functioning of an ecosystem.
- InvasiveSpecies: A species that is not native to an ecosystem and can cause harm to the ecosystem.

## Relations
- isPartOf: Relates a subclass to its superclass.
- isLocatedIn: Relates a subclass to its location within the Earth.


# Hydrosphere

## Classes
- Hydrosphere: The part of the Earth's surface where water exists.
- Ocean: The largest body of saltwater on Earth.
- Sea: A large body of saltwater that is partially enclosed by land.
- Lake: A body of fresh or salt water that is surrounded by land.
- River: A natural flowing watercourse that empties into an ocean, sea, lake, or another river.
- Stream: A small, narrow river.
- Glacier: A large body of ice that moves slowly downhill.
- Water: A chemical compound made up of hydrogen and oxygen atoms.
- Salinity: The amount of salt dissolved in a body of water.

## Properties
- hasOcean: Relates the hydrosphere to oceans.
- hasSea: Relates the hydrosphere to seas.
- hasLake: Relates the hydrosphere to lakes.
- hasRiver: Relates the hydrosphere to rivers.
- hasStream: Relates the hydrosphere to streams.
- hasGlacier: Relates the hydrosphere to glaciers.
- hasWater: Relates the hydrosphere to water.
- hasSalinity: Relates a body of water to its salinity.

## Subclasses
- Saltwater: Water that contains a significant amount of dissolved salts.
- Freshwater: Water that has a low concentration of dissolved salts.
- Wetland: An area of land that is saturated with water.
- Estuary: A partially enclosed body of water where freshwater from rivers mixes with saltwater from the ocean.
- CoralReef: A diverse underwater ecosystem formed by colonies of coral polyps.
- Tides: The regular rise and fall of sea levels caused by the gravitational pull of the Moon and the Sun.

## Relationships
- isPartOf: Relates a subclass to its superclass.
- isLocatedIn: Relates a subclass to its location within the Earth.

# Geospace

## Classes
- Geospace: The overarching class representing the space above the Earth's surface.
- Satellite: An object in orbit around the Earth that is used for communication, navigation, or scientific research.
- Asteroid: A small rocky object that orbits the Sun and can potentially collide with the Earth.
- Meteoroid: A small rocky or metallic object that travels through space.
- Comet: A small celestial body that orbits the Sun and releases gas or dust as it approaches the Sun.
- Solar radiation: The electromagnetic radiation emitted by the Sun, including visible light, ultraviolet radiation, and X-rays.

## Properties

- hasSatellite: Relates the geospace to artificial satellites.
- hasAsteroid: Relates the geospace to asteroids.
- hasMeteoroid: Relates the geospace to meteoroids.
- hasComet: Relates the geospace to comets.
hasSolarRadiation: Relates the geospace to solar radiation.


## Subclasses
- Orbit: The path that an object takes as it revolves around another object, such as the Earth or the Sun.
- Solar System: The collection of planets, asteroids, comets, and other celestial bodies that orbit the Sun.
- Near-Earth Object (NEO): An asteroid or comet with an orbit that brings it close to the Earth's orbit.


## Relationships

- isPartOf: Relates a subclass to its superclass, for example, a satellite is part of the geospace.
- isLocatedIn: Relates a subclass to its location within the geospace, for example, an asteroid may be located in the asteroid belt between Mars and Jupiter.

# Universe
## Classes
- Universe: The overarching class representing the entirety of space and all matter and energy within it.
- Galaxy: A gravitationally bound system of stars, gas, dust, and dark matter.
- Star: A luminous ball of plasma held together by its own gravity.
- Planet: A celestial body that orbits a star, has sufficient mass for its gravity to compress it into a spherical shape, and has cleared its orbit of other debris.
- Moon: A natural satellite that orbits a planet.
- Comet: A small celestial body that orbits the Sun and releases gas or dust as it approaches the Sun.
- Asteroid: A small rocky or metallic object that travels through space.
- Black hole: A region of spacetime where gravity is so strong that nothing, not even light, can escape.
- Dark matter: Matter that does not emit, absorb, or reflect light, but can be inferred from its gravitational effects.
- Dark energy: A form of energy that permeates all of space and is thought to be responsible for the accelerating expansion of the Universe.

## Properties

- hasGalaxy: Relates the Universe to galaxies.
- hasStar: Relates the Universe to stars.
- hasPlanet: Relates the Universe to planets.
- hasMoon: Relates the Universe to moons.
- hasComet: Relates the Universe to comets.
- hasAsteroid: Relates the Universe to asteroids.
- hasBlackHole: Relates the Universe to black holes.
- hasDarkMatter: Relates the Universe to dark matter.
- hasDarkEnergy: Relates the Universe to dark energy.


## Subclasses
- Solar System: The collection of planets, asteroids, comets, and other celestial bodies that orbit a star.
- Exoplanet: A planet that orbits a star outside the Solar System.
- Supernova: An astronomical event that occurs during the last stages of a star's life when it undergoes a catastrophic explosion.
- Quasar: An extremely luminous active galactic nucleus powered by accretion of material onto a supermassive black hole at the center of a galaxy.
- Nebula: A cloud of gas and dust in outer space, visible either as an indistinct bright patch or as a dark silhouette against other luminous matter.

## Relationships
- Relates a subclass to its superclass, for example, a planet is part of a solar system, which is part of the Universe.
- isLocatedIn: Relates a subclass to its location within the Universe, for example, a galaxy may be located in a particular region or cluster of galaxies.