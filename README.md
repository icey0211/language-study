# language-study
四大方言对比数据集
Chinese Dialect Contrast Dataset (CDCD)
收集北京话、东北话、山东话、粤语四类方言的日常对话音频，并与标准普通话进行转写对照，用于语言学分析及多方言语音识别模型训练。

Purpose（项目目的）
文化保护：系统记录正在消失的方言特征，为中华语言多样性留存珍贵档案
学术研究：提供结构化数据支撑方言演变、社会语言学及对比语言学研究
技术赋能：构建高质量训练集，推动方言语音识别、合成等AI技术的发展
教育传承：通过可视化对比帮助新一代理解方言与普通话的差异与联系


目录
数据概览
标注示例
文件结构
方言特征对比表

数据概览
方言类型	时长	说话人数	场景分类	特殊标注项
北京话	15min	3人	北京相声	儿化音（"事儿"→"shèr"）
东北话	15min	-人	------	动词替换（"整"="做"）
山东话	15min	-人	------	声调变异（"喝"→"hēi"）
粤语	15min	-人	家庭对话	特有词汇（"咩"="什么"）

标注格式规范（中英对照+词性）
1. CSV格式示例
方言类型	原始文本	字粒度分解	英文注释 (per char)	词性标注 (POS)	普通话对照
粤语	"你食咗饭未？"	你|食|咗|饭|未|？	you|eat|(perfective)|rice|yet|?	Pron|V|AUX|N|ADV|PUNCT	"你吃饭了吗？"
北京话	"今儿个真高兴"	今|儿|个|真|高|兴	today|(erhua)|measure|really|high|happy	N|PART|MEAS|ADV|ADJ|ADJ	"今天真的很开心"

标注字段说明
字段名	要求
字粒度分解	用|分隔每个字/词（分词边界需明确）
英文注释	逐字翻译，方言虚词用()说明功能（如"咗"→"(perfective)"）
词性标注	采用Universal POS Tags标准：
- NOUN（名词）
- VERB（动词）
- PART（虚词/语气词）
- DIALECT（方言特有词）

/CDCD-Dataset
├── /raw_audio                  # 原始音频
│   ├── /beijing                # 北京话
│   ├── /dongbei                # 东北话  
│   └── ...（其他方言）
/annotations
├── /per_char_annotations
│   ├── beijing_pos.csv       # 北京话字粒度标注
│   ├── shandong_pos.json     # 山东话JSON格式
│   └── ...
├── vocabulary_glossary.md    # 方言特殊词汇对照表（含词性）
└── pos_tag_guidelines.md     # 词性标注规范文档
