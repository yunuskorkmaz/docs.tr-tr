---
title: 'Nasıl yapılır: Öğeden Tüm Donatıcıları Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770779"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="195ef-102">Nasıl yapılır: Öğeden Tüm Donatıcıları Kaldırma</span><span class="sxs-lookup"><span data-stu-id="195ef-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="195ef-103">Bu örnekte, program aracılığıyla bir belirtilen tüm donatıcıları kaldırma işlemi gösterilmektedir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="195ef-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="195ef-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="195ef-104">Example</span></span>  
 <span data-ttu-id="195ef-105">Bu ayrıntılı kod örneği tüm donatıcıları tarafından döndürülen dizi kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="195ef-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="195ef-106">Donatıcıları almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="195ef-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="195ef-107">Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir donatıcıları sahip `null` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="195ef-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="195ef-108">Bu kod açıkça boş bir dize arar ve burada null dizide nispeten daha sık karşılaşılan olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="195ef-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="195ef-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="195ef-109">Example</span></span>  
 <span data-ttu-id="195ef-110">Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı bir örnek için işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="195ef-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="195ef-111">Mümkün olduğu için bu kodu boş bir dize açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="195ef-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="195ef-112">Bu kod burada null dizide nadir olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="195ef-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="195ef-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="195ef-113">See also</span></span>

- [<span data-ttu-id="195ef-114">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="195ef-114">Adorners Overview</span></span>](adorners-overview.md)
