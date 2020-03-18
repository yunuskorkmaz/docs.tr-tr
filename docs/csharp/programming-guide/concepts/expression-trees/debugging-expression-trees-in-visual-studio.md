---
title: Görsel Stüdyoda İfade Ağaçları Nın Hata Ayıklanması (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: cf1708d1155e48d8609baca2067baa66dae08c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169694"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Görsel Stüdyoda İfade Ağaçları Nın Hata Ayıklanması (C#)
Uygulamalarınızı hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz. İfade ağacı yapısına hızlı bir genel bakış `DebugView` elde etmek için, ifade ağaçlarını [özel bir sözdizimi kullanarak](debugview-syntax.md)temsil eden özelliği kullanabilirsiniz. (Yalnızca `DebugView` hata ayıklama modunda kullanılabilenleri unutmayın.)  

![VS hata ayıklama içindeki bir ifade ağacının Hata Ayıklama Görüntüsünün ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

Bir `DebugView` dize olduğundan, `DebugView` etiketin yanındaki büyüteç simgesinden **Metin Görselleştiricisi'ni** seçerek, yerleşik Metin [Görselleştiricisini](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) birden çok satırda görüntülemek için kullanabilirsiniz.

 ![DebugView sonuçlarına uygulanan Metin Görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Alternatif olarak, ifade ağaçları için [özel bir görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:

- [Okunabilir İfadeler](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), [Visual Studio Marketplace'te](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)mevcuttur), ifade ağacını C# kodu olarak işler:

  ![Okunabilir İfadeler görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı),](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar:

  ![İfade Ağacı Görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>İfade ağacı için görselleştirici açmak için  
  
1. **DataTips,** **Watch** penceresi, **Otomatik Ler** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesini tıklatın.  

    Kullanılabilir görselleştiricilerin listesi görüntülenir.:

    ![Visual Studio'dan görselleştiricilerin açılışını gösteren ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Kullanmak istediğiniz görselleştiriciyi tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade Ağaçları (C#)](./index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugger-feature-tour)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`Sözdizimi](debugview-syntax.md)
