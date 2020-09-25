---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: b2193e7e8bda396451274d2da96e7cb86774fd03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196969"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="5bad5-102">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="5bad5-102">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="5bad5-103">Giderek ertelenmiş yüklemeyi devre dışı bırakabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="5bad5-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="5bad5-104">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="5bad5-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bad5-105">Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bad5-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="5bad5-106">Daha fazla bilgi için bkz. [nasıl yapılır: bilgileri salt okuma olarak alma](how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="5bad5-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bad5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bad5-107">Example</span></span>  

 <span data-ttu-id="5bad5-108">Aşağıdaki örnek, ' i ' ye ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> gösterilmektedir `false` .</span><span class="sxs-lookup"><span data-stu-id="5bad5-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5bad5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bad5-109">See also</span></span>

- [<span data-ttu-id="5bad5-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="5bad5-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="5bad5-111">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="5bad5-111">Querying the Database</span></span>](querying-the-database.md)
