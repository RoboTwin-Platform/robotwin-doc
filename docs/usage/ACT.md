# ACT (Action Chunking Transformer)

## Install
```
pip install pyquaternion pyyaml rospkg pexpect mujoco==2.3.7 dm_control==1.0.14 opencv-python matplotlib einops packaging h5py ipython

cd adetr && pip install -e .
```

## Prepare Training Data

This step performs data preprocessing, converting the original **RoboTwin 2.0** data into the format required for ACT training.
The `expert_data_num` parameter specifies the number of trajectory pairs to be used as training data.

```
bash process_data.sh ${task_name} ${task_config} ${expert_data_num}
```

## Train Policy

This step launches the training process.
By default, the model is trained for **6,000 steps**.

```
bash train.sh ${task_name} ${task_config} ${expert_data_num} ${seed} ${gpu_id}
```

## Eval Policy

The `task_config` field refers to the **evaluation environment configuration**, while the `ckpt_setting` field refers to the **training data configuration** used during policy learning.

```
bash eval.sh ${task_name} ${task_config} ${ckpt_setting} ${expert_data_num} ${seed} ${gpu_id}
```

The evaluation results, including videos, will be saved in the `eval_result` directory under the project root.
