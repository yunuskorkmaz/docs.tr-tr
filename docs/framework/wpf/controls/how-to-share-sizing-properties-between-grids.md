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
ms.openlocfilehash: bd0f812ce9a15628bd0bddf3a88e898311f0a9d3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373133"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="df45b-102">Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma</span><span class="sxs-lookup"><span data-stu-id="df45b-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="df45b-103">Bu örnek arasında satır ve sütunların boyutlandırma verilerini paylaşma gösterir <xref:System.Windows.Controls.Grid> tutarlı boyutlandırma tutmak için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="df45b-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df45b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="df45b-104">Example</span></span>  
 <span data-ttu-id="df45b-105">Aşağıdaki örnek iki tanıtır <xref:System.Windows.Controls.Grid> öğeleri bir üst öğenin alt öğeleri olarak <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="df45b-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="df45b-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Özelliği bağlı <xref:System.Windows.Controls.Grid> üst öğede tanımlanan <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="df45b-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="df45b-107">Örneğin, iki kullanarak özellik değeri yönetir <xref:System.Windows.Controls.Button> öğeleri; bir Boolean özelliği değerlerinin her öğe temsil.</span><span class="sxs-lookup"><span data-stu-id="df45b-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="df45b-108">Zaman <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> özellik değeri ayarı `true`, her sütunda veya satırda üyesi bir <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> bir satır veya sütun içeriğini bağımsız olarak boyutlandırma bilgi paylaşır.</span><span class="sxs-lookup"><span data-stu-id="df45b-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="df45b-109">...</span><span class="sxs-lookup"><span data-stu-id="df45b-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="df45b-110">Aşağıdaki arka plan kod örnek yöntemleri işler, düğmeyi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="df45b-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="df45b-111">Bu yöntem çağrılarının sonuçlarını örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğeleri al yeni özellik değerlerinin dizeler olarak çıkış yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="df45b-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="df45b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df45b-112">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="df45b-113">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="df45b-113">Panels Overview</span></span>](panels-overview.md)
