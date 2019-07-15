# ShopCarExample
####
通过model中添加是否勾选来更新UI

//增加某个商品数量或者减少某个商品数量更新总价格

```
-(void)updatePriceTotal:(ShopCarModel *)model{
    BOOL isAllChose=YES;
    for(NSInteger i=0;i<_dataArray.count;i++){
        ShopCarModel *shopModel=_dataArray[i];
        if([model.productId isEqualToString:shopModel.productId]){
            shopModel.productCount=model.productCount;
            shopModel.priceTotal=model.priceTotal;
        }
        if(model.isSelect==NO){
            isAllChose=NO;
        }
    }
    [self updateShopCarBuyPrice];
    if(!isAllChose){
        _buyView.choseBtn.selected=NO;
    }
}
```
每次对购物车商品数量增加或者减少，都需要更新总价格
