```mermaid
graph TD
    %% =================================================================
    %% Masterplan: Lifecycle of a Hierarchical Conscious AI Agent
    %% Design: Based on user concepts of awareness, exploration, and planning.
    %% Version: 2.0 (Parser-Safe)
    %% =================================================================

    %% -----------------------------------------------------------------
    %% Phase 0: System Initialization & Neural Architecture
    %% -----------------------------------------------------------------
    subgraph Phase0_System_Initialization
        style Phase0_System_Initialization fill:#ddd,stroke:#333,stroke-width:2px

        INIT_START("
        <div style='font-weight:bold; font-size:16px; margin-bottom:5px;'>1. System Power-On</div>
        <div style='text-align:left; font-size:12px;'>
        - All neural networks initialized with random weights.<br/>
        - Experience Replay Buffers are empty.<br/>
        - Zero prior knowledge of self or environment (Tabula Rasa).
        </div>
        ")

        INIT_MODELS("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>2. Define Neural Components</div>
        <div style='text-align:left; font-size:12px;'>
        <b>a. The Self-Model (World / Dynamics Model):</b><br/>
        &nbsp;&nbsp;&nbsp;&nbsp;- Network predicts the next state (s_next) from current state (s) and action (a).<br/>
        <b>b. The Environment-Model (Perception Model):</b><br/>
        &nbsp;&nbsp;&nbsp;&nbsp;- Network predicts sensor inputs (ray-casts) from a given position and orientation.<br/>
        <b>c. The Hierarchical Policy:</b><br/>
        &nbsp;&nbsp;&nbsp;&nbsp;<b>- The Manager (High-Level Policy):</b> Selects abstract sub-goals.<br/>
        &nbsp;&nbsp;&nbsp;&nbsp;<b>- The Experts (Low-Level Policies):</b> Specialized networks for each sub-goal.
        </div>
        ")

        INIT_MEMORY("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>3. Define Experience Replay Buffers</div>
        <div style='text-align:left; font-size:12px;'>
        - <b>Physics Buffer:</b> Stores (state, action, reward, next_state) transitions.<br/>
        - <b>Mapping Buffer:</b> Stores (location, sensor_readings) data.<br/>
        - <b>Task Buffer:</b> Stores (state, goal, action, reward, next_state) trajectories.
        </div>
        ")
        INIT_START --> INIT_MODELS --> INIT_MEMORY
    end

    %% -----------------------------------------------------------------
    %% Phase 1: Self-Discovery (Learning Physics via Intrinsic Motivation)
    %% -----------------------------------------------------------------
    subgraph Phase1_Self_Discovery
        style Phase1_Self_Discovery fill:#f9f,stroke:#333,stroke-width:2px

        SELF_START("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>4. Start Self-Discovery Phase</div>
        <div style='text-align:left; font-size:12px;'>
        - Environment: Empty, infinite plane.<br/>
        - Drive: Intrinsic Motivation only (Curiosity). No external goal.
        </div>
        ")
        
        SELF_LOOP_START("
        <div style='font-weight:bold; font-size:12px;'>5. Self-Exploration Loop</div>
        ")

        SELF_ACTION(Issue a random or curiosity-driven action)
        SELF_EXECUTE(Execute action in the physics engine)
        SELF_OBSERVE(Observe the resulting state, s_next, and reward, r)
        SELF_STORE(Store the transition in the Physics Buffer)
        SELF_TRAIN_PREPARE(Sample a mini-batch from the Physics Buffer)
        SELF_TRAIN_MODEL("
        <div style='font-weight:bold; font-size:12px;'>Train the Self-Model</div>
        <div style='text-align:left; font-size:11px;'>
        - Predict s_predicted using the model.<br/>
        - Calculate prediction error against s_actual.<br/>
        - Update network weights via backpropagation.
        </div>
        ")
        
        SELF_CURIOSITY("
        <div style='font-weight:bold; font-size:12px;'>6. Calculate Curiosity Reward</div>
        <div style='text-align:left; font-size:11px;'>
        - Intrinsic Reward = Prediction Error.<br/>
        - The more surprising the outcome, the higher the reward.<br/>
        - This reward guides exploration towards poorly understood actions.
        </div>
        ")

        SELF_CHECK_CONVERGENCE{"
        <div style='font-weight:bold; font-size:12px;'>7. Is the Self-Model Accurate?</div>
        <div style='text-align:left; font-size:11px;'>
        (Is the average prediction error low?)
        </div>
        "}

        SELF_MODEL_COMPLETE(("
        <div style='font-weight:bold; font-size:14px;'>8. Self-Model Converged</div>
        <div style='text-align:left; font-size:12px;'>
        The AI now has an intuitive understanding of its own physics. It knows it is a car.
        </div>
        "))

        SELF_LOOP_START --> SELF_ACTION --> SELF_EXECUTE --> SELF_OBSERVE --> SELF_STORE --> SELF_TRAIN_PREPARE --> SELF_TRAIN_MODEL --> SELF_CURIOSITY --> SELF_CHECK_CONVERGENCE
        SELF_CHECK_CONVERGENCE -- "No, continue exploring" --> SELF_LOOP_START
        SELF_CHECK_CONVERGENCE -- "Yes, model is stable" --> SELF_MODEL_COMPLETE
    end

    %% -----------------------------------------------------------------
    %% Phase 2: Environment Discovery (Building a Mental Map)
    %% -----------------------------------------------------------------
    subgraph Phase2_Environment_Mapping
        style Phase2_Environment_Mapping fill:#9cf,stroke:#333,stroke-width:2px

        MAP_START("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>9. Start Environment Exploration</div>
        <div style='text-align:left; font-size:12px;'>
        - Environment: The actual race track.<br/>
        - Activate 'Sensor Rays' (the bat-like sense).
        </div>
        ")
        
        MAP_LOOP_START("
        <div style='font-weight:bold; font-size:12px;'>10. Map-Building Loop</div>
        ")
        
        MAP_MOVE(Move through the track using the now-learned Self-Model)
        MAP_SENSE(Fire sensor rays in all directions)
        MAP_COLLECT(Collect data: [current_location, sensor_readings])
        MAP_STORE(Store data in the Mapping Buffer)
        MAP_TRAIN_PREPARE(Sample a mini-batch from the Mapping Buffer)
        MAP_TRAIN_MODEL("
        <div style='font-weight:bold; font-size:12px;'>Train the Environment-Model</div>
        <div style='text-align:left; font-size:11px;'>
        - The model learns to associate a location on the track with the shape of the boundaries around it.
        </div>
        ")

        MAP_CHECK_COVERAGE{"
        <div style='font-weight:bold; font-size:12px;'>11. Sufficient Coverage?</div>
        "}
        
        MAP_MODEL_COMPLETE(("
        <div style='font-weight:bold; font-size:14px;'>12. Environment-Model Converged</div>
        <div style='text-align:left; font-size:12px;'>
        The AI now has a 'mental map' of the track.
        </div>
        "))

        MAP_LOOP_START --> MAP_MOVE --> MAP_SENSE --> MAP_COLLECT --> MAP_STORE --> MAP_TRAIN_PREPARE --> MAP_TRAIN_MODEL --> MAP_CHECK_COVERAGE
        MAP_CHECK_COVERAGE -- "No, explore more" --> MAP_LOOP_START
        MAP_CHECK_COVERAGE -- "Yes, map is detailed" --> MAP_MODEL_COMPLETE
    end

    %% -----------------------------------------------------------------
    %% Phase 3: The Conscious Action Loop (Perceive-Plan-Act-Learn Cycle)
    %% -----------------------------------------------------------------
    subgraph Phase3_Conscious_Action_Loop
        style Phase3_Conscious_Action_Loop fill:#9f9,stroke:#333,stroke-width:2px

        MAIN_LOOP("
        <div style='font-weight:bold; font-size:16px;'>13. Start Conscious Racing Loop</div>
        ")

        PERCEIVE("
        <div style='font-weight:bold; font-size:14px;'>A. Perception</div>
        <div style='text-align:left; font-size:12px;'>
        - Receive current state (s) from the game engine.<br/>
        - Use Environment-Model to understand context ('I am approaching a sharp left turn').
        </div>
        ")
        
        PLAN_MANAGER("
        <div style='font-weight:bold; font-size:14px;'>B. High-Level Planning (Manager)</div>
        <div style='text-align:left; font-size:12px;'>
        - Manager analyzes context and selects a high-level sub-goal.<br/>
        - Example: 'Goal: Execute a perfect drift through the next corner'.<br/>
        - Passes control to the appropriate Expert (e.g., the 'Drift Expert').
        </div>
        ")

        PLAN_EXPERT("
        <div style='font-weight:bold; font-size:14px;'>C. Low-Level Planning (Expert)</div>
        <div style='text-align:left; font-size:12px;'>
        - The selected Expert performs 'Mental Simulation' (Imagination).<br/>
        - It uses the Self-Model to rapidly 'imagine' hundreds of action sequences.<br/>
        - It selects the best sequence of actions to achieve the Manager's sub-goal.
        </div>
        ")

        ACT("
        <div style='font-weight:bold; font-size:14px;'>D. Action</div>
        <div style='text-align:left; font-size:12px;'>
        - Execute ONLY the first action from the imagined best-plan in the real game.
        </div>
        ")

        LEARN_FEEDBACK("
        <div style='font-weight:bold; font-size:14px;'>E. Learning & Feedback</div>
        <div style='text-align:left; font-size:12px;'>
        - Observe the real outcome (s_next) and reward (r).<br/>
        - Store the full experience in the Task Buffer.<br/>
        - <b>Self-Model Update:</b> Compare real s_next with imagined s_next to refine its physics understanding.<br/>
        - <b>Expert Update:</b> Use reward r to improve its ability to achieve its sub-goal.<br/>
        - <b>Manager Update:</b> Use reward r to evaluate if choosing that sub-goal was a good decision.
        </div>
        ")
        
        MAIN_LOOP --> PERCEIVE --> PLAN_MANAGER --> PLAN_EXPERT --> ACT --> LEARN_FEEDBACK --> MAIN_LOOP
    end

    %% -----------------------------------------------------------------
    %% Linking the High-Level Phases Together
    %% -----------------------------------------------------------------
    INIT_MEMORY --> SELF_START
    SELF_MODEL_COMPLETE --> MAP_START
    MAP_MODEL_COMPLETE --> MAIN_LOOP
```
