---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklama (C#)
description: Visual Studio 'da DebugView özelliği hakkında bilgi edinin. İfade ağaçlarının yapısını ve içeriğini çözümlemek için bu özelliği nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5dcf56f96ecdbfdc3f4cb171fdb30b96456b59c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154138"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="10306-104">Visual Studio 'da Ifade ağaçlarında hata ayıklama (C#)</span><span class="sxs-lookup"><span data-stu-id="10306-104">Debugging Expression Trees in Visual Studio (C#)</span></span>

<span data-ttu-id="10306-105">Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10306-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="10306-106">İfade ağacı yapısına hızlı bir genel bakış almak için, `DebugView` [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade ağaçlarını temsil eden özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10306-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="10306-107">( `DebugView` Yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="10306-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![VS hata ayıklayıcı içindeki bir ifade ağacının DebugView 'ın ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="10306-109">`DebugView`Bir dize olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek Için [yerleşik metin Görselleştirici](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz `DebugView` .</span><span class="sxs-lookup"><span data-stu-id="10306-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![DebugView sonuçlarına uygulanan metin görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="10306-111">Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="10306-111">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="10306-112">[Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ( [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)kullanılabilir[), ifade](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)ağacını çeşitli Işleme seçenekleriyle birlikte, ayrılabilir C# kodu olarak işler:</span><span class="sxs-lookup"><span data-stu-id="10306-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Okunabilir Ifade Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="10306-114">[Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT Lisansı](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)), ifade ağacının ve ayrı düğümlerin ağaç görünümünü sağlar:</span><span class="sxs-lookup"><span data-stu-id="10306-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Ifade ağacı Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="10306-116">Bir ifade ağacı için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="10306-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="10306-117">**DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="10306-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="10306-118">Kullanılabilir görselleştiricilerin listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="10306-118">A list of available visualizers is displayed.:</span></span>

    ![Visual Studio 'dan görselleştiricilerin açılmasını gösteren ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="10306-120">Kullanmak istediğiniz Görselleştirici tıklayın.</span><span class="sxs-lookup"><span data-stu-id="10306-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10306-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10306-121">See also</span></span>

- [<span data-ttu-id="10306-122">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="10306-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="10306-123">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="10306-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="10306-124">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="10306-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="10306-125">`DebugView` sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10306-125">`DebugView` syntax</span></span>](debugview-syntax.md)
