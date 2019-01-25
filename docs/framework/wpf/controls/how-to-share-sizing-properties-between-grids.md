---
title: 'Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: e415cb8bf5d2eb53926ae885ba18685390a61201
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694106"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="f2a70-102">Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma</span><span class="sxs-lookup"><span data-stu-id="f2a70-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="f2a70-103">Bu örnek arasında satır ve sütunların boyutlandırma verilerini paylaşma gösterir <xref:System.Windows.Controls.Grid> tutarlı boyutlandırma tutmak için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f2a70-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a70-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2a70-104">Example</span></span>  
 <span data-ttu-id="f2a70-105">Aşağıdaki örnek iki tanıtır <xref:System.Windows.Controls.Grid> öğeleri bir üst öğenin alt öğeleri olarak <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="f2a70-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="f2a70-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Özelliği bağlı <xref:System.Windows.Controls.Grid> üst öğede tanımlanan <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="f2a70-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="f2a70-107">Örneğin, iki kullanarak özellik değeri yönetir <xref:System.Windows.Controls.Button> öğeleri; bir Boolean özelliği değerlerinin her öğe temsil.</span><span class="sxs-lookup"><span data-stu-id="f2a70-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="f2a70-108">Zaman <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> özellik değeri ayarı `true`, her sütunda veya satırda üyesi bir <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> bir satır veya sütun içeriğini bağımsız olarak boyutlandırma bilgi paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f2a70-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="f2a70-109">...</span><span class="sxs-lookup"><span data-stu-id="f2a70-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="f2a70-110">Aşağıdaki arka plan kod örnek yöntemleri işler, düğmeyi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="f2a70-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="f2a70-111">Bu yöntem çağrılarının sonuçlarını örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğeleri al yeni özellik değerlerinin dizeler olarak çıkış yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f2a70-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f2a70-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2a70-112">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="f2a70-113">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f2a70-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
