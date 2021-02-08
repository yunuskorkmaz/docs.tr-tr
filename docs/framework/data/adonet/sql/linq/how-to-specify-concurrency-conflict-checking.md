---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Concurrency-Conflict denetleme belirtme'
title: 'Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: a1c1c771dba95e558d86764d023625a63e9e53bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785932"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="65f7c-103">Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme</span><span class="sxs-lookup"><span data-stu-id="65f7c-103">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="65f7c-104">Çağırdığınızda, hangi veritabanının sütunlarının eşzamanlılık çakışmaları için denetleneceğini belirtebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="65f7c-104">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="65f7c-105">Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirtme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="65f7c-105">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65f7c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f7c-106">Example</span></span>  

 <span data-ttu-id="65f7c-107">Aşağıdaki kod, `HomePage` üyenin güncelleştirme denetimleri sırasında asla sınanmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="65f7c-107">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="65f7c-108">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="65f7c-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="65f7c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f7c-109">See also</span></span>

- [<span data-ttu-id="65f7c-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="65f7c-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="65f7c-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="65f7c-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
