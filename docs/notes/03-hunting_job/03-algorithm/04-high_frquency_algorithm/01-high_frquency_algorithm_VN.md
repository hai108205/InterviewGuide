---
layout: post
category: hunting_job
title: Đề thi Thuật toán Tần suất cao trong Phỏng vấn (13 Bài cốt lõi)
tagline: by A Tú
tags:
    - Nguyên tác
    - Tình huống phỏng vấn
    - Câu hỏi trí tuệ
    - Tuyển dụng trường học
    - A Tú
excerpt: Đề thi Thuật toán Tần suất cao trong Phỏng vấn (13 Bài cốt lõi)
comment: false
---

<p id="精选高频面试题"></p>

<h1 align="center">Đề thi Thuật toán Tần suất cao trong Phỏng vấn (13 Bài Cốt Lõi)</h1>

> Phần thuật toán được A Tú đúc kết và phân loại theo nhiều cấp độ từ cơ bản đến nâng cao. Nếu bạn chưa biết bắt đầu từ đâu, hãy xem [Hướng dẫn tại đây](/notes/03-hunting_job/03-algorithm/01-basic-algorithm/01-introduce.md).

Trong các kỳ thi viết và phỏng vấn Live Coding của các tập đoàn công nghệ lớn (Big Tech), độ khó của bài thi viết thường ở mức LeetCode Medium đến Hard, còn phỏng vấn trực tiếp thường yêu cầu code tay chuẩn chỉ (No-IDE / Whiteboard) các bài kinh điển mức Medium hoặc Easy. Dưới đây là **13 dạng bài có tần suất xuất hiện cao nhất**!

---

<p id="合并有序链表"></p>

## 1. Gộp hai Danh sách Liên kết có thứ tự (Merge Two Sorted Lists)

