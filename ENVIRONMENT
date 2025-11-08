import React, { useState, useEffect } from "react";
import { ChevronDown, Factory, Car, Zap, Leaf, Droplet, Wind, Sun, ArrowUp, CheckCircle, XCircle, Beaker } from "lucide-react";

export default function App() {
  // State for Industrial Emissions Simulator
  const [selectedSource, setSelectedSource] = useState<string | null>(null);
  const [pH, setPH] = useState<number>(7);

  // State for Material Corrosion Test
  const [selectedMaterial, setSelectedMaterial] = useState<string | null>(null);

  // State for Acid Rain Formation Game
  const [acidRainStep, setAcidRainStep] = useState<number>(0);

  // State for Pollution Source Identification Game
  const [pollutionAnswer, setPollutionAnswer] = useState<string | null>(null);
  const [pollutionFeedback, setPollutionFeedback] = useState<string | null>(null);

  // State for Smog Challenge
  const [sunlight, setSunlight] = useState<number>(50);
  const [pollution, setPollution] = useState<number>(50);
  const [windSpeed, setWindSpeed] = useState<number>(50);

  // State for pH Visualization Tool
  const [pHSlider, setPHSlider] = useState<number>(7);

  // State for Daily Quiz
  const [quizAnswers, setQuizAnswers] = useState<(string | null)[]>([null, null, null, null, null]);
  const [quizSubmitted, setQuizSubmitted] = useState<boolean>(false);

  // State for Eco-Substitutions Game
  const [ecoMatches, setEcoMatches] = useState<{ [key: string]: string }>({});

  const emissions = {
    Factory: { gases: ["SO₂", "NOₓ", "CO₂"], pH: 4.2, reaction: "2SO₂ + O₂ → 2SO₃" },
    Vehicle: { gases: ["NOₓ", "CO", "CO₂"], pH: 5.0, reaction: "2NO + O₂ → 2NO₂" },
    PowerPlant: { gases: ["SO₂", "CO₂", "NOₓ"], pH: 4.5, reaction: "SO₃ + H₂O → H₂SO₄" }
  };

  const materials = {
    Marble: { corrosion: 65, reaction: "CaCO₃ + H₂SO₄ → CaSO₄ + H₂O + CO₂" },
    Metal: { corrosion: 80, reaction: "Fe + H₂SO₄ → FeSO₄ + H₂" },
    Concrete: { corrosion: 45, reaction: "CaO + H₂SO₄ → CaSO₄ + H₂O" },
    Leaf: { corrosion: 90, reaction: "Chlorophyll breakdown" }
  };

  const acidRainSteps = [
    { title: "Industrial Emissions", desc: "Factories release SO₂ and NOₓ" },
    { title: "Atmospheric Reaction", desc: "SO₂ + O₂ → SO₃" },
    { title: "Acid Formation", desc: "SO₃ + H₂O → H₂SO₄" },
    { title: "Acid Rain Falls", desc: "Rain becomes acidic (pH < 5.6)" }
  ];

  const pollutionQuestion = {
    question: "Which source emits the most SO₂?",
    options: ["Factory", "Vehicle", "PowerPlant"],
    correct: "Factory"
  };

  const quizQuestions = [
    { q: "What is the normal pH of rain?", options: ["5.6", "7.0", "4.0", "8.0"], correct: "5.6", explanation: "Normal rain is slightly acidic at pH 5.6" },
    { q: "Which gas causes acid rain?", options: ["SO₂", "O₂", "N₂", "Ar"], correct: "SO₂", explanation: "SO₂ reacts with water to form sulfuric acid" },
    { q: "Smog is worst with:", options: ["High sunlight + pollution", "Rain", "Wind", "Night"], correct: "High sunlight + pollution", explanation: "Sunlight reacts with pollutants to create smog" },
    { q: "Acid rain damages:", options: ["All of these", "Buildings", "Plants", "Water"], correct: "All of these", explanation: "Acid rain harms structures, ecosystems, and water bodies" },
    { q: "Best way to reduce smog:", options: ["Reduce emissions", "Add more cars", "Stop wind", "Remove sun"], correct: "Reduce emissions", explanation: "Lowering pollution levels reduces smog formation" }
  ];

  const ecoOptions = [
    { traditional: "Coal", eco: "Solar" },
    { traditional: "Gasoline Car", eco: "Electric Car" },
    { traditional: "Plastic Bag", eco: "Reusable Bag" },
    { traditional: "Incandescent Bulb", eco: "LED Bulb" }
  ];

  const scrollToContent = () => {
    document.getElementById("content")?.scrollIntoView({ behavior: "smooth" });
  };

  const scrollToTop = () => {
    window.scrollTo({ top: 0, behavior: "smooth" });
  };

  const handleEmissionClick = (source: string) => {
    setSelectedSource(source);
    const key = source.replace(" ", "") as keyof typeof emissions;
    setPH(emissions[key].pH);
  };

  const handleMaterialClick = (material: string) => {
    setSelectedMaterial(material);
  };

  const handlePollutionAnswer = (answer: string) => {
    setPollutionAnswer(answer);
    setPollutionFeedback(answer === pollutionQuestion.correct ? "correct" : "incorrect");
  };

  const calculateAirQuality = () => {
    const smogLevel = (sunlight * pollution) / (windSpeed + 1);
    if (smogLevel > 60) return { status: "Smog", color: "bg-red-200 dark:bg-red-900" };
    if (smogLevel > 30) return { status: "Haze", color: "bg-orange-200 dark:bg-orange-900" };
    return { status: "Clear", color: "bg-green-200 dark:bg-green-900" };
  };

  const getPHColor = (value: number) => {
    if (value < 4) return "bg-red-400";
    if (value < 7) return "bg-orange-300";
    if (value === 7) return "bg-green-300";
    if (value < 11) return "bg-blue-300";
    return "bg-purple-400";
  };

  const getPHLabel = (value: number) => {
    if (value < 7) return "Acidic";
    if (value === 7) return "Neutral";
    return "Alkaline";
  };

  const handleQuizAnswer = (index: number, answer: string) => {
    const newAnswers = [...quizAnswers];
    newAnswers[index] = answer;
    setQuizAnswers(newAnswers);
  };

  const handleEcoMatch = (traditional: string, eco: string) => {
    const newMatches = { ...ecoMatches };
    newMatches[traditional] = eco;
    setEcoMatches(newMatches);
  };

  const getDailyExperiment = () => {
    const day = new Date().getDate();
    const experiments = [
      "Test vinegar pH with red cabbage indicator",
      "Create a mini greenhouse to see CO₂ effects",
      "Compare water evaporation in sun vs shade",
      "Mix baking soda and vinegar to simulate gas release",
      "Test soil pH in your garden"
    ];
    return experiments[day % experiments.length];
  };

  const getDailyFact = () => {
    const day = new Date().getDate();
    const facts = [
      "Acid rain can have a pH as low as 2.5",
      "Cars emit about 4.6 metric tons of CO₂ per year",
      "Smog can reduce visibility to less than 1 mile",
      "Trees absorb about 48 pounds of CO₂ per year",
      "Electric cars produce 50% less emissions than gasoline cars"
    ];
    return facts[day % facts.length];
  };

  const airQuality = calculateAirQuality();

  return (
    <div className="min-h-screen bg-gradient-to-b from-blue-50 to-green-50 dark:from-gray-900 dark:to-gray-800">
      {/* Landing Section */}
      <div className="flex flex-col items-center justify-center min-h-screen px-4">
        <div className="text-center space-y-6">
          <h1 className="text-5xl md:text-6xl font-bold text-blue-600 dark:text-blue-400">
            EnviroChem Interactive Simulator
          </h1>
          <p className="text-xl md:text-2xl text-muted-foreground max-w-2xl">
            Learn about acid rain, pollution, and smog through fun, hands-on simulations
          </p>
          <button
            onClick={scrollToContent}
            className="mt-8 px-8 py-4 bg-blue-500 hover:bg-blue-600 text-white rounded-full flex items-center gap-2 mx-auto transition-colors"
          >
            Start Learning <ChevronDown className="w-5 h-5 animate-bounce" />
          </button>
        </div>
      </div>

      {/* Main Content */}
      <div id="content" className="container mx-auto px-4 py-16 space-y-16 max-w-6xl">
        
        {/* Industrial Emissions Simulator */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6 flex items-center gap-2">
            <Factory className="w-8 h-8 text-blue-500" />
            Industrial Emissions Simulator
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
            <button
              onClick={() => handleEmissionClick("Factory")}
              className={`p-6 rounded-xl border-2 transition-all ${
                selectedSource === "Factory"
                  ? "border-blue-500 bg-blue-50 dark:bg-blue-950"
                  : "border-border hover:border-blue-300"
              }`}
            >
              <Factory className="w-12 h-12 mx-auto mb-2 text-blue-600" />
              <p className="font-semibold">Factory</p>
            </button>
            <button
              onClick={() => handleEmissionClick("Vehicle")}
              className={`p-6 rounded-xl border-2 transition-all ${
                selectedSource === "Vehicle"
                  ? "border-blue-500 bg-blue-50 dark:bg-blue-950"
                  : "border-border hover:border-blue-300"
              }`}
            >
              <Car className="w-12 h-12 mx-auto mb-2 text-blue-600" />
              <p className="font-semibold">Vehicle</p>
            </button>
            <button
              onClick={() => handleEmissionClick("PowerPlant")}
              className={`p-6 rounded-xl border-2 transition-all ${
                selectedSource === "PowerPlant"
                  ? "border-blue-500 bg-blue-50 dark:bg-blue-950"
                  : "border-border hover:border-blue-300"
              }`}
            >
              <Zap className="w-12 h-12 mx-auto mb-2 text-blue-600" />
              <p className="font-semibold">Power Plant</p>
            </button>
          </div>
          {selectedSource && (
            <div className="bg-blue-50 dark:bg-blue-950 p-6 rounded-xl space-y-4 animate-in fade-in">
              <div>
                <p className="font-semibold mb-2">Emitted Gases:</p>
                <div className="flex gap-2 flex-wrap">
                  {emissions[selectedSource.replace(" ", "") as keyof typeof emissions].gases.map((gas) => (
                    <span key={gas} className="px-4 py-2 bg-orange-200 dark:bg-orange-900 rounded-full text-sm font-mono">
                      {gas}
                    </span>
                  ))}
                </div>
              </div>
              <div>
                <p className="font-semibold mb-2">Chemical Reaction:</p>
                <p className="font-mono text-sm bg-white dark:bg-gray-800 p-3 rounded-lg">
                  {emissions[selectedSource.replace(" ", "") as keyof typeof emissions].reaction}
                </p>
              </div>
              <div>
                <p className="font-semibold mb-2">Resulting pH Level:</p>
                <div className="flex items-center gap-4">
                  <div className="flex-1 h-8 bg-gradient-to-r from-red-400 via-yellow-300 via-green-300 to-blue-400 rounded-full"></div>
                  <span className="text-2xl font-bold">{pH}</span>
                </div>
              </div>
            </div>
          )}
        </section>

        {/* Material Corrosion Test */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6 flex items-center gap-2">
            <Beaker className="w-8 h-8 text-green-500" />
            Material Corrosion Test
          </h2>
          <div className="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
            {Object.keys(materials).map((material) => (
              <button
                key={material}
                onClick={() => handleMaterialClick(material)}
                className={`p-6 rounded-xl border-2 transition-all ${
                  selectedMaterial === material
                    ? "border-green-500 bg-green-50 dark:bg-green-950"
                    : "border-border hover:border-green-300"
                }`}
              >
                <p className="font-semibold">{material}</p>
              </button>
            ))}
          </div>
          {selectedMaterial && (
            <div className="bg-green-50 dark:bg-green-950 p-6 rounded-xl space-y-4 animate-in fade-in">
              <div>
                <p className="font-semibold mb-2">Corrosion Level:</p>
                <div className="flex items-center gap-4">
                  <div className="flex-1 bg-gray-200 dark:bg-gray-700 rounded-full h-6 overflow-hidden">
                    <div
                      className="bg-red-500 h-full transition-all duration-1000"
                      style={{ width: `${materials[selectedMaterial as keyof typeof materials].corrosion}%` }}
                    ></div>
                  </div>
                  <span className="text-xl font-bold">
                    {materials[selectedMaterial as keyof typeof materials].corrosion}%
                  </span>
                </div>
              </div>
              <div>
                <p className="font-semibold mb-2">Chemical Reaction:</p>
                <p className="font-mono text-sm bg-white dark:bg-gray-800 p-3 rounded-lg">
                  {materials[selectedMaterial as keyof typeof materials].reaction}
                </p>
              </div>
            </div>
          )}
        </section>

        {/* Acid Rain Formation Game */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6 flex items-center gap-2">
            <Droplet className="w-8 h-8 text-blue-500" />
            Acid Rain Formation Game
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-4 gap-4">
            {acidRainSteps.map((step, index) => (
              <button
                key={index}
                onClick={() => setAcidRainStep(index)}
                className={`p-6 rounded-xl border-2 transition-all ${
                  acidRainStep === index
                    ? "border-blue-500 bg-blue-50 dark:bg-blue-950"
                    : "border-border hover:border-blue-300"
                }`}
              >
                <div className="w-12 h-12 rounded-full bg-blue-500 text-white flex items-center justify-center mx-auto mb-3 text-xl font-bold">
                  {index + 1}
                </div>
                <p className="font-semibold text-sm mb-2">{step.title}</p>
                {acidRainStep === index && (
                  <p className="text-xs text-muted-foreground">{step.desc}</p>
                )}
              </button>
            ))}
          </div>
        </section>

        {/* Pollution Source Identification Game */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6">Pollution Source Identification</h2>
          <p className="text-lg mb-6">{pollutionQuestion.question}</p>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
            {pollutionQuestion.options.map((option) => (
              <button
                key={option}
                onClick={() => handlePollutionAnswer(option)}
                disabled={pollutionAnswer !== null}
                className={`p-6 rounded-xl border-2 transition-all ${
                  pollutionAnswer === option && pollutionFeedback === "correct"
                    ? "border-green-500 bg-green-50 dark:bg-green-950"
                    : pollutionAnswer === option && pollutionFeedback === "incorrect"
                    ? "border-red-500 bg-red-50 dark:bg-red-950"
                    : "border-border hover:border-blue-300"
                }`}
              >
                <p className="font-semibold">{option}</p>
                {pollutionAnswer === option && (
                  <div className="mt-2">
                    {pollutionFeedback === "correct" ? (
                      <CheckCircle className="w-8 h-8 text-green-500 mx-auto" />
                    ) : (
                      <XCircle className="w-8 h-8 text-red-500 mx-auto" />
                    )}
                  </div>
                )}
              </button>
            ))}
          </div>
          {pollutionFeedback === "correct" && (
            <div className="mt-6 bg-green-50 dark:bg-green-950 p-4 rounded-xl">
              <p className="text-sm">✓ Factories emit large amounts of SO₂ from burning coal and fossil fuels!</p>
            </div>
          )}
        </section>

        {/* Smog Challenge */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6 flex items-center gap-2">
            <Sun className="w-8 h-8 text-yellow-500" />
            Smog Challenge
          </h2>
          <div className="space-y-6">
            <div>
              <label className="flex items-center gap-2 mb-2 font-semibold">
                <Sun className="w-5 h-5" /> Sunlight: {sunlight}%
              </label>
              <input
                type="range"
                min="0"
                max="100"
                value={sunlight}
                onChange={(e) => setSunlight(Number(e.target.value))}
                className="w-full"
              />
            </div>
            <div>
              <label className="flex items-center gap-2 mb-2 font-semibold">
                <Factory className="w-5 h-5" /> Pollution: {pollution}%
              </label>
              <input
                type="range"
                min="0"
                max="100"
                value={pollution}
                onChange={(e) => setPollution(Number(e.target.value))}
                className="w-full"
              />
            </div>
            <div>
              <label className="flex items-center gap-2 mb-2 font-semibold">
                <Wind className="w-5 h-5" /> Wind Speed: {windSpeed}%
              </label>
              <input
                type="range"
                min="0"
                max="100"
                value={windSpeed}
                onChange={(e) => setWindSpeed(Number(e.target.value))}
                className="w-full"
              />
            </div>
            <div className={`p-6 rounded-xl ${airQuality.color} transition-all`}>
              <p className="text-2xl font-bold text-center">Air Quality: {airQuality.status}</p>
            </div>
          </div>
        </section>

        {/* pH Visualization Tool */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6">pH Visualization Tool</h2>
          <div className="space-y-6">
            <div>
              <label className="mb-2 font-semibold block">pH Level: {pHSlider}</label>
              <input
                type="range"
                min="0"
                max="14"
                value={pHSlider}
                onChange={(e) => setPHSlider(Number(e.target.value))}
                className="w-full"
              />
            </div>
            <div className="flex items-center gap-4">
              <div className="flex-1 h-16 bg-gradient-to-r from-red-500 via-yellow-300 via-green-400 via-blue-400 to-purple-500 rounded-xl"></div>
            </div>
            <div className={`p-6 rounded-xl ${getPHColor(pHSlider)} transition-all`}>
              <p className="text-2xl font-bold text-center text-gray-800">
                {getPHLabel(pHSlider)} (pH {pHSlider})
              </p>
            </div>
          </div>
        </section>

        {/* Daily Experiment & Fun Fact */}
        <section className="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div className="bg-purple-50 dark:bg-purple-950 p-8 rounded-2xl shadow-lg">
            <h3 className="text-2xl font-bold text-foreground mb-4">Today's Experiment</h3>
            <p className="text-lg">{getDailyExperiment()}</p>
          </div>
          <div className="bg-teal-50 dark:bg-teal-950 p-8 rounded-2xl shadow-lg">
            <h3 className="text-2xl font-bold text-foreground mb-4">Fun Fact</h3>
            <p className="text-lg">{getDailyFact()}</p>
          </div>
        </section>

        {/* Daily Quiz */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6">Daily Quiz</h2>
          <div className="space-y-6">
            {quizQuestions.map((q, index) => (
              <div key={index} className="p-6 bg-gray-50 dark:bg-gray-900 rounded-xl">
                <p className="font-semibold mb-4">
                  {index + 1}. {q.q}
                </p>
                <div className="grid grid-cols-2 gap-3">
                  {q.options.map((option) => (
                    <button
                      key={option}
                      onClick={() => handleQuizAnswer(index, option)}
                      disabled={quizSubmitted}
                      className={`p-3 rounded-lg border-2 transition-all ${
                        quizSubmitted && option === q.correct
                          ? "border-green-500 bg-green-50 dark:bg-green-950"
                          : quizSubmitted && quizAnswers[index] === option && option !== q.correct
                          ? "border-red-500 bg-red-50 dark:bg-red-950"
                          : quizAnswers[index] === option
                          ? "border-blue-500 bg-blue-50 dark:bg-blue-950"
                          : "border-border hover:border-blue-300"
                      }`}
                    >
                      <div className="flex items-center justify-between">
                        <span>{option}</span>
                        {quizSubmitted && option === q.correct && (
                          <CheckCircle className="w-5 h-5 text-green-500" />
                        )}
                        {quizSubmitted && quizAnswers[index] === option && option !== q.correct && (
                          <XCircle className="w-5 h-5 text-red-500" />
                        )}
                      </div>
                    </button>
                  ))}
                </div>
                {quizSubmitted && (
                  <p className="mt-3 text-sm text-muted-foreground">{q.explanation}</p>
                )}
              </div>
            ))}
            <button
              onClick={() => setQuizSubmitted(!quizSubmitted)}
              className="w-full py-4 bg-blue-500 hover:bg-blue-600 text-white rounded-xl font-semibold transition-colors"
            >
              {quizSubmitted ? "Reset Quiz" : "Submit Answers"}
            </button>
          </div>
        </section>

        {/* Smart Eco-Substitutions */}
        <section className="bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg">
          <h2 className="text-3xl font-bold text-foreground mb-6">Smart Eco-Substitutions</h2>
          <p className="text-muted-foreground mb-6">Match traditional choices with eco-friendly alternatives:</p>
          <div className="space-y-4">
            {ecoOptions.map((pair) => (
              <div key={pair.traditional} className="grid grid-cols-1 md:grid-cols-3 gap-4 items-center">
                <div className="p-4 bg-red-50 dark:bg-red-950 rounded-xl text-center font-semibold">
                  {pair.traditional}
                </div>
                <div className="text-center text-2xl">→</div>
                <select
                  value={ecoMatches[pair.traditional] || ""}
                  onChange={(e) => handleEcoMatch(pair.traditional, e.target.value)}
                  className="p-4 rounded-xl border-2 border-border bg-background"
                >
                  <option value="">Select eco alternative...</option>
                  {ecoOptions.map((opt) => (
                    <option key={opt.eco} value={opt.eco}>
                      {opt.eco}
                    </option>
                  ))}
                </select>
                {ecoMatches[pair.traditional] === pair.eco && (
                  <div className="md:col-start-3 flex justify-center">
                    <CheckCircle className="w-6 h-6 text-green-500" />
                  </div>
                )}
              </div>
            ))}
          </div>
        </section>
      </div>

      {/* Footer */}
      <footer className="bg-gray-800 dark:bg-gray-950 text-white py-8">
        <div className="container mx-auto px-4 flex flex-col md:flex-row justify-between items-center gap-4">
          <p>© {new Date().getFullYear()} EnviroChem Interactive Simulator. All rights reserved.</p>
          <button
            onClick={scrollToTop}
            className="flex items-center gap-2 px-6 py-3 bg-blue-500 hover:bg-blue-600 rounded-full transition-colors"
          >
            <ArrowUp className="w-5 h-5" />
            Back to Top
          </button>
        </div>
      </footer>
    </div>
  );
}

