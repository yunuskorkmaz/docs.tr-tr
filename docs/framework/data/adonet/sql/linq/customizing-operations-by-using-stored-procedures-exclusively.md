---
title: Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: a242ecdc774d67721aee640e75847317c1b815d6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247542"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="f039a-102">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f039a-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="f039a-103">Yalnızca saklı yordamlar kullanılarak verilere erişim, yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="f039a-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f039a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f039a-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f039a-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f039a-105">Description</span></span>  
 <span data-ttu-id="f039a-106">Saklı yordamları kullanarak, bir saklı yordamı sarmalayan ilk sorgu (dinamik SQL yürütmeye neden olur) bir yöntem çağrısıyla değiştirerek, [Işlemleri özelleştirme](customizing-operations-by-using-stored-procedures.md) bölümünde belirtilen örneği değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f039a-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="f039a-107">Aşağıdaki `CustomersByCity` örnekte olduğu gibi yönteminin yöntemi olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="f039a-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f039a-108">Kod</span><span class="sxs-lookup"><span data-stu-id="f039a-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="f039a-109">Aşağıdaki kod herhangi bir dinamik SQL olmadan yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f039a-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f039a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f039a-110">See also</span></span>

- [<span data-ttu-id="f039a-111">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="f039a-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
