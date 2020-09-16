---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklama (C#)
description: Visual Studio 'da DebugView özelliği hakkında bilgi edinin. İfade ağaçlarının yapısını ve içeriğini çözümlemek için bu özelliği nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: fab378149fb14ccf6a66434c933aa24a8c9c6119
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555620"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio 'da Ifade ağaçlarında hata ayıklama (C#)
Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz. İfade ağacı yapısına hızlı bir genel bakış almak için, `DebugView` [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade ağaçlarını temsil eden özelliğini kullanabilirsiniz. ( `DebugView` Yalnızca hata ayıklama modunda kullanılabilir.)  

![VS hata ayıklayıcı içindeki bir ifade ağacının DebugView 'ın ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

`DebugView`Bir dize olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek Için [yerleşik metin Görselleştirici](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz `DebugView` .

 ![DebugView sonuçlarına uygulanan metin görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:

- [Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ( [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)kullanılabilir[), ifade](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)ağacını çeşitli Işleme seçenekleriyle birlikte, ayrılabilir C# kodu olarak işler:

  ![Okunabilir Ifade Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT Lisansı](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)), ifade ağacının ve ayrı düğümlerin ağaç görünümünü sağlar:

  ![Ifade ağacı Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Bir ifade ağacı için Görselleştirici açmak için  
  
1. **DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.  

    Kullanılabilir görselleştiricilerin listesi görüntülenir.:

    ![Visual Studio 'dan görselleştiricilerin açılmasını gösteren ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Kullanmak istediğiniz Görselleştirici tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](./index.md)
- [Visual Studio'da Hata Ayıklama](/visualstudio/debugger/debugger-feature-tour)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` sözdizimi](debugview-syntax.md)
