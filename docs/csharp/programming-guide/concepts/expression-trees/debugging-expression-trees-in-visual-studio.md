---
title: Visual Studio 'da Ifade ağaçlarında hata ayıklamaC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 30f538712881e41b4fd0e62d06f74373d755ea40
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195688"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="431cf-102">Visual Studio 'da Ifade ağaçlarında hata ayıklamaC#()</span><span class="sxs-lookup"><span data-stu-id="431cf-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="431cf-103">Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431cf-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="431cf-104">İfade ağacı yapısına hızlı bir genel bakış almak için, [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade ağaçlarını temsil eden `DebugView` özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431cf-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="431cf-105">(`DebugView` yalnızca hata ayıklama modunda kullanılabilir olduğunu unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="431cf-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![VS hata ayıklayıcı içindeki bir ifade ağacının DebugView 'ın ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="431cf-107">`DebugView` bir dize olduğundan, `DebugView` etiketinin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek Için [yerleşik metin Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431cf-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![DebugView sonuçlarına uygulanan metin görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="431cf-109">Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="431cf-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="431cf-110">[Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ( [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)sağlanan C# [MIT Lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)), ifade ağacını kod olarak işler:</span><span class="sxs-lookup"><span data-stu-id="431cf-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Okunabilir Ifade Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="431cf-112">[Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT Lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacının, özelliklerinin ve ilgili nesnelerin grafik görünümünü sağlar:</span><span class="sxs-lookup"><span data-stu-id="431cf-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Ifade ağacı Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="431cf-114">Bir ifade ağacı için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="431cf-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="431cf-115">**DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="431cf-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="431cf-116">Kullanılabilir görselleştiricilerin listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="431cf-116">A list of available visualizers is displayed.:</span></span> 

    ![Visual Studio 'dan görselleştiricilerin açılmasını gösteren ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="431cf-118">Kullanmak istediğiniz Görselleştirici tıklayın.</span><span class="sxs-lookup"><span data-stu-id="431cf-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431cf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="431cf-119">See also</span></span>

- [<span data-ttu-id="431cf-120">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="431cf-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="431cf-121">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="431cf-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="431cf-122">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="431cf-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="431cf-123">`DebugView` sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431cf-123">`DebugView` syntax</span></span>](debugview-syntax.md)
