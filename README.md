# 生物学 · 立项说明与总纲

立项日期：2026-10-20。本类是「领域学习谱系」五类中的第四类，按《分类总纲》的推进顺序开工：量化交易、健康与长寿、医药与药物研发之后接生物学，化学排最后。本类的定位特殊——它不是离应用最近的一类，而是另外两类的地基：医药与药物研发、健康与长寿往下追两层，全是本类的概念。本文件定本类的总纲：收什么、不收什么、与上下游怎么衔接、经典材料有哪些。

## 一、本类总纲

### 收录范围（照《分类总纲》定版）

收四类东西：

1. **生物信息学与计算生物学的开源工具链**：序列处理与格式、序列比对、基因组变异检出、转录组与单细胞分析、工作流引擎与平台、软件分发——即「测序数据从机器里出来之后，怎么一步步变成生物学结论」的全套计算基础设施。这是本类的主体，按分析链条分层收。
2. **基因组学与蛋白质组学的公开数据与资源体系**：公共序列档案、参考基因组与注释、蛋白质结构数据库等一手数据来源（INSDC、Ensembl、UniProt、PDB、AlphaFold DB 等），讲清每个库的定位与口径。
3. **经典教材与里程碑论文**：分子生物学与细胞生物学的通行教材、开放教材，以及测序、比对、基因组计划、功能基因组、基因编辑、结构预测这条线上的源头论文——只列名目与出处、做摘要级导读，不搬在版原文。
4. **系统生物学经典与合成生物学入门**：通路与网络层面的经典材料、基因线路与标准生物元件的入门读物——排在工具链之后，作为从「单个基因」走向「系统」的桥。

### 不收什么（红线，长期有效）

- 不收**临床诊疗指南**与任何具体疾病的诊断、治疗、用药内容——那是医疗执业范围，与医药类的排除口径一致，本谱系五类均不涉及。本类讲研究方法与工具：一个变异是怎么被检出的，与「这个变异对某个病人意味着什么、该怎么治」是两回事，后者永远不在本类出现。
- 不收需要湿实验资质才能操作的**危险病原相关内容**：病原基因组细节、增强传播或毒力的方法学、生物武器相关的一切，一律不进谱系。本类以公开数据与计算分析为限。
- 不收纯商业闭源产品仓（商业测序云平台、专有 LIMS 等）；商业机构发布但代码真开源的（如第一批的 AlphaFold、GATK）按开源仓正常收，口径与量化类收 QuantDinger 一致。

### 按分析链条分层收录（批次的组织方式）

1. **基础库层**：在编程语言里处理生物数据的底层库（Biopython 为第一号样本；R 侧的 Bioconductor 以生态形式另行收录，理由见第一批取舍留痕）。
2. **格式与底层工具层**：SAM/BAM/CRAM、VCF 等公共数据格式的定义者与处理工具（samtools 三件套）。
3. **比对层**：短读长、长读长、剪接感知三类比对器（minimap2、STAR 为第一批代表；bwa、bowtie2 等经典留专题批次）。
4. **变异与基因组分析层**：变异检出与基因组分析管线（GATK 为代表）。
5. **转录组与单细胞层**：定量工具与单细胞分析框架（Seurat、scanpy 为第一批代表；salmon、kallisto 等定量工具留第二批）。
6. **流程与平台层**：工作流引擎与零代码平台（Nextflow、Snakemake、Galaxy）。
7. **分发层**：把上述工具送到每台机器的基础设施（Bioconda）。
8. **结构与 AI 层**：蛋白质结构预测与结构数据库（AlphaFold 及其数据库）。
9. **数据与教材层（贯穿）**：公共数据体系与经典材料，见本文件第三部分。

### 与既有线的关系（本类是地基，写细一点）

**对医药与药物研发类（下游）**：药物靶点本质上是基因与蛋白质。靶点发现的证据链——遗传学关联、差异表达、通路富集——每一条都建立在本类的基因组学与单细胞工具之上；变异检出（本类第一批的 GATK）是药物基因组学的地基；AlphaFold DB 的预测结构是医药类「结构药理与分子对接」的前置输入。本类建成后，医药类学习路线的阶段 0 里「靶点、通路」这些词，可以直接回链本类的对应阶段，不必在医药类里另起炉灶讲生物学。

**对健康与长寿类（下游）**：衰老标志（hallmarks of aging）里的每一项——基因组不稳定、端粒磨损、表观遗传改变、细胞衰老、干细胞耗竭——都是分子与细胞层面的机制陈述，读不懂本类的中心法则与基因表达调控，那些标志就只能背名词。长寿前沿里最热的单细胞衰老图谱、多组学时钟，用的正是本类第一批的 Seurat 与 scanpy。长寿类引用的每个干预证据，往下追两层都是本类的概念。

**对化学类（下一类，同为地基）**：生物大分子的行为归根到底是化学——肽键、氢键、疏水效应、酶促反应的热力学。化学类建成后与本类在「分子」这一层会合：化学讲分子本身，本类讲分子在细胞里的组织与信息流，两边共同支撑医药类的分子层面讲解。

