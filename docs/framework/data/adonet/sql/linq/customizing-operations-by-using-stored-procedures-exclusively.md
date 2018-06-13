---
title: İşlemleri kullanarak özelleştirme saklı özel yordamları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 3c60a9e430b4228117fd03a43a30f27342154b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357520"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="add7b-102">İşlemleri kullanarak özelleştirme saklı özel yordamları</span><span class="sxs-lookup"><span data-stu-id="add7b-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="add7b-103">Yalnızca depolanmış yordamları kullanarak verilere erişim ortak bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="add7b-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="add7b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="add7b-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="add7b-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="add7b-105">Description</span></span>  
 <span data-ttu-id="add7b-106">Sağlanan örnek değiştirebileceğiniz [özelleştirme işlemleri tarafından kullanarak saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) bile (hangi dinamik SQL yürütmesi neden olan) ilk sorgu bir saklı yordam sarmalar bir yöntem çağrısı ile değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="add7b-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="add7b-107">Varsayın `CustomersByCity` , aşağıdaki örnekte olduğu gibi bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="add7b-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="add7b-108">Kod</span><span class="sxs-lookup"><span data-stu-id="add7b-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="add7b-109">Aşağıdaki kod, tüm dinamik SQL yürütür.</span><span class="sxs-lookup"><span data-stu-id="add7b-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="add7b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="add7b-110">See Also</span></span>  
 [<span data-ttu-id="add7b-111">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="add7b-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
