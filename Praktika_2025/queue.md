#include "gtest/gtest.h"
#include "queue.h"

class QueueTest : public ::testing::Test {
protected:
    Queue<int> queue;
};

TEST_F(QueueTest, TestPushPop) {
    queue.push(1);
    queue.push(2);
    queue.push(3);
    
    EXPECT_EQ(queue.pop(), 1);
    EXPECT_EQ(queue.pop(), 2);
    EXPECT_EQ(queue.pop(), 3);
}

TEST_F(QueueTest, TestEmpty) {
    EXPECT_TRUE(queue.isEmpty());
    queue.push(1);
    EXPECT_FALSE(queue.isEmpty());
    queue.pop();
    EXPECT_TRUE(queue.isEmpty());
}

TEST_F(QueueTest, TestSize) {
    EXPECT_EQ(queue.size(), 0);
    queue.push(1);
    EXPECT_EQ(queue.size(), 1);
    queue.push(2);
    EXPECT_EQ(queue.size(), 2);
    queue.pop();
    EXPECT_EQ(queue.size(), 1);
}
