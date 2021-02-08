---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: ertelenmiş yüklemeyi kapatma'
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 739c9b0b65eda73d6c504409395eb805b0c02873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785841"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="ce0a9-103">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="ce0a9-103">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="ce0a9-104">Giderek ertelenmiş yüklemeyi devre dışı bırakabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="ce0a9-104">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="ce0a9-105">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="ce0a9-105">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0a9-106">Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce0a9-106">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="ce0a9-107">Daha fazla bilgi için bkz. [nasıl yapılır: bilgileri salt okuma olarak alma](how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="ce0a9-107">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce0a9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce0a9-108">Example</span></span>  

 <span data-ttu-id="ce0a9-109">Aşağıdaki örnek, ' i ' ye ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> gösterilmektedir `false` .</span><span class="sxs-lookup"><span data-stu-id="ce0a9-109">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ce0a9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce0a9-110">See also</span></span>

- [<span data-ttu-id="ce0a9-111">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="ce0a9-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="ce0a9-112">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ce0a9-112">Querying the Database</span></span>](querying-the-database.md)
