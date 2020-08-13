# Select <small>下拉选择</small>

:::tip
`Select` 组件可以内联 [`Option`](./option) 或 [`OptionGroup`](./option-group) 组件使用。
:::

## 示例

### 尺寸

可选的尺寸 `ui` 属性值：`xs`/`s`/`m`/`l`。

[[ demo src="/demo/select/size.vue" ]]

### 内联模式

`Select` 组件内支持内联使用 `OptionGroup` 及 `Option` 组件来代替 `options` 属性。

[[ demo src="/demo/select/inline.vue" ]]

### 搜索选项

使用 `searchable` 属性来开启选项搜索。

[[ demo src="/demo/select/searchable.vue" ]]

### 多选

使用 `multiple` 属性来开启多选模式。

[[ demo src="/demo/select/multiple.vue" ]]

## API

### 属性

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `ui` | `string=` | - | [^ui] |
| `options` | `Array<Object>` | - | [^options] |
| `value` | `Array<*>|*` | - | [^value] |
| `multiple` | `boolean` | `false` | 是否允许多选。 |
| `max` | `number` | - | 多选时允许选择的项目上限。 |
| `placeholder` | `string` | `select.placeholder` | 未选择时的占位文本。 |
| `clearable` | `boolean` | `false` | 是否可以清除已选内容。 |
| `searchable` | `boolean` | `false` | 是否允许搜索选项。 |
| `filter` | `function` | - | 选项过滤函数，签名为 `function(option: Object): boolean`。`option` 类型与 `options` 属性中的项相同。返回值表示是否将结果保留在下拉选项列表中。 |
| `disabled` | `boolean=` | `false` | 是否为禁用状态。 |
| `readonly` | `boolean=` | `false` | 是否为只读状态。 |
| `overlay-class` | `string|Array|Object=` | - | 参考 [Overlay](./overlay) 组件的 [`overlay-class` 属性](./overlay#属性)。 |

^^^ui
预设样式。

+++枚举值
| 值 | 描述 |
| -- | -- |
| `xs` | 超小尺寸样式。 |
| `s` | 小尺寸样式。 |
| `m` | 中尺寸样式。 |
| `l` | 大尺寸样式。 |
+++
^^^

^^^options
选项列表，项目的类型为 `{label, value, options, disabled, ...}`。

+++字段详情
| 名称 | 类型 | 描述 |
| -- | -- | -- |
| `label` | `string` | 选项的文字说明。 |
| `value` | `*` | 选项对应的值。 |
| `options` | `Array<Object>=` | 选项的子选项数组，数组项类型同 `options` 属性数组项。 |
| `disabled` | `boolean=` | 选项是否为禁用。 |
+++
^^^

^^^value
:::badges
`v-model`
:::

已选值。
^^^

### 插槽

| 名称 | 描述 |
| -- | -- |
| `default` | 选项列表的内容。在没有指定 `options` 属性时，可以用来直接内联 `Option` 或 `OptionGroup`。 |
| `before` | 选项列表前的内容。无默认内容。 |
| `after` | 选项列表后的内容。无默认内容。 |
| `label` | [^scoped-slot-label] |
| `group-label` | [^scoped-slot-group-label] |
| `option-label` | [^scoped-slot-option-label] |
| `option` | [^scoped-slot-option] |

^^^scoped-slot-label
下拉按钮文本区域。

默认内容：已选项对应的 `label` 属性值或内联模式下已选项的文本内容。

+++作用域参数
| 名称 | 类型 | 描述 |
| -- | -- | -- |
| `label` | `string` | 已选项文本。 |
| `value` | `*` | 已选项值。 |
| `selected` | `boolean` | 是否已选择某个值。 |
| `disabled` | `boolean=` | 选项是否禁用。 |
+++

另外，当前选项数据中除了上面描述的字段之外的其它字段也会自动通过 `v-bind` 进行绑定到作用域参数上。
^^^

^^^scoped-slot-group-label
下拉选项组（带 `options` 的选项）的标题文本区域。

默认内容：选项的 `label` 属性值。

+++作用域参数
| 名称 | 类型 | 描述 |
| -- | -- | -- |
| `label` | `string` | 选项组标题文本。 |
| `disabled` | `boolean=` | 选项组是否禁用。 |
+++

另外，当前选项数据中除了上面描述的字段之外的其它字段也会自动通过 `v-bind` 进行绑定到作用域参数上。
^^^

^^^scoped-slot-option-label
下拉选项（不带 `options` 的选项）的文本区域。

默认内容：选项的 `label` 属性值。

+++作用域参数
| 名称 | 类型 | 描述 |
| -- | -- | -- |
| `label` | `string` | 选项文本。 |
| `value` | `*` | 选项值。 |
| `selected` | `boolean` | 是否已选择。 |
| `disabled` | `boolean=` | 选项是否禁用。 |
+++

另外，当前选项数据中除了上面描述的字段之外的其它字段也会自动通过 `v-bind` 进行绑定到作用域参数上。
^^^

^^^scoped-slot-option
可供选择的下拉选项的整个区域。

默认内容：`Option` 内的组件默认结构。

+++作用域参数
| 名称 | 类型 | 描述 |
| -- | -- | -- |
| `label` | `string` | 选项文本。 |
| `value` | `*` | 选项值。 |
| `selected` | `boolean` | 是否已选择。 |
| `disabled` | `boolean=` | 选项是否禁用。 |
+++

另外，当前选项数据中除了上面描述的字段之外的其它字段也会自动通过 `v-bind` 进行绑定到作用域参数上。
^^^

### 事件

| 名称 | 描述 |
| -- | -- |
| `change` | [^event-change] |

^^^event-change
:::badges
`v-model`
:::

选中状态变化后触发，回调参数为 `(value: *)`。`value` 为当前已选项 `value` 字段的值。
^^^

### 全局配置

| 配置项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `select.placeholder` | `string` | `@@select.placeholder` | 未选择时的占位内容。 |

:::tip
`@@` 开头的值表示引用多语言配置中的相应字段。
:::

### 图标

| 名称 | 描述 |
| -- | -- |
| `expand` | 展开浮层。 |
| `collapse` | 收起浮层。 |