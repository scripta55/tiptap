<template>
	<div>
		<editor class="editor" :extensions="extensions">

			<div class="menubar is-hidden" :class="{ 'is-focused': focused }" slot="menubar" slot-scope="{ nodes, marks, focused }">
				<div v-if="nodes && marks">

					<button
						class="menubar__button"
						:class="{ 'is-active': marks.bold.active() }"
						@click="marks.bold.command"
					>
						<icon name="bold" />
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': marks.italic.active() }"
						@click="marks.italic.command"
					>
						<icon name="italic" />
					</button>

					<button
						class="menubar__button"
						@click="marks.code.command"
						:class="{ 'is-active': marks.code.active() }
					">
						<icon name="code" />
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.paragraph.active() }"
						@click="nodes.paragraph.command"
					>
						<icon name="paragraph" />
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.heading.active({ level: 1 }) }"
						@click="nodes.heading.command({ level: 1 })"
					>
						H1
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.heading.active({ level: 2 }) }"
						@click="nodes.heading.command({ level: 2 })"
					>
						H2
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.heading.active({ level: 3 }) }"
						@click="nodes.heading.command({ level: 3 })"
					>
						H3
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.bullet_list.active() }"
						@click="nodes.bullet_list.command"
					>
						<icon name="ul" />
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.ordered_list.active() }"
						@click="nodes.ordered_list.command"
					>
						<icon name="ol" />
					</button>

					<button
						class="menubar__button"
						:class="{ 'is-active': nodes.code_block.active() }"
						@click="nodes.code_block.command"
					>
						<icon name="code" />
					</button>

				</div>
			</div>

			<div class="editor__content" slot="content" slot-scope="props">
				<h2>
					Hiding Menu Bar
				</h2>
				<p>
					Click into this text to see the menu. Click outside and the menu will disappear. It's like magic.
				</p>
			</div>

		</editor>
	</div>
</template>

<script>
import Icon from 'Components/Icon'
import { Editor } from 'tiptap'
import {
	BlockquoteNode,
	BulletListNode,
	CodeBlockNode,
	HardBreakNode,
	HeadingNode,
	ListItemNode,
	OrderedListNode,
	TodoItemNode,
	TodoListNode,
	BoldMark,
	CodeMark,
	ItalicMark,
	LinkMark,
	HistoryExtension,
} from 'tiptap-extensions'

export default {
	components: {
		Editor,
		Icon,
	},
	data() {
		return {
			extensions: [
				new BlockquoteNode(),
				new BulletListNode(),
				new CodeBlockNode(),
				new HardBreakNode(),
				new HeadingNode({ maxLevel: 3 }),
				new ListItemNode(),
				new OrderedListNode(),
				new TodoItemNode(),
				new TodoListNode(),
				new BoldMark(),
				new CodeMark(),
				new ItalicMark(),
				new LinkMark(),
				new HistoryExtension(),
			],
		}
	},
}
</script>