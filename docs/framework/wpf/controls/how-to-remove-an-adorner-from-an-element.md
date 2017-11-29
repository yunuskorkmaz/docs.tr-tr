---
title: "Nasıl yapılır: Öğeden Donatıcıyı Kaldırma"
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
helpviewer_keywords: adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe11dc8df1a29518ba05792877bd26670f96b29d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="9c14f-102">Nasıl yapılır: Öğeden Donatıcıyı Kaldırma</span><span class="sxs-lookup"><span data-stu-id="9c14f-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="9c14f-103">Bu örnek program aracılığıyla belirli donatıcının belirtilen bir nasıl kaldırılacağını gösterir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="9c14f-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c14f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c14f-104">Example</span></span>  
 <span data-ttu-id="9c14f-105">Bu ayrıntılı kod örneği tarafından döndürülen donatıcı dizisinden ilk donatıcıyı kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c14f-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="9c14f-106">Donatıcılar almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="9c14f-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="9c14f-107">Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir Donatıcılar sahip `null` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9c14f-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="9c14f-108">Bu kod açıkça boş bir dize arar ve boş bir dizi görece yaygın olarak beklenirken uygulamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="9c14f-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="9c14f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c14f-109">Example</span></span>  
 <span data-ttu-id="9c14f-110">Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı örneğe işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9c14f-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="9c14f-111">Mümkün olması için bu kodu boş dize, açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="9c14f-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="9c14f-112">Bu kod boş bir dizi seyrek olarak beklenirken uygulamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="9c14f-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="9c14f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c14f-113">See Also</span></span>  
 [<span data-ttu-id="9c14f-114">Donatıcılar genel bakış</span><span class="sxs-lookup"><span data-stu-id="9c14f-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
