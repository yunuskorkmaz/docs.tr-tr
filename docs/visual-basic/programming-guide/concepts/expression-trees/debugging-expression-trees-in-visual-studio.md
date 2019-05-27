---
title: Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 9aead09e0e9469f13e2d6befbad444d3c7fecabd
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196020"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="54c91-102">Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="54c91-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="54c91-103">Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54c91-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="54c91-104">İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` ifade ağaçları temsil eden özellik [özel bir söz dizimi kullanılarak](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="54c91-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="54c91-105">(Unutmayın `DebugView` yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="54c91-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView Visual Studio hata ayıklayıcısı içinde ifade ağacı](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="54c91-107">Bu yana `DebugView` bir dize ise kullanabilirsiniz [yerleşik metin Görselleştiriciye](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) seçerek birden çok satırda, görüntülemek için **metin görselleştiricisi** Büyüteç simgesinin yanındaki gelen `DebugView` Etiket.</span><span class="sxs-lookup"><span data-stu-id="54c91-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Metin Görselleştirici 'DebugView' sonuçlarına uygulandı](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="54c91-109">Alternatif olarak, yükleyip kullanabilir [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) için ifade ağaçları gibi:</span><span class="sxs-lookup"><span data-stu-id="54c91-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

* <span data-ttu-id="54c91-110">[Okunabilir ifadeleri](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), kullanılabilir [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), işler ifade ağacı C# kod:</span><span class="sxs-lookup"><span data-stu-id="54c91-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Okunabilir ifadeleri görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="54c91-112">[İfade ağacı Görselleştiricisini](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacı, özellikler ve ilgili nesneleri; grafik bir görünümünü sunar ve Visual Basic kodunu kullanarak ifade ağacı işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="54c91-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![ExpressionToString Görselleştirici](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="54c91-114">İfade ağacı bir görselleştiriciyi açmak için</span><span class="sxs-lookup"><span data-stu-id="54c91-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="54c91-115">İfade ağacında yanında Büyüteç simgesine tıklayarak **DataTips**, **Watch** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="54c91-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="54c91-116">Kullanılabilir görselleştiriciler listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="54c91-116">A list of available visualizers is displayed.:</span></span> 

      ![Visual Studio'dan açılış görselleştiriciler](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="54c91-118">Kullanmak istediğiniz Görselleştirici'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54c91-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="54c91-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54c91-119">See also</span></span>

- [<span data-ttu-id="54c91-120">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54c91-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="54c91-121">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="54c91-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="54c91-122">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54c91-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="54c91-123">`DebugView` Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="54c91-123">`DebugView` syntax</span></span>](debugview-syntax.md)
