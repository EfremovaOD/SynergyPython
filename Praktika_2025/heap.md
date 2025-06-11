    #include "gtest/gtest.h"
    #include "heap.h"
    
    class HeapTest : public ::testing::Test {
    protected:
        Heap<int> heap;
    };
    
    TEST_F(HeapTest, TestPushPop) {
        heap.push(3);
        heap.push(1);
        heap.push(4);
        heap.push(1);
        heap.push(5);
        
        EXPECT_EQ(heap.pop(), 5);
        EXPECT_EQ(heap.pop(), 4);
        EXPECT_EQ(heap.pop(), 3);
        EXPECT_EQ(heap.pop(), 1);
        EXPECT_EQ(heap.pop(), 1);
    }

    TEST_F(HeapTest, TestEmpty) {
        EXPECT_TRUE(heap.isEmpty());
        heap.push(1);
        EXPECT_FALSE(heap.isEmpty());
        heap.pop();
        EXPECT_TRUE(heap.isEmpty());
    }
    
    TEST_F(HeapTest, TestSize) {
        EXPECT_EQ(heap.size(), 0);
        heap.push(1);
        EXPECT_EQ(heap.size(), 1);
        heap.push(2);
        EXPECT_EQ(heap.size(), 2);
        heap.pop();
        EXPECT_EQ(heap.size(), 1);
    }
