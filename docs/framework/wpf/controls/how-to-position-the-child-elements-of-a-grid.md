---
title: 'Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 5ccdcb3d166e1b703faff1dc8046e61ee213d12a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187003"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="3d66b-102">Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="3d66b-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="3d66b-103">Bu örnek, get ve üzerinde tanımlanan yöntemlerini nasıl kullanılacağını gösterir. <xref:System.Windows.Controls.Grid> alt öğeleri konumlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="3d66b-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d66b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d66b-104">Example</span></span>  
 <span data-ttu-id="3d66b-105">Aşağıdaki örnek, bir üst tanımlar <xref:System.Windows.Controls.Grid> öğesi (`grid1`) üç ve üç satır vardır.</span><span class="sxs-lookup"><span data-stu-id="3d66b-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="3d66b-106">Bir alt <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) eklenir <xref:System.Windows.Controls.Grid> sütun konumu sıfır satır konumunu sıfır.</span><span class="sxs-lookup"><span data-stu-id="3d66b-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="3d66b-107"><xref:System.Windows.Controls.Button> öğeleri yeniden konumlandırmak için çağrılan yöntemi temsil <xref:System.Windows.Shapes.Rectangle> öğesiyle <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="3d66b-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="3d66b-108">İlgili yöntem, bir kullanıcı bir düğmeyi tıkladığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3d66b-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="3d66b-109">Aşağıdaki arka plan kod örnek yöntemleri işler, düğmeyi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3d66b-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="3d66b-110">Bu yöntem çağrıları örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğeleri al yeni özellik değerlerinin dizeler olarak çıkış yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3d66b-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="3d66b-111">Tamamlanmış sonucu geldi!</span><span class="sxs-lookup"><span data-stu-id="3d66b-111">Here is the finished result!</span></span>
 
 ![bir WPF kullanıcı arabirimi iki sütunlu bir ekran görüntüsü gösterilmektedir, sağ tarafındaki 3 x 3 kılavuz ve sol kılavuza satırlar ve sütunlar arasında renkli bir dikdörtgen geçmek düğmelerini sahiptir](./media/grid-methods-sample.png) 
  
## <a name="see-also"></a><span data-ttu-id="3d66b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d66b-113">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="3d66b-114">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d66b-114">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
