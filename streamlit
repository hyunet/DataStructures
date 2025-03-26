import streamlit as st
import numpy as np
import time
import matplotlib.pyplot as plt
import networkx as nx

# Streamlit 기본 설정
st.set_page_config(page_title='자료구조와 알고리즘 시각화', layout='wide')
st.title('자료구조와 알고리즘 시각화 - letsgetIT')

menu = st.sidebar.selectbox("메뉴 선택", ["스택", "큐", "정렬", "트리"])

if menu == "스택":
    st.header("📌 스택 (Stack)")
    stack = []
    col1, col2 = st.columns(2)
    
    with col1:
        push_value = st.text_input("추가할 값 입력")
        if st.button("Push"):
            stack.append(push_value)
    
    with col2:
        if st.button("Pop"):
            if stack:
                stack.pop()
            else:
                st.warning("스택이 비어 있습니다.")
    
    st.write("현재 스택 상태:", stack)

elif menu == "큐":
    st.header("📌 큐 (Queue)")
    queue = []
    col1, col2 = st.columns(2)
    
    with col1:
        enqueue_value = st.text_input("추가할 값 입력")
        if st.button("Enqueue"):
            queue.append(enqueue_value)
    
    with col2:
        if st.button("Dequeue"):
            if queue:
                queue.pop(0)
            else:
                st.warning("큐가 비어 있습니다.")
    
    st.write("현재 큐 상태:", queue)

elif menu == "정렬":
    st.header("📌 정렬 알고리즘 시각화")
    algo = st.selectbox("정렬 알고리즘 선택", ["퀵 정렬", "선택 정렬", "삽입 정렬", "버블 정렬"])
    data = np.random.randint(1, 100, 15)
    st.write("초기 데이터:", data)
    
    fig, ax = plt.subplots()
    ax.bar(range(len(data)), data)
    
    def update_chart():
        st.pyplot(fig)
        time.sleep(0.5)
    
    if algo == "버블 정렬":
        for i in range(len(data)):
            for j in range(len(data) - i - 1):
                if data[j] > data[j+1]:
                    data[j], data[j+1] = data[j+1], data[j]
                    ax.clear()
                    ax.bar(range(len(data)), data)
                    update_chart()
    elif algo == "퀵 정렬":
        def quick_sort(arr, start, end):
            if start < end:
                pivot = partition(arr, start, end)
                quick_sort(arr, start, pivot - 1)
                quick_sort(arr, pivot + 1, end)
                ax.clear()
                ax.bar(range(len(arr)), arr)
                update_chart()
        
        def partition(arr, start, end):
            pivot = arr[end]
            i = start - 1
            for j in range(start, end):
                if arr[j] < pivot:
                    i += 1
                    arr[i], arr[j] = arr[j], arr[i]
            arr[i + 1], arr[end] = arr[end], arr[i + 1]
            return i + 1
        
        quick_sort(data, 0, len(data) - 1)
    
    st.write("정렬 후 데이터:", data)
    st.pyplot(fig)
    st.info("시간 복잡도: 선택된 정렬 알고리즘의 Big-O 표기법을 비교해 보세요.")

elif menu == "트리":
    st.header("📌 트리 탐색")
    
    G = nx.DiGraph()
    G.add_edges_from([(1, 2), (1, 3), (2, 4), (2, 5), (3, 6), (3, 7)])
    pos = nx.spring_layout(G)
    
    fig, ax = plt.subplots()
    nx.draw(G, pos, with_labels=True, node_color='lightblue', edge_color='gray', node_size=2000, ax=ax)
    st.pyplot(fig)
    
    st.write("기본적인 이진 트리 구조를 나타냄.")
