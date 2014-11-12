iOS_Fonts
=========

自定义字体以及遍历字体库

1.将需要的字体库xxx.ttf添加到工程中，注意一定要在copy bundle resources中存在

2.在info.plist 文件中添加 fonts provided by application 默认为array，也可以使用dictionary  添加value为  xxx.ttf，
可以添加多个，使用的时候写对应字体名字就行。

3.在你的工程就可以直接用了。xx.font = [UIFont fontWithName:@"FZZhunYuan-M02S" size:20.0]；
（注意：这里的字体名字为familyName,不是文件名）通过遍历字体，可以得到所添加字体的familyName，应该是在数组的最后面。

//    遍历所有字体。这是已经把新字体添加进去了
    NSArray *familyNames = [[NSArray alloc] initWithArray:[UIFont familyNames]];
    NSArray *fontNames;
    NSInteger indFamily, indFont;
    for (indFamily=0; indFamily<[familyNames count]; ++indFamily)
    {
        NSLog(@"Family name: %@", [familyNames objectAtIndex:indFamily]);
        fontNames = [[NSArray alloc] initWithArray:
                     [UIFont fontNamesForFamilyName:
                      [familyNames objectAtIndex:indFamily]]];
        for (indFont=0; indFont<[fontNames count]; ++indFont)
        {
            NSLog(@"    Font name: %@", [fontNames objectAtIndex:indFont]);
        }
    }
