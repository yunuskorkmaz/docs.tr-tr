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
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="f6622-102">Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6622-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="f6622-103">Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6622-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="f6622-104">İfade ağacı yapısına hızlı bir genel bakış almak için, [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade `DebugView` ağaçlarını temsil eden özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6622-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="f6622-105">`DebugView` (Yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="f6622-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Visual Studio hata ayıklayıcı içindeki ifade ağacının DebugView 'ı](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="f6622-107">Bir dize `DebugView`olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek için [yerleşik metin Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz. `DebugView`</span><span class="sxs-lookup"><span data-stu-id="f6622-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![' DebugView ' sonuçlarına uygulanan metin görselleştiricisi](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="f6622-109">Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f6622-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="f6622-110">[Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ([](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md) [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), ifade ağacını kod olarak C# işler:</span><span class="sxs-lookup"><span data-stu-id="f6622-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Okunabilir Ifadeler görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- <span data-ttu-id="f6622-112">[Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT Lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar; ve Visual Basic kodu kullanarak ifade ağacını işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="f6622-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![ExpressionToString görselleştiricisi](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="f6622-114">Bir ifade ağacı için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="f6622-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="f6622-115">**DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6622-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="f6622-116">Kullanılabilir görselleştiricilerin listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="f6622-116">A list of available visualizers is displayed.:</span></span> 

      ![Visual Studio 'dan Görselleştiriciler açılıyor](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="f6622-118">Kullanmak istediğiniz Görselleştirici tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6622-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f6622-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6622-119">See also</span></span>

- [<span data-ttu-id="f6622-120">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6622-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="f6622-121">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f6622-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="f6622-122">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6622-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="f6622-123">`DebugView`sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6622-123">`DebugView` syntax</span></span>](debugview-syntax.md)
