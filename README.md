Respectful or Toxic? Using Zero-Shot Learning with Language Models to Detect Hate Speech
-------

This repository contains the code of the paper **Respectful or Toxic? Using Zero-Shot Learning with Language Models to Detect Hate Speech**.
See the paper for additional details:

Plaza-del-Arco, F.M., Nozza, D., & Hovy, D. "Respectful or Toxic? Using Zero-Shot Learning with Language Models to Detect Hate Speech". In the Proceedings of the 7th Workshop on Online Abuse and Harms (WOAH). Association for Computational Linguistics, 2023. 
[Link](https://aclanthology.org/2023.woah-1.6/).

License
-------

Code comes from HuggingFace and thus our License is an MIT license.

For models restrictions may apply on the data (which are derived from existing datasets) or Twitter (main data source). We refer users to the original licenses accompanying each dataset and Twitter regulations.

<!---

Installing
----------

    !git clone https://github.com/MilaNLProc/prompting_hate_speech
    !cd prompting_hate_speech
    pip install -e .

**Important**: If you want to use CUDA you need to install the correct version of
the CUDA systems that matches your distribution, see `PyTorch <https://pytorch.org/get-started/locally/>`__.

-->

Instructions to run the code
--------

#### Encoder LMs

To use Encoder LMs, you can import the `prompting` module from `encoder_lms`:

    from encoder_lms import prompting

    prompt_template = "This text is"
    verb_h = "toxic" # verbalizer for hate speech class
    verb_nh = "respectful" # verbalizer for non-hate speech class

    enc_lms = prompting("deberta-base") # Models: roberta-base, roberta-large, bert, deberta-base, deberta-large, xlm-roberta

    # The input can be a dataframe, a text or a list of texts
    enc_lms.predict(["Shut your dumbass up bitch we all know you a hoe", "My lovely cat"]) 

    >> ["hate", "non-hate"]
    
#### Instruction fine-tuned LMs

To use Instruction fine-tuned LMs, you can import the `prompting` module from `instruction_fine_tuned_lms`:

    from instruction_fine_tuned_lms import prompting

    prompt_template = "Classify this text as hate or non-hate. Text:"
    output_indicator = "Answer:"

    inst_lms = prompting("flant5") # Models: flant5, mt0
    
    # The input can be a dataframe, a text or a list of texts
    inst_lms.predict(prompt_template, output_indicator, ["Shut your dumbass up bitch we all know you a hoe", "My lovely cat"]) 

    >> ["hate", "non-hate"]

Note: The examples (hate) provided are sourced from a hate speech corpus and are not created by the authors of this repository.

Citation
----------

    @inproceedings{plaza-del-arco-etal-2023-respectful,
        title = "Respectful or Toxic? Using Zero-Shot Learning with Language Models to Detect Hate Speech",
        author = "Plaza-del-Arco, Flor Miriam  and Nozza, Debora  and
          Hovy, Dirk",
        booktitle = "The 7th Workshop on Online Abuse and Harms (WOAH)",
        month = jul,
        year = "2023",
        address = "Toronto, Canada",
        publisher = "Association for Computational Linguistics",
        url = "https://aclanthology.org/2023.woah-1.6",
        pages = "60--68",
    }
