---
title: "Nasıl yapılır: ListBox'ın Kayma Performansını Artırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552798"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="8b541-102">Nasıl yapılır: ListBox'ın Kayma Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="8b541-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="8b541-103">Varsa bir <xref:System.Windows.Controls.ListBox> sayıda öğe içeren bir kullanıcı kaydırdığında kullanıcı arabirimi yanıt yavaş olabilir <xref:System.Windows.Controls.ListBox> fare tekerleği kullanarak veya bir kaydırma çubuğu sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="8b541-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="8b541-104">Performansını artırabilir <xref:System.Windows.Controls.ListBox> kullanıcı ne zaman kayar ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b541-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b541-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b541-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b541-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b541-106">Description</span></span>  
<span data-ttu-id="8b541-107">Aşağıdaki örnekte bir <xref:System.Windows.Controls.ListBox> ve ayarlar `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> kaydırma sırasında performansı artırmak için.</span><span class="sxs-lookup"><span data-stu-id="8b541-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="8b541-108">Kod</span><span class="sxs-lookup"><span data-stu-id="8b541-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="8b541-109">Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b541-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
