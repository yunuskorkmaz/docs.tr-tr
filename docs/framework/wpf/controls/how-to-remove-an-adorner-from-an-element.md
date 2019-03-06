---
title: 'Nasıl yapılır: Öğeden Donatıcıyı Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 0c74fe9ed1e7190ce4ff26a7dbae1413f950ba7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374082"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="af1e4-102">Nasıl yapılır: Öğeden Donatıcıyı Kaldırma</span><span class="sxs-lookup"><span data-stu-id="af1e4-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="af1e4-103">Bu örnek program aracılığıyla belirli bir donatıcı belirtilen bir kaldırma işlemi gösterilmektedir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="af1e4-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af1e4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="af1e4-104">Example</span></span>  
 <span data-ttu-id="af1e4-105">Bu ayrıntılı kod örneğinde ilk donatıcı donatıcıları tarafından döndürülen dizi kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="af1e4-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="af1e4-106">Donatıcıları almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="af1e4-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="af1e4-107">Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir donatıcıları sahip `null` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="af1e4-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="af1e4-108">Bu kod açıkça boş bir dize arar ve burada null dizide nispeten daha sık karşılaşılan olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="af1e4-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="af1e4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="af1e4-109">Example</span></span>  
 <span data-ttu-id="af1e4-110">Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı bir örnek için işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="af1e4-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="af1e4-111">Mümkün olduğu için bu kodu boş bir dize açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="af1e4-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="af1e4-112">Bu kod burada null dizide nadir olması beklenir uygulamaları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="af1e4-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="af1e4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1e4-113">See also</span></span>
- [<span data-ttu-id="af1e4-114">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="af1e4-114">Adorners Overview</span></span>](adorners-overview.md)
