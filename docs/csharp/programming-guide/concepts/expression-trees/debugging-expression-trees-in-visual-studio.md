---
title: Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 93b1b660181cd81c31055f5d30d43e535171bb55
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195979"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz. İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` ifade ağaçları temsil eden özellik [özel bir söz dizimi kullanılarak](debugview-syntax.md). (Unutmayın `DebugView` yalnızca hata ayıklama modunda kullanılabilir.)  

![DebugView Visual Studio hata ayıklayıcısı içinde ifade ağacı](media/debugging-expression-trees-in-visual-studio/debugview.png)

Bu yana `DebugView` bir dize ise kullanabilirsiniz [yerleşik metin Görselleştiriciye](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) seçerek birden çok satırda, görüntülemek için **metin görselleştiricisi** Büyüteç simgesinin yanındaki gelen `DebugView` Etiket.

 ![Metin Görselleştirici 'DebugView' sonuçlarına uygulandı](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternatif olarak, yükleyip kullanabilir [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) için ifade ağaçları gibi:

* [Okunabilir ifadeleri](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), kullanılabilir [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), işler ifade ağacı C# kod:

  ![Okunabilir ifadeleri görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [İfade ağacı Görselleştiricisini](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacı, özelliklerini, grafik bir görünümünü sağlar ve ilgili nesneleri:

  ![ExpressionToString Görselleştirici](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>İfade ağacı bir görselleştiriciyi açmak için  
  
1. İfade ağacında yanında Büyüteç simgesine tıklayarak **DataTips**, **Watch** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.  
  
     Kullanılabilir görselleştiriciler listesi görüntülenir.: 

      ![Visual Studio'dan açılış görselleştiriciler](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Kullanmak istediğiniz Görselleştirici'a tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` Söz dizimi](debugview-syntax.md)
