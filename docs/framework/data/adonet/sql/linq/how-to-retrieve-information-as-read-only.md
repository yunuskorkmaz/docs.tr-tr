---
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793321"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="ea6f2-102">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="ea6f2-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="ea6f2-103">Verileri değiştirmeyi düşünmüyorsanız, salt okuma sonuçları girerek sorguların performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea6f2-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="ea6f2-104">Öğesini olarak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> `false`ayarlayarak salt okuma işlemini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea6f2-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea6f2-105">, Olarak `false`ayarlandığında, örtük<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> olarak olarak ayarlanır. `false` <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A></span><span class="sxs-lookup"><span data-stu-id="ea6f2-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea6f2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea6f2-106">Example</span></span>  
 <span data-ttu-id="ea6f2-107">Aşağıdaki kod, çalışan işe alma tarihlerinin salt okunurdur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="ea6f2-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ea6f2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea6f2-108">See also</span></span>

- [<span data-ttu-id="ea6f2-109">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="ea6f2-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="ea6f2-110">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ea6f2-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="ea6f2-111">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="ea6f2-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
