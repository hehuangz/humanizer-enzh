# humanizer-enzh

A Claude Code skill that removes signs of AI-generated writing from text in both English and Chinese.

English detection is based on Wikipedia's "[Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)" guide (via [blader/humanizer](https://github.com/blader/humanizer)). Chinese detection is based on common AI patterns in technical and business writing.

## What it detects and fixes

**English patterns:**
- Inflated symbolism ("testament to", "beacon of", "tapestry of")
- Promotional language ("seamless", "robust", "cutting-edge")
- AI vocabulary (delve, embark, realm, nuanced, foster, leverage...)
- Copula avoidance ("serves as" instead of "is")
- Em dash overuse, rule of three, chatbot artifacts, and more

**Chinese patterns (中文):**
- 连接词滥用 (首先/其次/最后, 综上所述...)
- 强调词堆砌 (值得注意的是, 需要强调的是...)
- 过度正式化 (运行→跑, 完成→搞定)
- 节奏死板 (每段 3-4 行, 每句长度相似)
- 模板化结构, 虚假对比, 空洞修饰

## Installation

### Claude Code

```bash
claude skill add --from /path/to/humanizer-enzh/SKILL.md
```

Or copy `SKILL.md` to your Claude Code skills directory:

```bash
cp SKILL.md ~/.claude/skills/humanizer-enzh/SKILL.md
```

### OpenCode

Copy `SKILL.md` to your OpenCode skills directory and register it in your configuration.

## Usage

### Default mode (rewrite)

```
/humanizer-enzh "Your text here"
/humanizer-enzh path/to/file.md
```

### Detect-only mode

```
/humanizer-enzh --detect "Your text here"
```

Returns a report of AI patterns found without rewriting.

### With voice sample

```
/humanizer-enzh --voice=path/to/sample.md "Your text here"
```

Matches the writing style from a sample of your own writing.

## Examples

### English

**Before:**
```
First and foremost, it's important to note that implementing this solution
requires a comprehensive understanding of the underlying architecture.
Moreover, one must delve into the nuanced aspects of the system to fully
leverage its robust capabilities.
```

**After:**
```
You'll need to understand how the system works before implementing this.
Dig into the details—especially the parts that aren't obvious.
```

### Chinese

**Before:**
```
首先，我们需要安装依赖。其次，配置环境变量。最后，启动服务。
值得注意的是，端口号需要设置为 8080。通过以上步骤，我们可以
成功部署应用。综上所述，该方案具有良好的可行性。
```

**After:**
```
装好依赖，配一下环境变量，然后跑起来就行。记得端口改成 8080。
这样就能把应用部署上去了。
```

## Credits

- English patterns based on [blader/humanizer](https://github.com/blader/humanizer) (MIT License) and [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- Chinese patterns based on analysis of AI-generated Chinese content in technical and business contexts

## License

MIT
