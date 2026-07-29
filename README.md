<!DOCTYPE html>
<html lang="en" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Surrey Hills Marathon Tracker</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        document.addEventListener('alpine:init', () => {
            Alpine.data('trackerApp', () => ({
                activePhase: 'All',
                phases: [
                    { name: 'Base Building' },
                    { name: 'Strength & Endurance' },
                    { name: 'Peak Block' },
                    { name: 'Taper & Race' }
                ],
                weeks: [
                    { id: 1, phase: 'Base Building', dates: 'Sep 1 - Sep 7', focus: 'Establishing 4-day routine', longRunTarget: '7 miles', monDesc: '~45m steady (~5mi)', thuDesc: '6 miles steady' },
                    { id: 2, phase: 'Base Building', dates: 'Sep 8 - Sep 14', focus: 'Consistency & rhythm', longRunTarget: '7.5 miles', monDesc: '~45m steady (~5mi)', thuDesc: '6 miles steady' },
                    { id: 3, phase: 'Base Building', dates: 'Sep 15 - Sep 21', focus: 'Aerobic adaptation', longRunTarget: '8 miles', monDesc: '~45m steady (~5.5mi)', thuDesc: '7 miles terrain' },
                    { id: 4, phase: 'Base Building', dates: 'Sep 22 - Sep 28', focus: 'End of month 1 base', longRunTarget: '8.5 miles', monDesc: '~45m steady (~5.5mi)', thuDesc: '7 miles terrain' },
                    { id: 5, phase: 'Base Building', dates: 'Sep 29 - Oct 5', focus: 'Transition into October', longRunTarget: '9 miles', monDesc: '~45m steady (~6mi)', thuDesc: '7 miles terrain' },
                    { id: 6, phase: 'Base Building', dates: 'Oct 6 - Oct 12', focus: 'Consolidating base', longRunTarget: '9.5 miles', monDesc: '~45m steady (~6mi)', thuDesc: '7.5 miles terrain' },
                    { id: 7, phase: 'Base Building', dates: 'Oct 13 - Oct 19', focus: 'Building endurance', longRunTarget: '10 miles', monDesc: '~45m steady (~6mi)', thuDesc: '8 miles terrain' },
                    { id: 8, phase: 'Base Building', dates: 'Oct 20 - Oct 26', focus: 'Base completion', longRunTarget: '10 miles', monDesc: '~45m steady (~6mi)', thuDesc: '8 miles terrain' },
                    { id: 9, phase: 'Strength & Endurance', dates: 'Oct 27 - Nov 2', focus: 'Introducing rolling hills', longRunTarget: '11 miles', monDesc: '~45m steady (~6mi)', thuDesc: '8 miles rolling' },
                    { id: 10, phase: 'Strength & Endurance', dates: 'Nov 3 - Nov 9', focus: 'Hill repeats focus', longRunTarget: '11.5 miles', monDesc: '~45m steady (~6.5mi)', thuDesc: '8.5 miles rolling' },
                    { id: 11, phase: 'Strength & Endurance', dates: 'Nov 10 - Nov 16', focus: 'Strength building', longRunTarget: '12 miles', monDesc: '~45m steady (~6.5mi)', thuDesc: '8.5 miles rolling' },
                    { id: 12, phase: 'Strength & Endurance', dates: 'Nov 17 - Nov 23', focus: 'Consolidating hills', longRunTarget: '12.5 miles', monDesc: '~45m steady (~6.5mi)', thuDesc: '9 miles rolling' },
                    { id: 13, phase: 'Strength & Endurance', dates: 'Nov 24 - Nov 30', focus: 'End of November block', longRunTarget: '13 miles', monDesc: '~45m steady (~7mi)', thuDesc: '9 miles rolling' },
                    { id: 14, phase: 'Strength & Endurance', dates: 'Dec 1 - Dec 7', focus: 'December volume maintenance', longRunTarget: '13 miles', monDesc: '~45m steady (~7mi)', thuDesc: '9 miles rolling' },
                    { id: 15, phase: 'Strength & Endurance', dates: 'Dec 8 - Dec 14', focus: 'Navigating holiday schedule', longRunTarget: '13.5 miles', monDesc: '~45m steady (~7mi)', thuDesc: '9 miles rolling' },
                    { id: 16, phase: 'Strength & Endurance', dates: 'Dec 15 - Dec 21', focus: 'Pre-holiday long run', longRunTarget: '14 miles', monDesc: '~45m steady (~7mi)', thuDesc: '9 miles rolling' },
                    { id: 17, phase: 'Strength & Endurance', dates: 'Dec 22 - Dec 28', focus: 'Holiday flexibility week', longRunTarget: '12 miles (Recovery)', monDesc: '~45m steady (~6mi)', thuDesc: '8 miles steady' },
                    { id: 18, phase: 'Strength & Endurance', dates: 'Dec 29 - Jan 4', focus: 'New Year reset', longRunTarget: '14 miles', monDesc: '~45m steady (~7mi)', thuDesc: '9 miles rolling' },
                    { id: 19, phase: 'Strength & Endurance', dates: 'Jan 5 - Jan 11', focus: 'Deep winter endurance', longRunTarget: '15 miles', monDesc: '~45m steady (~7.5mi)', thuDesc: '9.5 miles rolling' },
                    { id: 20, phase: 'Strength & Endurance', dates: 'Jan 12 - Jan 18', focus: 'Building stamina', longRunTarget: '16 miles', monDesc: '~45m steady (~7.5mi)', thuDesc: '10 miles rolling' },
                    { id: 21, phase: 'Strength & Endurance', dates: 'Jan 19 - Jan 25', focus: 'January peak prep', longRunTarget: '17 miles', monDesc: '~45m steady (~8mi)', thuDesc: '10 miles rolling' },
                    { id: 22, phase: 'Peak Block', dates: 'Jan 26 - Feb 1', focus: 'Entering peak block', longRunTarget: '18 miles', monDesc: '~45m steady (~8mi)', thuDesc: '10 miles rolling' },
                    { id: 23, phase: 'Peak Block', dates: 'Feb 2 - Feb 8', focus: 'First 20-miler push', longRunTarget: '20 miles', monDesc: '~45m steady (~8mi)', thuDesc: '10 miles rolling' },
                    { id: 24, phase: 'Peak Block', dates: 'Feb 9 - Feb 15', focus: 'Absorption & recovery', longRunTarget: '16 miles (Step-back)', monDesc: '~45m steady (~7mi)', thuDesc: '8 miles steady' },
                    { id: 25, phase: 'Peak Block', dates: 'Feb 16 - Feb 22', focus: 'Second 20-miler peak', longRunTarget: '20-22 miles', monDesc: '~45m steady (~8mi)', thuDesc: '10 miles rolling' },
                    { id: 26, phase: 'Peak Block', dates: 'Feb 23 - Mar 1', focus: 'Final peak effort', longRunTarget: '18 miles', monDesc: '~45m steady (~7.5mi)', thuDesc: '9 miles rolling' },
                    { id: 27, phase: 'Taper & Race', dates: 'Mar 2 - Mar 8', focus: 'Taper Week 1', longRunTarget: '14 miles', monDesc: '~45m steady (~6mi)', thuDesc: '7 miles steady' },
                    { id: 28, phase: 'Taper & Race', dates: 'Mar 9 - Mar 15', focus: 'Taper Week 2', longRunTarget: '10 miles', monDesc: '~30m steady (~4mi)', thuDesc: '5 miles steady' },
                    { id: 29, phase: 'Taper & Race', dates: 'Mar 16 - Mar 20', focus: 'Race Week! (Mar 20)', longRunTarget: 'Surrey Hills Marathon!', monDesc: 'Short shakeout (3mi)', thuDesc: 'Rest / Carb Load' }
                ],
                state: {},
                init() {
                    let saved = localStorage.getItem('surrey_hills_tracker');
                    if (saved) {
                        try {
                            this.state = JSON.parse(saved);
                        } catch (e) {
                            this.initDefaultState();
                        }
                    } else {
                        this.initDefaultState();
                    }
                },
                initDefaultState() {
                    this.weeks.forEach(w => {
                        this.state[w.id] = { mon: false, tue: false, thu: false, sat: false };
                    });
                    this.saveState();
                },
                saveState() {
                    localStorage.setItem('surrey_hills_tracker', JSON.stringify(this.state));
                },
                get filteredWeeks() {
                    if (this.activePhase === 'All') return this.weeks;
                    return this.weeks.filter(w => w.phase === this.activePhase);
                },
                totalRuns() {
                    return this.weeks.length * 4;
                },
                completedCount() {
                    let count = 0;
                    Object.values(this.state).forEach(week => {
                        if (week.mon) count++;
                        if (week.tue) count++;
                        if (week.thu) count++;
                        if (week.sat) count++;
                    });
                    return count;
                },
                progressPercentage() {
                    let total = this.totalRuns();
                    if (total === 0) return 0;
                    return Math.round((this.completedCount() / total) * 100);
                }
            }));
        });
    </script>
    <script src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
