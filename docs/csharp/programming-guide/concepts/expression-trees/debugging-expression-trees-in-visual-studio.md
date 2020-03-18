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
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="d4c1b-102">Görsel Stüdyoda İfade Ağaçları Nın Hata Ayıklanması (C#)</span><span class="sxs-lookup"><span data-stu-id="d4c1b-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="d4c1b-103">Uygulamalarınızı hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4c1b-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="d4c1b-104">İfade ağacı yapısına hızlı bir genel bakış `DebugView` elde etmek için, ifade ağaçlarını [özel bir sözdizimi kullanarak](debugview-syntax.md)temsil eden özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4c1b-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="d4c1b-105">(Yalnızca `DebugView` hata ayıklama modunda kullanılabilenleri unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="d4c1b-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![VS hata ayıklama içindeki bir ifade ağacının Hata Ayıklama Görüntüsünün ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="d4c1b-107">Bir `DebugView` dize olduğundan, `DebugView` etiketin yanındaki büyüteç simgesinden **Metin Görselleştiricisi'ni** seçerek, yerleşik Metin [Görselleştiricisini](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) birden çok satırda görüntülemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4c1b-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![DebugView sonuçlarına uygulanan Metin Görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="d4c1b-109">Alternatif olarak, ifade ağaçları için [özel bir görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4c1b-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="d4c1b-110">[Okunabilir İfadeler](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), [Visual Studio Marketplace'te](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)mevcuttur), ifade ağacını C# kodu olarak işler:</span><span class="sxs-lookup"><span data-stu-id="d4c1b-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Okunabilir İfadeler görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="d4c1b-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı),](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar:</span><span class="sxs-lookup"><span data-stu-id="d4c1b-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![İfade Ağacı Görselleştiricisinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="d4c1b-114">İfade ağacı için görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="d4c1b-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="d4c1b-115">**DataTips,** **Watch** penceresi, **Otomatik Ler** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d4c1b-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="d4c1b-116">Kullanılabilir görselleştiricilerin listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="d4c1b-116">A list of available visualizers is displayed.:</span></span>

    ![Visual Studio'dan görselleştiricilerin açılışını gösteren ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="d4c1b-118">Kullanmak istediğiniz görselleştiriciyi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d4c1b-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c1b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4c1b-119">See also</span></span>

- [<span data-ttu-id="d4c1b-120">İfade Ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="d4c1b-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="d4c1b-121">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d4c1b-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="d4c1b-122">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4c1b-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="d4c1b-123">`DebugView`Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4c1b-123">`DebugView` syntax</span></span>](debugview-syntax.md)
