    #include "gtest/gtest.h"
    #include "binary_tree.h"
    
    class BinaryTreeTest : public ::testing::Test {
    protected:
        BinaryTree<int> tree;
    };
    
    TEST_F(BinaryTreeTest, TestPushSearch) {
        tree.push(10);
        tree.push(5);
        tree.push(15);
        tree.push(3);
        tree.push(7);
        
        EXPECT_TRUE(tree.search(10));
        EXPECT_TRUE(tree.search(5));
        EXPECT_TRUE(tree.search(15));
        EXPECT_TRUE(tree.search(3));
        EXPECT_TRUE(tree.search(7));
        EXPECT_FALSE(tree.search(20));
    }
    
    TEST_F(BinaryTreeTest, TestPop) {
        tree.push(10);
        tree.push(5);
        tree.push(15);
        
        tree.pop(10);
        EXPECT_FALSE(tree.search(10));
        EXPECT_TRUE(tree.search(5));
        EXPECT_TRUE(tree.search(15));
        
        tree.pop(5);
        EXPECT_FALSE(tree.search(5));
        EXPECT_TRUE(tree.search(15));
    }
    
    TEST_F(BinaryTreeTest, TestSize) {
        EXPECT_EQ(tree.size(), 0);
        tree.push(1);
        EXPECT_EQ(tree.size(), 1);
        tree.push(2);
        EXPECT_EQ(tree.size(), 2);
        tree.pop(1);
        EXPECT_EQ(tree.
