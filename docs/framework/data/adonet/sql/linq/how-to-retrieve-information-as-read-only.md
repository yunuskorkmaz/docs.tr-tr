---
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 0a6853ef5d0b67e5efb95731adb5a106e8701e0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155841"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="ce251-102">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="ce251-102">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="ce251-103">Verileri değiştirmeyi düşünmüyorsanız, salt okuma sonuçları girerek sorguların performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce251-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="ce251-104">Öğesini olarak ayarlayarak salt okuma işlemini uygulayabilirsiniz <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="ce251-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce251-105">, Olarak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlandığında `false` , örtük olarak <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="ce251-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce251-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce251-106">Example</span></span>  

 <span data-ttu-id="ce251-107">Aşağıdaki kod, çalışan işe alma tarihlerinin salt okunurdur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="ce251-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ce251-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce251-108">See also</span></span>

- [<span data-ttu-id="ce251-109">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="ce251-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="ce251-110">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ce251-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="ce251-111">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="ce251-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
