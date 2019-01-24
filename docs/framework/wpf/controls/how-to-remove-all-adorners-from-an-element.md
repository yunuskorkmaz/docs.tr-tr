---
title: 'Nasıl yapılır: Öğeden Tüm Donatıcıları Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 310b0249c215801b2634d51a1a1117bd7df83526
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680207"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="3d3e6-102">Nasıl yapılır: Öğeden Tüm Donatıcıları Kaldırma</span><span class="sxs-lookup"><span data-stu-id="3d3e6-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="3d3e6-103">Bu örnekte, program aracılığıyla bir belirtilen tüm donatıcıları kaldırma işlemi gösterilmektedir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d3e6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d3e6-104">Example</span></span>  
 <span data-ttu-id="3d3e6-105">Bu ayrıntılı kod örneği tüm donatıcıları tarafından döndürülen dizi kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="3d3e6-106">Donatıcıları almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="3d3e6-107">Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir donatıcıları sahip `null` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="3d3e6-108">Bu kod açıkça boş bir dize arar ve burada null dizide nispeten daha sık karşılaşılan olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="3d3e6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d3e6-109">Example</span></span>  
 <span data-ttu-id="3d3e6-110">Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı bir örnek için işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="3d3e6-111">Mümkün olduğu için bu kodu boş bir dize açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="3d3e6-112">Bu kod burada null dizide nadir olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="3d3e6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-113">See also</span></span>
- [<span data-ttu-id="3d3e6-114">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d3e6-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
