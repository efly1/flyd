
    def plot_distribution(self, column, title=None, figsize=(10, 6)):
        """
        绘制分布图
        参数:
            column: 要绘制的列名
            title: 图表标题
            figsize: 图表大小
        """
        if self.processed_data is None:
            print("没有可绘制的数据")
            return False
        
        if column not in self.processed_data.columns:
            print(f"列 '{column}' 不存在于数据中")
            return False
        
        plt.figure(figsize=figsize)
        sns.histplot(self.processed_data[column], kde=True)
        plt.title(title if title else f"{column} 分布")
        plt.xlabel(column)
        plt.ylabel("频率")
        plt.tight_layout()
        plt.show()
        return True
    
    def calculate_economic_indicators(self, price_col='Close'):
        """
        计算基本经济指标
        参数:
            price_col: 价格列名 (默认为'Close')
        """
        if self.processed_data is None:
            print("没有可分析的数据")
            return None
        
        if price_col not in self.processed_data.columns:
            print(f"价格列 '{price_col}' 不存在于数据中")
            return None
        
        prices = self.processed_data[price_col]
        