**概念先行的具体所指**：三组概念必须在本类先立住，下游才讲得通——（1）序列：DNA/RNA/蛋白质是一维字符串，测序是把它们读出来，参考基因组是坐标系；（2）结构：序列折叠成三维结构，结构决定功能，AlphaFold 改写了获取结构的成本；（3）通路：基因与蛋白质不是单打独斗，而是成网络地调控与传导信号，药物打的、衰老坏的，都是网络上的节点。这三组概念就是本类学习路线图的前三个阶段。

### 学习路线（草案，随批次细化为正式路线图）

- 阶段 0 概念地基：中心法则、基因与表达、测序是怎么回事。读 OpenStax *Biology 2e* 相关章节，*Molecular Biology of the Cell* 选读。过关标准：能用自己的话讲清「一条 read 是什么、参考基因组是什么、变异是什么」。
- 阶段 1 序列与格式：FASTA/FASTQ/SAM/VCF 四种格式，用 Biopython 与 samtools 把真实数据摸一遍；配读 BLAST 两篇论文与 Durbin 教材选章，理解比对与打分的来历。
- 阶段 2 基因组主线：minimap2 比对 → samtools 处理 → GATK 检出变异，跑通一条最小的基因组分析链，知道每一环的输入输出与坑。
- 阶段 3 转录组与单细胞：STAR 的剪接比对为什么不同于 DNA 比对；Seurat 或 scanpy 二选一，走完一遍单细胞全流程（质控、降维、聚类、标志基因）。
- 阶段 4 流程与复现：把阶段 2、3 的链条改写成 Nextflow 或 Snakemake 流程，软件全部走 Bioconda 安装；Galaxy 作为零代码对照线，先点通再下到命令行也是一条合法坡道。
- 阶段 5 结构与系统：用 AlphaFold 预测一个蛋白的结构，去 AlphaFold DB 与 PDB 里查已知的结构；再补通路与网络的概念（系统生物学经典选读），为医药类的靶点章节与长寿类的机制章节合流做准备。

## 二、第一批的选品口径（摘要，完整留痕在《第一批-导读》卷末）

先以主题词（bioinformatics、genomics、computational biology、single-cell 等）与领域知识圈定 25 个候选仓，逐个用 GitHub API 实查硬数据，再按分析链条取样选出 12 个——结构、基础库、格式、比对、变异、单细胞、流程、分发、平台各层都有代表，宁可牺牲几个 star 更高但链条位置重复的仓。这个领域的 star 整体不高（第一名 AlphaFold 不到 1.5 万），且与真实采用量严重脱钩（samtools 不到两千 star，却是全行业的水电）——选品时把 star 只当参考，链条位置与不可替代性优先。

## 三、经典学习材料清单（只列名目与出处，本批不展开导读；名目与出处已于 2026-10-20 逐个核对出版社、期刊与官方页面）

### 教材

- Alberts, Heald, Johnson, Morgan, Raff, Roberts & Walter, *Molecular Biology of the Cell*（W. W. Norton，第 7 版，2022；初版 1983）——细胞与分子生物学的通行权威教材，全球生物课堂的默认参考。本类阶段 0 的主教材，只列名目，在版书籍不做全文处理。
- Durbin, Eddy, Krogh & Mitchison, *Biological Sequence Analysis: Probabilistic Models of Proteins and Nucleic Acids*（Cambridge University Press, 1998）——序列分析的概率模型源头教材：隐马尔可夫模型、成对比对、系统发育在一本书里讲透。理解 BLAST 之后「比对为什么成立」，读它。
- OpenStax, *Biology 2e*（Rice University, 2018；Clark, Douglas & Choi）——免费开放教材，覆盖两学期大学生物学的完整范围；按 OpenStax 官网该书页面口径，Biology 2e 以 CC BY-NC-SA 4.0 发布，可免费在线读与下载 PDF。零预算起步的正统选择，本类阶段 0 的先行读物。

### 公开数据与资源体系（官方，一手来源）

- **INSDC 三库**（GenBank / ENA / DDBJ）：国际核苷酸序列数据库协作体，全球测序数据的公共底账，三家每日同步；配套的 SRA 是原始测序读数据的档案库，GEO 是基因表达数据的档案库——都是 NCBI 与 EMBL-EBI 等机构运营的公共基础设施。
- **Ensembl 与 UCSC Genome Browser**：参考基因组与基因注释的两个主要入口；查一个基因在哪、长什么样、有何转录本，先来这两处。
- **UniProt**：蛋白质序列与功能注释的权威库（论文见 UniProt Consortium 在 *Nucleic Acids Research* 的定期更新版），是 AlphaFold DB 的序列来源之一。
- **RCSB PDB**：实验测定蛋白质结构的档案库，七十年代至今的结构生物学公共账本；**AlphaFold DB**（DeepMind 与 EMBL-EBI）是它的预测版扩展——方法与数据库论文见下。

### 里程碑论文（按时间排，每篇一句定位）

