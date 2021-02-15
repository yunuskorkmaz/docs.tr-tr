---
description: "Daha fazla bilgi edinin: Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)"
title: Visual Studio’da İfade Ağacı Hatalarını Ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 0221533a79dbc76be479380bd9b6e6df4156e288
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100459090"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="190a6-103">Visual Studio 'da Ifade ağaçlarında hata ayıklama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="190a6-103">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="190a6-104">Uygulamalarınızda hata ayıklarken ifade ağaçlarının yapısını ve içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a6-104">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="190a6-105">İfade ağacı yapısına hızlı bir genel bakış almak için, `DebugView` [özel bir sözdizimi kullanarak](debugview-syntax.md)ifade ağaçlarını temsil eden özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a6-105">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="190a6-106">( `DebugView` Yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="190a6-106">(Note that `DebugView` is available only in debug mode.)</span></span>  

![İfade ağacının DebugView ekranının ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="190a6-108">`DebugView`Bir dize olduğundan, etiketin yanındaki büyüteç simgesinden **metin görselleştiricisi** ' i seçerek birden çok satırda görüntülemek Için [yerleşik metin Görselleştirici](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) ' u kullanabilirsiniz `DebugView` .</span><span class="sxs-lookup"><span data-stu-id="190a6-108">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![DebugView sonuçlarına uygulanan metin görselleştirmesinin ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="190a6-110">Alternatif olarak, şu gibi bir ifade ağaçları için [özel Görselleştirici](/visualstudio/debugger/create-custom-visualizers-of-data) yükleyebilir ve kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="190a6-110">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="190a6-111">[Okunabilir ifadeler](https://github.com/agileobjects/ReadableExpressions) ( [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)kullanılabilir[), ifade](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)ağacını çeşitli Işleme seçenekleriyle birlikte, ayrılabilir C# kodu olarak işler:</span><span class="sxs-lookup"><span data-stu-id="190a6-111">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Okunabilir Ifade Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="190a6-113">[Ifade ağacı görselleştiricisi](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT Lisansı](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)), ifade ağacının ve bağımsız düğümlerinin ağaç görünümünü sağlar; ve Visual Basic sözdizimini kullanarak ifade ağacını işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="190a6-113">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![Ifade ağacı Görselleştirici ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="190a6-115">Bir ifade ağacı için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="190a6-115">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="190a6-116">**DataTips**, bir **Gözcü** penceresinde, **oto** penceresinde veya **Locals** penceresinde ifade ağacının yanında görünen büyüteç simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="190a6-116">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="190a6-117">Kullanılabilir görselleştiricilerin listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="190a6-117">A list of available visualizers is displayed.:</span></span>

    ![Visual Studio 'dan Görselleştiriciler açan kullanıcının ekran görüntüsü.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="190a6-119">Kullanmak istediğiniz Görselleştirici tıklayın.</span><span class="sxs-lookup"><span data-stu-id="190a6-119">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="190a6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="190a6-120">See also</span></span>

- [<span data-ttu-id="190a6-121">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="190a6-121">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="190a6-122">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="190a6-122">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="190a6-123">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="190a6-123">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="190a6-124">`DebugView` sözdizimi</span><span class="sxs-lookup"><span data-stu-id="190a6-124">`DebugView` syntax</span></span>](debugview-syntax.md)
