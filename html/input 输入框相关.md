##vue�ĵ�ѡ��󶨵�һ���ԣ���ѡ��󶨿����飬ѡ���ɸ������������ѡ�е�ֵ��Ϊdata��
##����Ҫ�󶨵���������vuex������Ҫ
```html
<input :value="message" @input="updateMessage"/>
```

```javascript
computed: {
  ...mapState({
    message: state => state.obj.message
  })
},
methods: {
  updateMessage (e) {
    this.$store.commit('updateMessage', e.target.value)
  }
}
```
����

```html
<input v-model="message">
```

```javascript
computed: {
  message: {
    get () {
      return this.$store.state.obj.message
    },
    set (value) {
      this.$store.commit('updateMessage', value)
    }
  }
}
```