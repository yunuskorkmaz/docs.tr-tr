---
title: Visual Studio’da İfade Ağacı Hatalarını Ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: c6c44d079ab0854b2325b82d3569280752da32fb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266839"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio'da İfade Ağaçlarını Hata Ayıklama (Visual Basic)
Uygulamalarınızı hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz. İfade ağacı yapısına hızlı bir genel bakış `DebugView` elde etmek için, ifade ağaçlarını [özel bir sözdizimi kullanarak](debugview-syntax.md)temsil eden özelliği kullanabilirsiniz. (Yalnızca `DebugView` hata ayıklama modunda kullanılabilenleri unutmayın.)  

![İfade ağacının DebugView ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Bir `DebugView` dize olduğundan, `DebugView` etiketin yanındaki büyüteç simgesinden **Metin Görselleştiricisi'ni** seçerek, yerleşik Metin [Görselleştiricisini](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) birden çok satırda görüntülemek için kullanabilirsiniz.

 ![DebugView sonuçlarına uygulanan Metin Görselleştiriciekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternatif olarak, ifade ağaçları için [özel bir görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:

- [Okunabilir İfadeler](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), [Visual Studio Marketplace'te](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)mevcuttur), ifade ağacını C# kodu olarak işler:

  ![Okunabilir İfadeler görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı),](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar; ve Visual Basic kodunu kullanarak ifade ağacını işleyebilir:

  ![ExpressionToString görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>İfade ağacı için görselleştirici açmak için  
  
1. **DataTips,** **Watch** penceresi, **Otomatik Ler** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesini tıklatın.  
  
    Kullanılabilir görselleştiricilerin listesi görüntülenir.:

    ![Visual Studio'dan görüntüleyenleri açan kullanıcının ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Kullanmak istediğiniz görselleştiriciyi tıklatın.  

## <a name="see-also"></a>Ayrıca bkz.

- [İfade Ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugger-feature-tour)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`Sözdizimi](debugview-syntax.md)
