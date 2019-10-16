---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 51579c74ecbebbfb7da8bf20bef7592980ec437c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320349"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)
Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz. İfade ağacı yapısına hızlı bir genel bakış almak için, [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade ağaçlarını temsil eden `DebugView` özelliğini kullanabilirsiniz. (@No__t-0 ' ın yalnızca hata ayıklama modunda kullanılabilir olduğunu unutmayın.)  

![İfade ağacının DebugView ekranının ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

@No__t-0 bir dize olduğundan, `DebugView` etiketinin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek Için [yerleşik metin Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz.

 ![DebugView sonuçlarına uygulanan metin görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:

- [Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ( [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)sağlanan C# [MIT Lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)), ifade ağacını kod olarak işler:

  ![Okunabilir Ifade Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT Lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar; ve Visual Basic kodu kullanarak ifade ağacını işleyebilir:

  ![ExpressionToString görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Bir ifade ağacı için Görselleştirici açmak için  
  
1. **DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.  
  
    Kullanılabilir görselleştiricilerin listesi görüntülenir.: 

    ![Visual Studio 'dan Görselleştiriciler açan kullanıcının ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Kullanmak istediğiniz Görselleştirici tıklayın.  

## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` sözdizimi](debugview-syntax.md)
