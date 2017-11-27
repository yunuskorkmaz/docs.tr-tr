---
title: "Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma"
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
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0e3be0a0b550f6fbbc9876709094d4a23abe1a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="9fd38-102">Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma</span><span class="sxs-lookup"><span data-stu-id="9fd38-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="9fd38-103">Bu örnek arasındaki satırları ve sütunları boyutlandırma verisinin nasıl paylaşılacağını gösterir <xref:System.Windows.Controls.Grid> boyutlandırmayı tutarlı saklamak için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9fd38-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fd38-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fd38-104">Example</span></span>  
 <span data-ttu-id="9fd38-105">Aşağıdaki örnekte iki tanıtır <xref:System.Windows.Controls.Grid> öğeler alt öğelerin üst öğesi olarak <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="9fd38-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="9fd38-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Özelliği bağlı <xref:System.Windows.Controls.Grid> üst öğede tanımlanan <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="9fd38-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="9fd38-107">İki kullanarak örnek özellik değerini yönetir <xref:System.Windows.Controls.Button> öğeleri; bir Boolean özellik değerlerinin her öğesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fd38-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="9fd38-108">Zaman <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> özellik değeri ayarlanmış `true`, her bir sütun veya satır üyesi bir <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> bir satır veya sütun içeriği ne olursa olsun boyutlandırma bilgi paylaşır.</span><span class="sxs-lookup"><span data-stu-id="9fd38-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="9fd38-109">...</span><span class="sxs-lookup"><span data-stu-id="9fd38-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="9fd38-110">Aşağıdaki arka plan kodu örnek yöntemleri işler, düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="9fd38-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="9fd38-111">Bu yöntem çağrılarının sonuçlarını örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğelerini alma dizesi olarak yeni özellik değerlerinin çıktısını almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9fd38-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9fd38-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fd38-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [<span data-ttu-id="9fd38-113">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9fd38-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
