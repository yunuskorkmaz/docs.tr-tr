---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bilgileri Read-Only olarak alma'
title: 'Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 7743e555bcc3f6371ca601d02313e30895e57961
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723458"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="d9815-103">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="d9815-103">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="d9815-104">Verileri değiştirmeyi düşünmüyorsanız, salt okuma sonuçları girerek sorguların performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9815-104">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="d9815-105">Öğesini olarak ayarlayarak salt okuma işlemini uygulayabilirsiniz <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="d9815-105">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9815-106">, Olarak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlandığında `false` , örtük olarak <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="d9815-106">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9815-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9815-107">Example</span></span>  

 <span data-ttu-id="d9815-108">Aşağıdaki kod, çalışan işe alma tarihlerinin salt okunurdur bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="d9815-108">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d9815-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9815-109">See also</span></span>

- [<span data-ttu-id="d9815-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="d9815-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="d9815-111">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="d9815-111">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="d9815-112">Ertelenmiş ve Hemen Yükleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="d9815-112">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
