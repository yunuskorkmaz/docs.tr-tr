---
title: 'Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma'
description: Alt öğeleri konumlandırmak için bir Windows Presentation Foundation kılavuzunda tanımlanan get ve set yöntemlerini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167398"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="a88ea-103">Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="a88ea-103">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="a88ea-104">Bu örnek, <xref:System.Windows.Controls.Grid> alt öğeleri konumlandırmak için üzerinde tanımlanan get ve set yöntemlerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a88ea-104">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a88ea-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a88ea-105">Example</span></span>  
 <span data-ttu-id="a88ea-106">Aşağıdaki örnek, <xref:System.Windows.Controls.Grid> `grid1` üç sütun ve üç satır içeren bir üst öğe () tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a88ea-106">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="a88ea-107">Bir alt <xref:System.Windows.Shapes.Rectangle> öğe ( `rect1` ) <xref:System.Windows.Controls.Grid> sütun konumu sıfır, satır konumu sıfır olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="a88ea-107">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="a88ea-108"><xref:System.Windows.Controls.Button>öğeleri, içindeki öğesini yeniden konumlandırmak için çağrılabilecek yöntemleri temsil eder <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="a88ea-108"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="a88ea-109">Kullanıcı bir düğmeye tıkladığında ilgili yöntem etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a88ea-109">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="a88ea-110">Aşağıdaki kod arkasındaki örnek, düğme olaylarının işlediği yöntemleri işler <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .</span><span class="sxs-lookup"><span data-stu-id="a88ea-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="a88ea-111">Örnek, <xref:System.Windows.Controls.TextBlock> yeni özellik değerlerini dizeler olarak çıkarmak için ilgili Get yöntemlerini kullanan öğelere bu yöntem çağrılarını yazar.</span><span class="sxs-lookup"><span data-stu-id="a88ea-111">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="a88ea-112">İşte tamamlanan sonuç!</span><span class="sxs-lookup"><span data-stu-id="a88ea-112">Here is the finished result!</span></span>

 ![bir ekran görüntüsü, iki sütunlu bir WPF Kullanıcı arabirimini gösterir ve sağ tarafta 3 x 3 ızgara bulunur ve sol tarafta, kılavuzun sütunları ve satırları arasında renkli bir dikdörtgeni taşıma düğmeleri vardır](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="a88ea-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a88ea-114">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="a88ea-115">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a88ea-115">Panels Overview</span></span>](panels-overview.md)
