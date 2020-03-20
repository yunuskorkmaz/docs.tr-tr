---
title: 'Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186714"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="8a0cd-102">Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="8a0cd-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="8a0cd-103">Bu örnek, alt öğeleri <xref:System.Windows.Controls.Grid> konumlandırmak için tanımlanan alma ve ayarlama yöntemlerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a0cd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a0cd-104">Example</span></span>  
 <span data-ttu-id="8a0cd-105">Aşağıdaki örnekte, üç <xref:System.Windows.Controls.Grid> sütun`grid1`ve üç satıriçeren bir üst öğe ( ) tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="8a0cd-106">Bir <xref:System.Windows.Shapes.Rectangle> alt`rect1`öğe ( ) <xref:System.Windows.Controls.Grid> sütun konumu sıfır, satır konumu sıfır eklenir.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="8a0cd-107"><xref:System.Windows.Controls.Button>öğeleri içinde <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Grid>öğeyi yeniden konumlandırmak için çağrılabilir yöntemleri temsil .</span><span class="sxs-lookup"><span data-stu-id="8a0cd-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="8a0cd-108">Bir kullanıcı bir düğmeyi tıklattığında, ilgili yöntem etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="8a0cd-109">Aşağıdaki kod arkası örneği, düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylarının yükselttiğini işler.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="8a0cd-110">Örnek, ilgili get <xref:System.Windows.Controls.TextBlock> yöntemlerini kullanan elemanlara bu yöntem çağrılarını yeni özellik değerlerini dizeleri olarak çıktıolarak yazar.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="8a0cd-111">İşte bitmiş sonuç!</span><span class="sxs-lookup"><span data-stu-id="8a0cd-111">Here is the finished result!</span></span>

 ![ekran görüntüsü iki sütunlu bir WPF kullanıcı arabirimini betimliyor, sağ tarafında 3 x 3 ızgara ve sol tarafta ızgara sütunları ve satırları arasında renkli bir dikdörtgen taşımak için düğmeleri var](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="8a0cd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a0cd-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="8a0cd-114">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8a0cd-114">Panels Overview</span></span>](panels-overview.md)
