import streamlit as st
from datetime import datetime

st.set_page_config(page_title="Minha Extensão", page_icon="💪")

st.title("🧬 Minha Extensão")

# Lógica de Horário
agora = datetime.now()
hora = agora.time()
dia = agora.weekday()

st.subheader("📍 Onde devo estar?")
if dia < 5: # Seg-Sex
    if hora < datetime.strptime("17:00", "%H:%M").time():
        st.success("💼 Trabalho: Foco na GD")
    elif hora < datetime.strptime("18:30", "%H:%M").time():
        st.warning("💪 ACADEMIA: Janela de 1h10!")
    elif hora < datetime.strptime("22:30", "%H:%M").time():
        st.error("📚 AULA: Foco total")
    else: st.write("🌙 Casa: Descanso")
elif dia == 5: # Sábado
    st.info("📚 Aula até 11:10 -> 💪 Treino -> 🚗 Buscar Esposa (13:20)")
else: st.write("🍱 Domingo: Marmitas e Finanças")

st.divider()
st.subheader("📖 Estudos Pendentes")
st.checkbox("Revisar matéria de hoje")
st.checkbox("Organização Financeira")

st.divider()
with st.expander("💰 Gasto Rápido"):
    valor = st.number_input("R$:", min_value=0.0)
    if st.button("Salvar"): st.success(f"R$ {valor} guardado!")
