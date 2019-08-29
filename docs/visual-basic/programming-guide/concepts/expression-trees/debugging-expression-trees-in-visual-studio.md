---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 3334828475ef5d933ea660ea33ae264d4ccce172
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106876"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)
Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz. İfade ağacı yapısına hızlı bir genel bakış almak için, [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade `DebugView` ağaçlarını temsil eden özelliğini kullanabilirsiniz. `DebugView` (Yalnızca hata ayıklama modunda kullanılabilir.)  

![Visual Studio hata ayıklayıcı içindeki ifade ağacının DebugView 'ı](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

Bir dize `DebugView`olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek için [yerleşik metin Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz. `DebugView`

 ![' DebugView ' sonuçlarına uygulanan metin görselleştiricisi](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:

- [Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ([](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md) [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), ifade ağacını kod olarak C# işler:

  ![Okunabilir Ifadeler görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT Lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar; ve Visual Basic kodu kullanarak ifade ağacını işleyebilir:

  ![ExpressionToString görselleştiricisi](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Bir ifade ağacı için Görselleştirici açmak için  
  
1. **DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.  
  
     Kullanılabilir görselleştiricilerin listesi görüntülenir.: 

      ![Visual Studio 'dan Görselleştiriciler açılıyor](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. Kullanmak istediğiniz Görselleştirici tıklayın.  

## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`sözdizimi](debugview-syntax.md)
