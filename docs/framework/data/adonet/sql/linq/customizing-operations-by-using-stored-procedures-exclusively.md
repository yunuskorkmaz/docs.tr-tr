---
title: Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 61230ffc5cd055ee64de9d519cdfb4d76c856ca3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038057"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="6f191-102">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6f191-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="6f191-103">Yalnızca saklı yordamları kullanarak veri erişimi sık karşılaşılan bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="6f191-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f191-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f191-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6f191-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f191-105">Description</span></span>  
 <span data-ttu-id="6f191-106">Sağlanan örnek değiştirebileceğiniz [özelleştirme işlemleri tarafından kullanarak saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) bile (Bu, dinamik SQL yürütülmesine neden olur) ilk sorgu bir saklı yordam sarmalayan bir yöntem çağrısının ile değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="6f191-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="6f191-107">Varsayar `CustomersByCity` aşağıdaki örnekteki gibi bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="6f191-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f191-108">Kod</span><span class="sxs-lookup"><span data-stu-id="6f191-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="6f191-109">Aşağıdaki kodu herhangi bir dinamik SQL çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6f191-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6f191-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f191-110">See also</span></span>

- [<span data-ttu-id="6f191-111">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="6f191-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
