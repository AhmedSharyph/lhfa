// newCHR_Milestones.js
/**
 * newCHR_Milestones Library
 * Version: 1.0.0
 * Author: Your Name
 * Description: Dynamically render child milestone forms by age/month
 * License: MIT
 */

const newCHR_Milestones = (function () {

  // --- Milestones Data ---
  const milestonesData = [
    {month: 2, category: "Social/Emotional Milestones", label: "Calms down when spoken to or picked up", name: "calms_down_when_spoken_or_picked_up"},
    {month: 2, category: "Social/Emotional Milestones", label: "Looks at your face", name: "looks_at_your_face"},
    {month: 2, category: "Language/Communication Milestones", label: "Makes sounds other than crying", name: "makes_sounds_other_than_crying"},
    {month: 2, category: "Language/Communication Milestones", label: "Reacts to loud sounds", name: "reacts_to_loud_sounds"},
    {month: 2, category: "Cognitive Milestones", label: "Watches you as you move", name: "watches_you_as_you_move"},
    {month: 2, category: "Cognitive Milestones", label: "Looks at a toy for several seconds", name: "looks_at_toy_for_several_seconds"},
    {month: 2, category: "Movement/Physical Development", label: "Holds head up when on tummy", name: "holds_head_up_on_tummy"},
    {month: 2, category: "Movement/Physical Development", label: "Moves both arms and both legs", name: "moves_both_arms_and_legs"},
    {month: 2, category: "Movement/Physical Development", label: "Opens hands briefly", name: "opens_hands_briefly"},
    // Add more months later
  ];

  // --- Category Colors (Tailwind CSS classes) ---
  const categoryColors = {
    "Social/Emotional Milestones": "bg-blue-100 border-blue-400",
    "Language/Communication Milestones": "bg-green-100 border-green-400",
    "Cognitive Milestones": "bg-yellow-100 border-yellow-400",
    "Movement/Physical Development": "bg-pink-100 border-pink-400"
  };

  // --- Get milestones by month ---
  function getByMonth(month) {
    return milestonesData.filter(m => m.month === month);
  }

  // --- Create Yes/No select element ---
  function createSelect(name) {
    const select = document.createElement('select');
    select.name = name;
    select.id = name;
    select.required = true;
    select.className = "border border-gray-300 rounded px-2 py-1 w-full";

    const defaultOption = document.createElement('option');
    defaultOption.value = "";
    defaultOption.text = "Select";
    select.appendChild(defaultOption);

    ["Yes", "No"].forEach(opt => {
      const option = document.createElement('option');
      option.value = opt;
      option.text = opt;
      select.appendChild(option);
    });

    return select;
  }

  // --- Render form ---
  function renderForm(month, containerId) {
    const container = document.getElementById(containerId);
    if (!container) return;
    container.innerHTML = "";

    const milestones = getByMonth(month);
    if (milestones.length === 0) {
      container.innerHTML = `<p class="text-gray-500">No milestones available for ${month} month(s)</p>`;
      return;
    }

    // Group by category
    const categories = [...new Set(milestones.map(m => m.category))];

    categories.forEach(cat => {
      const catDiv = document.createElement('div');
      catDiv.className = "mb-6 p-3 rounded shadow";

      const catTitle = document.createElement('h3');
      catTitle.className = "font-semibold text-lg mb-3";
      catTitle.innerText = cat;
      catDiv.appendChild(catTitle);

      const catMilestones = milestones.filter(m => m.category === cat);
      catMilestones.forEach((milestone, index) => {
        const wrapper = document.createElement('div');
        const colorClass = categoryColors[cat] || "bg-gray-100 border-gray-300";
        wrapper.className = `mb-2 p-2 rounded border ${colorClass} ${index % 2 === 0 ? "opacity-90" : "opacity-70"}`;

        const label = document.createElement('label');
        label.className = "block mb-1 font-medium";
        label.innerText = milestone.label;
        label.htmlFor = milestone.name;
        wrapper.appendChild(label);

        const select = createSelect(milestone.name);
        wrapper.appendChild(select);

        catDiv.appendChild(wrapper);
      });

      container.appendChild(catDiv);
    });
  }

  return {
    renderForm
  };

})();