[Link LeetCode](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

- **Đề bài**: Gộp 2 danh sách liên kết đơn đã sắp xếp tăng dần thành 1 danh sách mới duy nhất cũng có thứ tự tăng dần.

```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int _val) : val(_val), next(nullptr) {}
};

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    ListNode dummy(0);
    ListNode* cur = &dummy;

    while (l1 != nullptr && l2 != nullptr) {
        if (l1->val <= l2->val) {
            cur->next = l1;
            l1 = l1->next;
        } else {
            cur->next = l2;
            l2 = l2->next;
        }
        cur = cur->next;
    }
    cur->next = (l1 != nullptr) ? l1 : l2;
    return dummy.next;
}
```

---

<p id="反转链表"></p>

## 2. Đảo ngược Danh sách Liên kết (Reverse Linked List)

- **Đề bài**: Đảo ngược một danh sách liên kết đơn $1 \to 2 \to 3 \to 4 \to 5 \to \text{NULL}$ thành $5 \to 4 \to 3 \to 2 \to 1 \to \text{NULL}$.

```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;
    ListNode* cur = head;
    while (cur != nullptr) {
        ListNode* nextTemp = cur->next;
        cur->next = prev;
        prev = cur;
        cur = nextTemp;
    }
    return prev;
}
```

---

<p id="单例模式"></p>

## 3. Cài đặt Mẫu Thiết kế Singleton (Design Pattern Singleton)

### Bản Eager Initialization (Khởi tạo sớm - An toàn đa luồng)
```cpp
class SingletonEager {
private:
    SingletonEager() {}
    static SingletonEager* instance;
public:
    static SingletonEager* getInstance() {
        return instance;
    }
};
SingletonEager* SingletonEager::instance = new SingletonEager();
```

### Bản Meyer's Singleton (C++11 Thread-Safe Magic Static - Khuyên dùng nhất)
```cpp
class Singleton {
private:
    Singleton() {}
public:
    static Singleton& getInstance() {
        static Singleton instance; // Đảm bảo khởi tạo 1 lần duy nhất và thread-safe từ C++11
        return instance;
    }
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;
};
```

---

<p id="简单工厂模式"></p>

## 4. Mẫu Thiết kế Simple Factory Pattern

```cpp
#include <iostream>
#include <memory>
using namespace std;

class Product {
public:
    virtual void show() = 0;
    virtual ~Product() = default;
};

class ProductA : public Product {
public:
    void show() override { cout << "Product A" << endl; }
};

class ProductB : public Product {
public:
    void show() override { cout << "Product B" << endl; }
};

enum class ProductType { TYPE_A, TYPE_B };

class SimpleFactory {
public:
    static unique_ptr<Product> createProduct(ProductType type) {
        switch (type) {
            case ProductType::TYPE_A: return make_unique<ProductA>();
            case ProductType::TYPE_B: return make_unique<ProductB>();
            default: return nullptr;
        }
    }
};
```

---

<p id="快速排序"></p>

## 5. Sắp xếp Nhanh (Quick Sort)

```cpp
void quickSort(vector<int>& nums, int low, int high) {
    if (low >= high) return;
    int first = low, last = high;
    int key = nums[first];

    while (first < last) {
        while (first < last && nums[last] >= key) last--;
        if (first < last) nums[first++] = nums[last];

        while (first < last && nums[first] <= key) first++;
        if (first < last) nums[last--] = nums[first];
    }
    nums[first] = key;

    quickSort(nums, low, first - 1);
    quickSort(nums, first + 1, high);
}
```

---

<p id="归并排序"></p>

## 6. Sắp xếp Trộn (Merge Sort)

```cpp
void mergeSortCore(vector<int>& nums, vector<int>& temp, int low, int high) {
    if (low >= high) return;
    int mid = low + (high - low) / 2;
    mergeSortCore(nums, temp, low, mid);
    mergeSortCore(nums, temp, mid + 1, high);

    int i = low, j = mid + 1, k = low;
    while (i <= mid && j <= high) {
        temp[k++] = (nums[i] <= nums[j]) ? nums[i++] : nums[j++];
    }
    while (i <= mid) temp[k++] = nums[i++];
    while (j <= high) temp[k++] = nums[j++];

    for (int p = low; p <= high; ++p) nums[p] = temp[p];
}

void mergeSort(vector<int>& nums) {
    vector<int> temp(nums.size());
    mergeSortCore(nums, temp, 0, nums.size() - 1);
}
```

---

<p id="实现一个堆排序"></p>

## 7. Sắp xếp Vun đống (Heap Sort)

```cpp
void heapify(vector<int>& arr, int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest]) largest = left;
    if (right < n && arr[right] > arr[largest]) largest = right;

    if (largest != i) {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = n / 2 - 1; i >= 0; i--) heapify(arr, n, i);
    for (int i = n - 1; i > 0; i--) {
        swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}
```

---

<p id="设计缓存"></p>

## 8. Thiết kế Bộ đệm LRU Cache (LeetCode 146)

[Link LeetCode](https://leetcode-cn.com/problems/lru-cache-lcci)

- **Cấu trúc dữ liệu**: Kết hợp **Bảng băm (HashMap)** để đạt tốc độ truy vấn $O(1)$ và **Danh sách liên kết đôi (Doubly LinkedList)** để đưa phần tử vừa truy cập lên đầu và xóa phần tử ít dùng nhất ở cuối trong $O(1)$.

```cpp
#include <unordered_map>
using namespace std;

struct Node {
    int key, val;
    Node* prev;
    Node* next;
    Node(int k, int v) : key(k), val(v), prev(nullptr), next(nullptr) {}
};

class LRUCache {
private:
    int cap;
    Node* head;
    Node* tail;
    unordered_map<int, Node*> cache;

    void removeNode(Node* node) {
        node->prev->next = node->next;
        node->next->prev = node->prev;
    }

    void addToHead(Node* node) {
        node->next = head->next;
        node->prev = head;
        head->next->prev = node;
        head->next = node;
    }

    void moveToHead(Node* node) {
        removeNode(node);
        addToHead(node);
    }

    Node* removeTail() {
        Node* res = tail->prev;
        removeNode(res);
        return res;
    }

public:
    LRUCache(int capacity) : cap(capacity) {
        head = new Node(-1, -1);
        tail = new Node(-1, -1);
        head->next = tail;
        tail->prev = head;
    }

    int get(int key) {
        if (cache.find(key) == cache.end()) return -1;
        Node* node = cache[key];
        moveToHead(node);
        return node->val;
    }

    void put(int key, int value) {
        if (cache.find(key) != cache.end()) {
            Node* node = cache[key];
            node->val = value;
            moveToHead(node);
        } else {
            if (cache.size() >= cap) {
                Node* deleted = removeTail();
                cache.erase(deleted->key);
                delete deleted;
            }
            Node* newNode = new Node(key, value);
            cache[key] = newNode;
            addToHead(newNode);
        }
    }
};
```

---

<p id="重排链表"></p>

## 9. Sắp xếp lại Danh sách Liên kết (Reorder List - LeetCode 143)

- **Đề bài**: Cho $L_0 \to L_1 \to \dots \to L_{n-1} \to L_n$, sắp xếp lại thành $L_0 \to L_n \to L_1 \to L_{n-1} \to L_2 \to \dots$
- **3 bước giải quyết**:
  1. Tìm điểm giữa của danh sách bằng con trỏ Nhanh - Chậm (Fast & Slow Pointers).
  2. Đảo ngược nửa sau danh sách liên kết.
  3. Đan xen (Merge) hai nửa danh sách lại với nhau.

```cpp
void reorderList(ListNode* head) {
    if (!head || !head->next) return;

    // 1. Tìm trung điểm
    ListNode *slow = head, *fast = head;
    while (fast->next && fast->next->next) {
        slow = slow->next;
        fast = fast->next->next;
    }

    // 2. Đảo ngược nửa sau
    ListNode* second = slow->next;
    slow->next = nullptr;
    ListNode* prev = nullptr;
    while (second) {
        ListNode* nextTemp = second->next;
        second->next = prev;
        prev = second;
        second = nextTemp;
    }

    // 3. Đan xen hai nửa
    ListNode* first = head;
    second = prev;
    while (second) {
        ListNode* t1 = first->next;
        ListNode* t2 = second->next;
        first->next = second;
        second->next = t1;
        first = t1;
        second = t2;
    }
}
```

---

<p id="奇偶链表"></p>

## 10. Danh sách Liên kết Chẵn Lẻ (Odd-Even Linked List - LeetCode 328)

- **Đề bài**: Gom tất cả các nút ở vị trí chỉ số lẻ lên trước, các nút ở vị trí chỉ số chẵn ra sau, duy trì tính ổn định tương đối và bộ nhớ $O(1)$.

```cpp
ListNode* oddEvenList(ListNode* head) {
    if (!head || !head->next) return head;
    ListNode* odd = head;
    ListNode* even = head->next;
    ListNode* evenHead = even;

    while (even && even->next) {
        odd->next = even->next;
        odd = odd->next;
        even->next = odd->next;
        even = even->next;
    }
    odd->next = evenHead;
    return head;
}
```

---

<p id="三个线程"></p>

## 11. Ba Luồng in xen kẽ A, B, C (Thread Synchronization)

```cpp
#include <iostream>
#include <thread>
#include <mutex>
#include <condition_variable>

using namespace std;

mutex mtx;
condition_variable cv;
int state = 0; // 0 -> in A, 1 -> in B, 2 -> in C

void printLetter(int id, char letter) {
    for (int i = 0; i < 10; ++i) {
        unique_lock<mutex> lock(mtx);
        cv.wait(lock, [id] { return state == id; });
        cout << letter << " ";
        state = (state + 1) % 3;
        cv.notify_all();
    }
}

int main() {
    thread t1(printLetter, 0, 'A');
    thread t2(printLetter, 1, 'B');
    thread t3(printLetter, 2, 'C');

    t1.join();
    t2.join();
    t3.join();
    cout << endl;
    return 0;
}
```

---

<p id="涛普问题"></p>

## 12. Bài toán Top K (K-th Largest / Top K Elements)

- **Cách 1: Min-Heap (Kích thước $K$)**: Quét mảng, duy trì $K$ phần tử lớn nhất trong Min-Heap. Độ phức tạp: $O(N \log K)$.
- **Cách 2: QuickSelect (Phân vùng như Quick Sort)**: Kỳ vọng $O(N)$ thời gian.

```cpp
int partition(vector<int>& nums, int l, int r) {
    int pivot = nums[r], i = l;
    for (int j = l; j < r; j++) {
        if (nums[j] >= pivot) { // Sắp giảm dần để tìm phần tử lớn thứ K
            swap(nums[i++], nums[j]);
        }
    }
    swap(nums[i], nums[r]);
    return i;
}

int quickSelect(vector<int>& nums, int l, int r, int k) {
    if (l == r) return nums[l];
    int p = partition(nums, l, r);
    if (p == k - 1) return nums[p];
    if (p > k - 1) return quickSelect(nums, l, p - 1, k);
    return quickSelect(nums, p + 1, r, k);
}

int findKthLargest(vector<int>& nums, int k) {
    return quickSelect(nums, 0, nums.size() - 1, k);
}
```

---

<p id="布隆过滤器原理与优点"></p>

## 13. Nguyên lý và Ưu thế của Bộ lọc Bloom (Bloom Filter)

- **Bản chất**: Là một mảng bit (Bit Array) kích thước $m$ kết hợp với $k$ hàm băm độc lập.
- **Quy trình thêm phần tử**: Tính $k$ giá trị băm của phần tử và bật các bit tương ứng thành 1 (`bits[h_i(x)] = 1`).
- **Quy trình kiểm tra**: Tính $k$ hàm băm:
  - Nếu có **bất kỳ bit nào bằng 0** $\implies$ **Phần tử CHẮC CHẮN 100% KHÔNG TỒN TẠI** trong tập hợp.
  - Nếu **tất cả $k$ bit đều bằng 1** $\implies$ **Phần tử CÓ THỂ TỒN TẠI** (tồn tại xác suất dương tính giả - False Positive do va chạm băm).
- **Ưu điểm**: Cực kỳ tiết kiệm bộ nhớ RAM ($O(1)$) và tốc độ kiểm tra $O(k)$ siêu tốc.
