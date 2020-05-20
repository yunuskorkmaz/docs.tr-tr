---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklama (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4c522f2c24cff037ff33d400c8bdfa7500fd4c32
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614388"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="5a678-102">Visual Studio 'da Ifade ağaçlarında hata ayıklama (C#)</span><span class="sxs-lookup"><span data-stu-id="5a678-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="5a678-103">Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a678-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="5a678-104">İfade ağacı yapısına hızlı bir genel bakış almak için, `DebugView` [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade ağaçlarını temsil eden özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a678-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="5a678-105">( `DebugView` Yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="5a678-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![VS hata ayıklayıcı içindeki bir ifade ağacının DebugView 'ın ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="5a678-107">`DebugView`Bir dize olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek Için [yerleşik metin Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz `DebugView` .</span><span class="sxs-lookup"><span data-stu-id="5a678-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![DebugView sonuçlarına uygulanan metin görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="5a678-109">Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a678-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="5a678-110">[Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ( [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)kullanılabilir[), ifade](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)ağacını çeşitli Işleme seçenekleriyle birlikte, ayrılabilir C# kodu olarak işler:</span><span class="sxs-lookup"><span data-stu-id="5a678-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Okunabilir Ifade Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="5a678-112">[Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT Lisansı](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)), ifade ağacının ve ayrı düğümlerin ağaç görünümünü sağlar:</span><span class="sxs-lookup"><span data-stu-id="5a678-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Ifade ağacı Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="5a678-114">Bir ifade ağacı için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="5a678-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="5a678-115">**DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5a678-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="5a678-116">Kullanılabilir görselleştiricilerin listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="5a678-116">A list of available visualizers is displayed.:</span></span>

    ![Visual Studio 'dan görselleştiricilerin açılmasını gösteren ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="5a678-118">Kullanmak istediğiniz Görselleştirici tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5a678-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a678-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a678-119">See also</span></span>

- [<span data-ttu-id="5a678-120">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="5a678-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="5a678-121">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5a678-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="5a678-122">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a678-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="5a678-123">`DebugView`sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a678-123">`DebugView` syntax</span></span>](debugview-syntax.md)
