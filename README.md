# Maker Stack

Maker Stack 是一个 Claude Code Marketplace，按 Keystone 的目录格式维护一组可独立安装的开发插件。

## 安装

```text
/plugin marketplace add Capsule7446/maker-stack
/plugin install backend-best-practices@maker-stack
```

## 插件

- [backend-best-practices](https://github.com/Capsule7446/backend-best-practices)
- [consistent-frontend](https://github.com/Capsule7446/consistent-frontend)
- [git-workflow](https://github.com/Capsule7446/git-workflow)
- [svelte-quality-suite](https://github.com/Capsule7446/svelte-quality-suite)
- [go-performance-skills](https://github.com/Capsule7446/go-performance-skills)

权威配置位于 `.claude-plugin/marketplace.json`。

## 验证

```text
claude plugin validate .
```

## License

[MIT](LICENSE)
