<script setup>
import { ref } from "vue";

const fontList = ref([
	"Arial",
	"Verdana",
	"Times New Roman",
	"Garamond",
	"Georgia",
	"Courier New",
	"Cursive",
]);

const fontColorSelected = ref("");
const backColorSelected = ref("");
const generateButtons = ref([
	{ type: "button", id: "bold", classIcon: "fa-solid fa-bold" },
	{ type: "button", id: "superscript", classIcon: "fa-solid fa-superscript" },
	{ type: "button", id: "subscript", classIcon: "fa-solid fa-subscript" },
	{
		type: "button",
		id: "insertOrderedList",
		classIcon: "fa-solid fa-list-ol",
	},
	{
		type: "button",
		id: "insertUnorderedList",
		classIcon: "fa-solid fa-list",
	},
	{ type: "button", id: "undo", classIcon: "fa-solid fa-rotate-left" },
	{ type: "button", id: "redo", classIcon: "fa-solid fa-rotate-right" },
	{ type: "button", id: "createLink", classIcon: "fa fa-link" },
	{ type: "button", id: "unlink", classIcon: "fa fa-unlink" },
	{ type: "button", id: "justifyLeft", classIcon: "fa-solid fa-align-left" },
	{
		type: "button",
		id: "justifyCenter",
		classIcon: "fa-solid fa-align-center",
	},
	{
		type: "button",
		id: "justifyRight",
		classIcon: "fa-solid fa-align-right",
	},
	{
		type: "button",
		id: "justifyFull",
		classIcon: "fa-solid fa-align-justify",
	},
	{ type: "button", id: "indent", classIcon: "fa-solid fa-indent" },
	{ type: "button", id: "outdent", classIcon: "fa-solid fa-outdent" },
]);
</script>

<template>
	<section
		class="w-full h-screen flex flex-wrap items-center justify-center bg-gray-500"
	>
		<div class="w-[50%] h-4/5 rounded-2xl bg-white">
			<div
				class="flex flex-wrap justify-center items-center gap-3 mt-3 0"
			>
				<template
					v-for="(value, index) in generateButtons"
					:key="index"
					:id="value.id"
				>
					<div
						class="border-2 border-bg-slate-200 p-2 text-sm hover:bg-slate-200"
					>
						<input :type="value.type" :id="value.id" />
						<i :class="value.classIcon"></i>
					</div>
				</template>

				<select id="formatBlock" class="adv-option-button">
					<option value="H1">H1</option>
					<option value="H2">H2</option>
					<option value="H3">H3</option>
					<option value="H4">H4</option>
					<option value="H5">H5</option>
					<option value="H6">H6</option>
				</select>

				<select id="fontName" class="adv-option-button">
					<option
						v-for="(value, index) in fontList"
						:key="index"
						:value="value"
					>
						{{ value }}
					</option>
				</select>

				<select id="fontSize" class="adv-option-button">
					<option v-for="(qtd, index) in 8" :key="index">
						{{ qtd }}
					</option>
				</select>

				<div class="input-wrapper">
					<input
						type="color"
						id="foreColor"
						class="adv-option-button"
						v-model="fontColorSelected"
					/>
					<label for="foreColor">Cor da Fonte</label>
				</div>
				<div class="input-wrapper">
					<input
						type="color"
						id="backColor"
						class="adv-option-button"
						v-model="backColorSelected"
					/>
					<label for="backColor">Destaque Fundo</label>
				</div>
			</div>

			<div id="text-input" contenteditable="true"></div>
		</div>
	</section>
</template>

<style scoped></style>