- **测序法**：Sanger, Nicklen & Coulson, "DNA sequencing with chain-terminating inhibitors", *PNAS* 74(12): 5463-5467, 1977——双脱氧链终止法（Sanger 测序）的原始论文，作者因此获 1980 年诺贝尔化学奖；此后三十年测序都站在它上面。
- **BLAST 原始论文**：Altschul, Gish, Miller, Myers & Lipman, "Basic local alignment search tool", *Journal of Molecular Biology* 215(3): 403-410, 1990——序列相似性搜索的起点，科学史上被引次数最高的论文之一（与 1997 年续篇合计被引超过十万次，NCBI 引用指南口径）。
- **BLAST 续篇**：Altschul et al., "Gapped BLAST and PSI-BLAST: a new generation of protein database search programs", *Nucleic Acids Research* 25(17): 3389-3402, 1997——引入缺口比对与位置特异迭代搜索，今天 NCBI BLAST 的形态由它定型。
- **人类基因组草图**：International Human Genome Sequencing Consortium, "Initial sequencing and analysis of the human genome", *Nature* 409: 860-921, 2001；与 Venter et al., "The sequence of the human genome", *Science* 291: 1304-1351, 2001 同周背靠背发表——公共计划与 Celera 公司的竞赛以这种方式同时抵达终点，是理解基因组时代开局的标准读物。
- **人类基因组完成图**：International Human Genome Sequencing Consortium, "Finishing the euchromatic sequence of the human genome", *Nature* 431: 931-945, 2004——常染色质部分完成，错误率低于十万分之一，当年口径下蛋白编码基因数估计约 20,000–25,000 个。
- **ENCODE**：ENCODE Project Consortium, "An integrated encyclopedia of DNA elements in the human genome", *Nature* 489: 57-74, 2012；扩展版见 "Expanded encyclopaedias of DNA elements in the human and mouse genomes", *Nature*, 2020（DOI: 10.1038/s41586-020-2493-4）——给基因组的非编码部分系统性地做功能注释。如实标注：2012 年论文「为 80% 的基因组赋予生化功能」的表述在学界引发了持续至今的争议（「功能」的定义之争），读时必须带这个语境，这也是本谱系收它时最想让学习者看到的东西——大科学的结论同样要过批判性阅读这一关。
- **CRISPR**：Jinek et al., "A programmable dual-RNA-guided DNA endonuclease in adaptive bacterial immunity", *Science* 337: 816-821, 2012——证明 Cas9 可由 RNA 编程切割任意 DNA 序列，基因编辑时代的起点；Charpentier 与 Doudna 因此获 2020 年诺贝尔化学奖。本类收它作为遗传学方法的里程碑，只讲原理与研究方法，不涉及任何临床应用编辑。
- **AlphaFold 2**：Jumper et al., "Highly accurate protein structure prediction with a deep learning system", *Nature* 596: 583-589, 2021——蛋白质结构预测问题被深度学习实质性地解决；其开源代码仓是本类第一批导读的第 1 条。配套数据库论文：Varadi et al., "AlphaFold Protein Structure Database: massively expanding the structural coverage of protein-sequence space with high-accuracy models", *Nucleic Acids Research* 50(D1): D439-D444, 2022（该库已收录两亿个以上的预测结构，比 PDB 的实验结构多三个数量级——数据库论文口径）。Jumper 与 Hassabis 因结构预测获 2024 年诺贝尔化学奖。
- **完整人类基因组（T2T）**：Nurk et al.（Telomere-to-Telomere Consortium）, "The complete sequence of a human genome", *Science* 376: 44-53, 2022——靠长读长测序与新组装方法补齐 2001/2004 两版留下的全部缺口，端粒到端粒无缺口的单倍体基因组；本类第一批的 minimap2 正是这一代组装工作的主力比对工具。
- **Bioconductor 纲领**：Huber et al., "Orchestrating high-throughput genomic analysis with Bioconductor", *Nature Methods* 12: 115-121, 2015——R 语言生信生态（数千个经同行评议流程收录的包）的纲领性论文。Bioconductor 不以单个 GitHub 仓的形式存在，故以本条论文代生态入典（取舍理由见第一批导读卷末留痕）。

## 四、批次规划

- 第一批（已完成）：分析链条 12 仓导读，见 `第一批-导读.md`——覆盖结构预测、基础库、流程引擎、单细胞、比对、变异、格式底层、分发、平台九个层位。
- 第二批（候）：流水线与专题——nf-core/rnaseq（流程生态的代表作）、seqkit（FASTA/Q 处理，国人开发者的代表作）、salmon 与 kallisto（转录组定量的伪比对路线，与 STAR 对读）、IGV（基因组浏览器）、deepTools（表观组分析）、bwa 与 bowtie2（经典比对工具专题）、Bioconductor 生态导读（以包生态而非单仓为单位写）。
- 第三批（候）：数据层专题——公共数据库的取数工具与用法（NCBI Entrez 编程接口、Ensembl REST、UniProt 与 AlphaFold DB 的批量取数），与经典清单的里程碑论文导读穿插。
- 经典材料导读与学习路线图正式版，在项目导读攒到两批后开工，与其他各类的节奏一致。
