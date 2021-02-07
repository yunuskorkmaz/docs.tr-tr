---
description: 'Hakkında daha fazla bilgi edinin: yalnızca saklı yordamları kullanarak Işlemleri özelleştirme'
title: Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 4ddcc6b4face1abccb502e12617105a734bb5f0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729555"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="5a5ca-103">Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5a5ca-103">Customizing Operations by Using Stored Procedures Exclusively</span></span>

<span data-ttu-id="5a5ca-104">Yalnızca saklı yordamlar kullanılarak verilere erişim, yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="5a5ca-104">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5ca-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a5ca-105">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5a5ca-106">Description</span><span class="sxs-lookup"><span data-stu-id="5a5ca-106">Description</span></span>  

 <span data-ttu-id="5a5ca-107">Saklı yordamları kullanarak, bir saklı yordamı sarmalayan ilk sorgu (dinamik SQL yürütmeye neden olur) bir yöntem çağrısıyla değiştirerek, [Işlemleri özelleştirme](customizing-operations-by-using-stored-procedures.md) bölümünde belirtilen örneği değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a5ca-107">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="5a5ca-108">`CustomersByCity`Aşağıdaki örnekte olduğu gibi yönteminin yöntemi olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="5a5ca-108">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5a5ca-109">Kod</span><span class="sxs-lookup"><span data-stu-id="5a5ca-109">Code</span></span>  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="5a5ca-110">Aşağıdaki kod herhangi bir dinamik SQL olmadan yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5a5ca-110">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5a5ca-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a5ca-111">See also</span></span>

- [<span data-ttu-id="5a5ca-112">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="5a5ca-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
