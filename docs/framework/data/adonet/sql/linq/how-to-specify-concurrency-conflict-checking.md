---
title: 'Nasıl yapılır: Eşzamanlılık çakışması denetimini belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 033a547b25e7280eb39be2698963391543437083
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573731"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="1fdb7-102">Nasıl yapılır: Eşzamanlılık çakışması denetimini belirtme</span><span class="sxs-lookup"><span data-stu-id="1fdb7-102">How to: Specify Concurrency-Conflict Checking</span></span>
<span data-ttu-id="1fdb7-103">Hangi sütunların veritabanının çağırdığınızda eşzamanlılık çakışmaları için denetlenecek olan belirtebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fdb7-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="1fdb7-104">Daha fazla bilgi için [nasıl yapılır: Hangi üyelerin eşzamanlılık çakışmaları için test edildiğini belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="1fdb7-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fdb7-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1fdb7-105">Example</span></span>  
 <span data-ttu-id="1fdb7-106">Aşağıdaki kod belirten `HomePage` üye hiçbir zaman test edilemez güncelleştirme denetimler sırasında.</span><span class="sxs-lookup"><span data-stu-id="1fdb7-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="1fdb7-107">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fdb7-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1fdb7-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fdb7-108">See also</span></span>
- [<span data-ttu-id="1fdb7-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="1fdb7-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="1fdb7-110">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1fdb7-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
