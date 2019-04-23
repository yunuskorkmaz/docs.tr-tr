---
title: 'Nasıl yapılır: Öğeden Donatıcıyı Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 256dd6fa0117f88aec2ef6b60c6dcd4c33b57855
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212407"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="87dc1-102">Nasıl yapılır: Öğeden Donatıcıyı Kaldırma</span><span class="sxs-lookup"><span data-stu-id="87dc1-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="87dc1-103">Bu örnek program aracılığıyla belirli bir donatıcı belirtilen bir kaldırma işlemi gösterilmektedir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="87dc1-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87dc1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="87dc1-104">Example</span></span>  
 <span data-ttu-id="87dc1-105">Bu ayrıntılı kod örneğinde ilk donatıcı donatıcıları tarafından döndürülen dizi kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="87dc1-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="87dc1-106">Donatıcıları almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="87dc1-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="87dc1-107">Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir donatıcıları sahip `null` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="87dc1-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="87dc1-108">Bu kod açıkça boş bir dize arar ve burada null dizide nispeten daha sık karşılaşılan olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="87dc1-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="87dc1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="87dc1-109">Example</span></span>  
 <span data-ttu-id="87dc1-110">Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı bir örnek için işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="87dc1-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="87dc1-111">Mümkün olduğu için bu kodu boş bir dize açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="87dc1-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="87dc1-112">Bu kod burada null dizide nadir olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="87dc1-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="87dc1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87dc1-113">See also</span></span>

- [<span data-ttu-id="87dc1-114">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="87dc1-114">Adorners Overview</span></span>](adorners-overview.md)
