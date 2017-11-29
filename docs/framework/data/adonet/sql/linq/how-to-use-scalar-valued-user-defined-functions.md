---
title: "Nasıl yapılır: kullanıcı tanımlı işlevler skaler değerli kullanın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ef9e687522e200487e0fc2a661bbd545d4eb4bbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="a12b8-102">Nasıl yapılır: kullanıcı tanımlı işlevler skaler değerli kullanın</span><span class="sxs-lookup"><span data-stu-id="a12b8-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="a12b8-103">Kullanıcı tanımlı bir işlev için bir sınıf tarafından tanımlanan bir istemci yöntemi eşleyebilirsiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a12b8-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="a12b8-104">Yönteminin gövdesi yöntem çağrısının amacı yakalar ve bu ifadeye aktaran bir ifade oluşturur Not <xref:System.Data.Linq.DataContext> çeviri ve yürütme.</span><span class="sxs-lookup"><span data-stu-id="a12b8-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a12b8-105">Yalnızca bir sorgu dışında işlevi çağrıldıysa doğrudan yürütme oluşur.</span><span class="sxs-lookup"><span data-stu-id="a12b8-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="a12b8-106">Daha fazla bilgi için bkz: [nasıl yapılır: Call User-Defined işlevler satır içi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="a12b8-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a12b8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a12b8-107">Example</span></span>  
 <span data-ttu-id="a12b8-108">Aşağıdaki SQL kod skaler değerli kullanıcı tanımlı bir işlev gösterir `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="a12b8-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="a12b8-109">Bu kodun aşağıdaki gibi bir istemci yöntemi eşleyen:</span><span class="sxs-lookup"><span data-stu-id="a12b8-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a12b8-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a12b8-110">See Also</span></span>  
 [<span data-ttu-id="a12b8-111">Kullanıcı tanımlı işlevler</span><span class="sxs-lookup"><span data-stu-id="a12b8-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
