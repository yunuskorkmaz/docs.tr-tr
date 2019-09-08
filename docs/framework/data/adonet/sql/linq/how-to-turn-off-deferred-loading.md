---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781659"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="b57db-102">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="b57db-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="b57db-103">Giderek ertelenmiş yüklemeyi <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b57db-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="b57db-104">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="b57db-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b57db-105">Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="b57db-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="b57db-106">Daha fazla bilgi için [nasıl yapılır: Bilgileri salt okuma](how-to-retrieve-information-as-read-only.md)olarak alın.</span><span class="sxs-lookup"><span data-stu-id="b57db-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b57db-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b57db-107">Example</span></span>  
 <span data-ttu-id="b57db-108">Aşağıdaki örnek, ' i ' ye <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b57db-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b57db-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b57db-109">See also</span></span>

- [<span data-ttu-id="b57db-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="b57db-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="b57db-111">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="b57db-111">Querying the Database</span></span>](querying-the-database.md)
