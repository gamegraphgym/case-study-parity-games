# Case study on benchmarking parity game solvers

### Dependancies

```bash
# Boost library for efficient data structure
sudo apt-get install -y build-essential cmake libboost-all-dev

# Python library to plot line charts
sudo apt-get install python3-matplotlib

# Python library to plot bar charts
sudo apt-get install python3-pandas
```

### Repository Setup
```bash
# Framework clone
git clone https://github.com/gamegraphgym/ggg.git

# Framework build
cd ggg
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DTOOLS_ALL=ON
cmake --build build -j$(nproc)

# Case study clone
cd extra
git clone https://github.com/gamegraphgym/case-study-parity-games.git
```

### Benchmarking 1
```bash
# Benchmarking on random games and 60 seconds timeout
bash ggg/extra/scripts/benchmark.sh case-study-parity-games/games/random ggg/build/bin --time 60 -o random_results.json --solvers ggg_parity_solver_recursive,ggg_parity_solver_priority_promotion

# Plotting line chart of results
python3 ggg/extra/scripts/plot_time_by_vertex_count.py random_results.json
```

### Benchmarking 2
```bash
# Benchmarking on concrete games and 60 seconds timeout
bash ggg/extra/scripts/benchmark.sh case-study-parity-games/games/syntDOT ggg/build/bin --time 60 -o type_results.json --solvers ggg_parity_solver_recursive,ggg_parity_solver_priority_promotion

# Plotting bar chart of results
python3 ggg/extra/scripts/plot_performance_by_game_type.py type_results.json
```
