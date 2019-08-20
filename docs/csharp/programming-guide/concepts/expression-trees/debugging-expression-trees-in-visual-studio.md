---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklamaC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 19d00aaa99c7ef08e291337f38bf74a3beac12b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595229"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio 'da Ifade ağaçlarında hata ayıklamaC#()
Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz. İfade ağacı yapısına hızlı bir genel bakış almak için, [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade `DebugView` ağaçlarını temsil eden özelliğini kullanabilirsiniz. `DebugView` (Yalnızca hata ayıklama modunda kullanılabilir.)  

![Visual Studio hata ayıklayıcı içindeki ifade ağacının DebugView 'ı](media/debugging-expression-trees-in-visual-studio/debugview.png)

Bir dize `DebugView`olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek için [yerleşik metin Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz. `DebugView`

 ![' DebugView ' sonuçlarına uygulanan metin görselleştiricisi](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:

* [Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ([](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md) [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), ifade ağacını kod olarak C# işler:

  ![Okunabilir Ifadeler görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT Lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar:

  ![ExpressionToString görselleştiricisi](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Bir ifade ağacı için Görselleştirici açmak için  
  
1. **DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.  
  
     Kullanılabilir görselleştiricilerin listesi görüntülenir.: 

      ![Visual Studio 'dan Görselleştiriciler açılıyor](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Kullanmak istediğiniz Görselleştirici tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](./index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`sözdizimi](debugview-syntax.md)
