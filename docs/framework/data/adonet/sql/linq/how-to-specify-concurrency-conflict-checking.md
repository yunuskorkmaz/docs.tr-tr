---
title: 'Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 7adacdccd12c6493ff7c62c0e6a44058a9719d7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197215"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="7fcaf-102">Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme</span><span class="sxs-lookup"><span data-stu-id="7fcaf-102">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="7fcaf-103">Çağırdığınızda, hangi veritabanının sütunlarının eşzamanlılık çakışmaları için denetleneceğini belirtebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="7fcaf-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="7fcaf-104">Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirtme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="7fcaf-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fcaf-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fcaf-105">Example</span></span>  

 <span data-ttu-id="7fcaf-106">Aşağıdaki kod, `HomePage` üyenin güncelleştirme denetimleri sırasında asla sınanmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fcaf-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="7fcaf-107">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="7fcaf-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7fcaf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fcaf-108">See also</span></span>

- [<span data-ttu-id="7fcaf-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="7fcaf-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7fcaf-110">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7fcaf-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