</head>
<body class="bg-slate-900 text-slate-100 h-full font-sans antialiased" x-data="trackerApp()">

    <div class="min-h-full flex flex-col">
        <!-- Header -->
        <header class="bg-slate-800 border-b border-slate-700 py-6 px-4 sm:px-8 shadow-md">
            <div class="max-w-6xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-4">
                <div>
                    <h1 class="text-2xl sm:text-3xl font-bold tracking-tight text-emerald-400">Surrey Hills Marathon Tracker</h1>
                    <p class="text-sm text-slate-400 mt-1">Target Date: March 20, 2027 | 4 Runs/Week • Waitrose HQ Hills • No Wednesday Chaos</p>
                </div>
                <div class="bg-slate-700/50 px-4 py-2 rounded-xl border border-slate-600 flex items-center gap-4">
                    <div>
                        <span class="block text-xs uppercase tracking-wider text-slate-400">Overall Progress</span>
                        <span class="text-xl font-bold text-emerald-400" x-text="completedCount() + ' / ' + totalRuns()"></span>
                        <span class="text-xs text-slate-400">runs completed</span>
                    </div>
                    <div class="w-16 bg-slate-700 rounded-full h-3 overflow-hidden">
                        <div class="bg-emerald-500 h-full transition-all duration-500" :style="'width: ' + progressPercentage() + '%'"></div>
                    </div>
                </div>
            </div>
        </header>

        <!-- Main Content -->
        <main class="flex-1 max-w-6xl w-full mx-auto px-4 sm:px-8 py-8 space-y-8">
            
            <!-- Phase Filters / Navigation -->
            <div class="flex flex-wrap gap-2">
                <template x-for="phase in phases" :key="phase.name">
                    <button @click="activePhase = phase.name"
                        :class="activePhase === phase.name ? 'bg-emerald-600 text-white border-emerald-500' : 'bg-slate-800 text-slate-300 border-slate-700 hover:bg-slate-700'"
                        class="px-4 py-2 rounded-lg text-sm font-medium border transition shadow-sm"
                        x-text="phase.name">
                    </button>
                </template>
                <button @click="activePhase = 'All'"
                    :class="activePhase === 'All' ? 'bg-emerald-600 text-white border-emerald-500' : 'bg-slate-800 text-slate-300 border-slate-700 hover:bg-slate-700'"
                    class="px-4 py-2 rounded-lg text-sm font-medium border transition shadow-sm">
                    View All Weeks
                </button>
            </div>

            <!-- Weeks List -->
            <div class="space-y-4">
                <template x-for="week in filteredWeeks" :key="week.id">
                    <div class="bg-slate-800 border border-slate-700 rounded-2xl p-5 shadow-lg transition hover:border-slate-600">
                        <div class="flex flex-col md:flex-row md:items-center justify-between gap-2 pb-4 border-b border-slate-700/60">
                            <div>
                                <div class="flex items-center gap-3">
                                    <span class="text-xs font-semibold uppercase tracking-wider px-2.5 py-1 rounded-md"
                                        :class="{
                                            'bg-blue-900/50 text-blue-300 border border-blue-700/50': week.phase === 'Base Building',
                                            'bg-amber-900/50 text-amber-300 border border-amber-700/50': week.phase === 'Strength & Endurance',
                                            'bg-purple-900/50 text-purple-300 border border-purple-700/50': week.phase === 'Peak Block',
                                            'bg-emerald-900/50 text-emerald-300 border border-emerald-700/50': week.phase === 'Taper & Race'
                                        }"
                                        x-text="week.phase"></span>
                                    <h3 class="text-lg font-bold text-slate-100" x-text="'Week ' + week.id + ' (' + week.dates + ')'"></h3>
                                </div>
                                <p class="text-xs text-slate-400 mt-1" x-text="'Focus: ' + week.focus"></p>
                            </div>
                            <div class="text-sm font-medium text-slate-300 bg-slate-900/40 px-3 py-1.5 rounded-lg border border-slate-700/50 self-start md:self-auto">
                                Max Long Run: <span class="text-emerald-400 font-bold" x-text="week.longRunTarget"></span>
                            </div>
                        </div>

                        <!-- Runs Grid -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3 mt-4">
                            <!-- Monday -->
                            <label class="flex items-start gap-3 p-3 rounded-xl bg-slate-900/50 border border-slate-700/40 cursor-pointer hover:bg-slate-700/30 transition">
                                <input type="checkbox" class="mt-1 h-4 w-4 rounded border-slate-700 text-emerald-500 focus:ring-emerald-500 bg-slate-900"
                                    x-model="state[week.id].mon" @change="saveState()">
                                <div class="text-sm">
                                    <span class="block font-semibold text-slate-200">Mon: Steady Run</span>
                                    <span class="text-xs text-slate-400" x-text="week.monDesc"></span>
                                </div>
                            </label>

                            <!-- Tuesday -->
                            <label class="flex items-start gap-3 p-3 rounded-xl bg-slate-900/50 border border-slate-700/40 cursor-pointer hover:bg-slate-700/30 transition">
                                <input type="checkbox" class="mt-1 h-4 w-4 rounded border-slate-700 text-emerald-500 focus:ring-emerald-500 bg-slate-900"
                                    x-model="state[week.id].tue" @change="saveState()">
                                <div class="text-sm">
                                    <span class="block font-semibold text-slate-200">Tue: Hill Sprints</span>
                                    <span class="text-xs text-slate-400">Waitrose HQ (~3-4mi)</span>
                                </div>
                            </label>

                            <!-- Thursday -->
                            <label class="flex items-start gap-3 p-3 rounded-xl bg-slate-900/50 border border-slate-700/40 cursor-pointer hover:bg-slate-700/30 transition">
                                <input type="checkbox" class="mt-1 h-4 w-4 rounded border-slate-700 text-emerald-500 focus:ring-emerald-500 bg-slate-900"
                                    x-model="state[week.id].thu" @change="saveState()">
                                <div class="text-sm">
                                    <span class="block font-semibold text-slate-200">Thu: Terrain Run</span>
                                    <span class="text-xs text-slate-400" x-text="week.thuDesc"></span>
                                </div>
                            </label>

                            <!-- Weekend -->
                            <label class="flex items-start gap-3 p-3 rounded-xl bg-slate-900/50 border border-slate-700/40 cursor-pointer hover:bg-slate-700/30 transition">
                                <input type="checkbox" class="mt-1 h-4 w-4 rounded border-slate-700 text-emerald-500 focus:ring-emerald-500 bg-slate-900"
                                    x-model="state[week.id].sat" @change="saveState()">
                                <div class="text-sm">
                                    <span class="block font-semibold text-slate-200">Sat/Sun: Long Run</span>
                                    <span class="text-xs text-slate-400" x-text="week.longRunTarget + ' Time on feet'"></span>
                                </div>
                            </label>
                        </div>
                    </div>
                </template>
            </div>
        </main>
    </div>

</body>
</html>
