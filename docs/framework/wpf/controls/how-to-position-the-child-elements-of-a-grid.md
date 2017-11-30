---
title: "Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dbe0bcb5d3c46edcb97410e00832f1b9d6205b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="12b75-102">Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="12b75-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="12b75-103">Bu örnekte get ve set üzerinde tanımlanan yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Windows.Controls.Grid> alt öğeleri konumlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="12b75-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12b75-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="12b75-104">Example</span></span>  
 <span data-ttu-id="12b75-105">Aşağıdaki örnek, bir üst tanımlar <xref:System.Windows.Controls.Grid> öğesi (`grid1`) üç sütun ve üç satır vardır.</span><span class="sxs-lookup"><span data-stu-id="12b75-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="12b75-106">Bir alt <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) eklenen <xref:System.Windows.Controls.Grid> sütun konumu sıfır'da, konumu sıfır satır.</span><span class="sxs-lookup"><span data-stu-id="12b75-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="12b75-107"><xref:System.Windows.Controls.Button>öğeleri yeniden konumlandırmak için çağrılan yöntemleri temsil eden <xref:System.Windows.Shapes.Rectangle> öğesi içinde <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="12b75-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="12b75-108">Bir kullanıcı bir düğmesine tıkladığında, ilgili yöntem etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="12b75-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="12b75-109">Aşağıdaki arka plan kodu örnek yöntemleri işler, düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları Yükselt.</span><span class="sxs-lookup"><span data-stu-id="12b75-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="12b75-110">Bu yöntem çağrıları örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğelerini alma dizesi olarak yeni özellik değerlerinin çıktısını almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="12b75-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="12b75-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12b75-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="12b75-112">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="12b75-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
