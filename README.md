<<<<<<< HEAD
# Meta Pseudo Labels
This is an unofficial PyTorch implementation of [Meta Pseudo Labels](https://arxiv.org/abs/2003.10580).
The official Tensorflow implementation is [here](https://github.com/google-research/google-research/tree/master/meta_pseudo_labels).


## Results

|  | CIFAR-10-4K | SVHN-1K | ImageNet-10% |
|:---:|:---:|:---:|:---:|
| Paper (w/ finetune) | 96.11 ± 0.07 | 98.01 ± 0.07 | 73.89 |
| This code (w/o finetune) | 96.01 | - | - |
| This code (w/ finetune) | 96.08 | - | - |
| Acc. curve | [w/o finetune](https://tensorboard.dev/experiment/ehMVEk39SrGiqM43ye2c7w/)<br>[w/ finetune](https://tensorboard.dev/experiment/vbqR7dt2Q9aw6rf8yVu56g/) | - | - |

* February 2022, Retested.

## Usage

Train the model by 4000 labeled data of CIFAR-10 dataset:

```
python main.py \
    --seed 2 \
    --name cifar10-4K.2 \
    --expand-labels \
    --dataset cifar10 \
    --num-classes 10 \
    --num-labeled 4000 \
    --total-steps 300000 \
    --eval-step 1000 \
    --randaug 2 16 \
    --batch-size 128 \
    --teacher_lr 0.05 \
    --student_lr 0.05 \
    --weight-decay 5e-4 \
    --ema 0.995 \
    --nesterov \
    --mu 7 \
    --label-smoothing 0.15 \
    --temperature 0.7 \
    --threshold 0.6 \
    --lambda-u 8 \
    --warmup-steps 5000 \
    --uda-steps 5000 \
    --student-wait-steps 3000 \
    --teacher-dropout 0.2 \
    --student-dropout 0.2 \
    --finetune-epochs 625 \
    --finetune-batch-size 512 \
    --finetune-lr 3e-5 \
    --finetune-weight-decay 0 \
    --finetune-momentum 0.9 \
    --amp
```

Train the model by 10000 labeled data of CIFAR-100 dataset by using DistributedDataParallel:
```
python -m torch.distributed.launch --nproc_per_node 4 main.py \
    --seed 2 \
    --name cifar100-10K.2 \
    --dataset cifar100 \
    --num-classes 100 \
    --num-labeled 10000 \
    --expand-labels \
    --total-steps 300000 \
    --eval-step 1000 \
    --randaug 2 16 \
    --batch-size 128 \
    --teacher_lr 0.05 \
    --student_lr 0.05 \
    --weight-decay 5e-4 \
    --ema 0.995 \
    --nesterov \
    --mu 7 \
    --label-smoothing 0.15 \
    --temperature 0.7 \
    --threshold 0.6 \
    --lambda-u 8 \
    --warmup-steps 5000 \
    --uda-steps 5000 \
    --student-wait-steps 3000 \
    --teacher-dropout 0.2 \
    --student-dropout 0.2 \
    --finetune-epochs 250 \
    --finetune-batch-size 512 \
    --finetune-lr 3e-5 \
    --finetune-weight-decay 0 \
    --finetune-momentum 0.9 \
    --amp
```

Monitoring training progress

tensorboard
```
tensorboard --logdir results
```
or

Use wandb

## Requirements
- python 3.6+
- torch 1.7+
- torchvision 0.8+
- tensorboard
- wandb
- numpy
- tqdm
=======
# Diabetic Retinopathy Screening



## Getting started

To make it easy for you to get started with GitLab, here's a list of recommended next steps.

Already a pro? Just edit this README.md and make it your own. Want to make it easy? [Use the template at the bottom](#editing-this-readme)!

## Add your files

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/ee/gitlab-basics/add-file.html#add-a-file-using-the-command-line) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://ncai-gitlab.xyz/diabetic-retinopathy-screening/diabetic-retinopathy-screening.git
git branch -M main
git push -uf origin main
```

## Integrate with your tools

- [ ] [Set up project integrations](https://ncai-gitlab.xyz/diabetic-retinopathy-screening/diabetic-retinopathy-screening/-/settings/integrations)

## Collaborate with your team

- [ ] [Invite team members and collaborators](https://docs.gitlab.com/ee/user/project/members/)
- [ ] [Create a new merge request](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html)
- [ ] [Automatically close issues from merge requests](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html#closing-issues-automatically)
- [ ] [Enable merge request approvals](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/)
- [ ] [Automatically merge when pipeline succeeds](https://docs.gitlab.com/ee/user/project/merge_requests/merge_when_pipeline_succeeds.html)

## Test and Deploy

Use the built-in continuous integration in GitLab.

- [ ] [Get started with GitLab CI/CD](https://docs.gitlab.com/ee/ci/quick_start/index.html)
- [ ] [Analyze your code for known vulnerabilities with Static Application Security Testing(SAST)](https://docs.gitlab.com/ee/user/application_security/sast/)
- [ ] [Deploy to Kubernetes, Amazon EC2, or Amazon ECS using Auto Deploy](https://docs.gitlab.com/ee/topics/autodevops/requirements.html)
- [ ] [Use pull-based deployments for improved Kubernetes management](https://docs.gitlab.com/ee/user/clusters/agent/)
- [ ] [Set up protected environments](https://docs.gitlab.com/ee/ci/environments/protected_environments.html)

***

# Editing this README

When you're ready to make this README your own, just edit this file and use the handy template below (or feel free to structure it however you want - this is just a starting point!).  Thank you to [makeareadme.com](https://www.makeareadme.com/) for this template.

## Suggestions for a good README
Every project is different, so consider which of these sections apply to yours. The sections used in the template are suggestions for most open source projects. Also keep in mind that while a README can be too long and detailed, too long is better than too short. If you think your README is too long, consider utilizing another form of documentation rather than cutting out information.

## Name
Choose a self-explaining name for your project.

## Description
Let people know what your project can do specifically. Provide context and add a link to any reference visitors might be unfamiliar with. A list of Features or a Background subsection can also be added here. If there are alternatives to your project, this is a good place to list differentiating factors.

## Badges
On some READMEs, you may see small images that convey metadata, such as whether or not all the tests are passing for the project. You can use Shields to add some to your README. Many services also have instructions for adding a badge.

## Visuals
Depending on what you are making, it can be a good idea to include screenshots or even a video (you'll frequently see GIFs rather than actual videos). Tools like ttygif can help, but check out Asciinema for a more sophisticated method.

## Installation
Within a particular ecosystem, there may be a common way of installing things, such as using Yarn, NuGet, or Homebrew. However, consider the possibility that whoever is reading your README is a novice and would like more guidance. Listing specific steps helps remove ambiguity and gets people to using your project as quickly as possible. If it only runs in a specific context like a particular programming language version or operating system or has dependencies that have to be installed manually, also add a Requirements subsection.

## Usage
Use examples liberally, and show the expected output if you can. It's helpful to have inline the smallest example of usage that you can demonstrate, while providing links to more sophisticated examples if they are too long to reasonably include in the README.

## Support
Tell people where they can go to for help. It can be any combination of an issue tracker, a chat room, an email address, etc.

## Roadmap
If you have ideas for releases in the future, it is a good idea to list them in the README.

## Contributing
State if you are open to contributions and what your requirements are for accepting them.

For people who want to make changes to your project, it's helpful to have some documentation on how to get started. Perhaps there is a script that they should run or some environment variables that they need to set. Make these steps explicit. These instructions could also be useful to your future self.

You can also document commands to lint the code or run tests. These steps help to ensure high code quality and reduce the likelihood that the changes inadvertently break something. Having instructions for running tests is especially helpful if it requires external setup, such as starting a Selenium server for testing in a browser.

## Authors and acknowledgment
Show your appreciation to those who have contributed to the project.

## License
For open source projects, say how it is licensed.

## Project status
If you have run out of energy or time for your project, put a note at the top of the README saying that development has slowed down or stopped completely. Someone may choose to fork your project or volunteer to step in as a maintainer or owner, allowing your project to keep going. You can also make an explicit request for maintainers.
>>>>>>> 21efbbf981a37bba61af466308c4b841ec4fa4e2
