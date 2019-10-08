---
title: 'Nasıl yapılır: skaler değerli Kullanıcı tanımlı Işlevler kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: dfe82fd50eb3eedeaff9082a4288901f72197795
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003230"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="bd46f-102">Nasıl yapılır: skaler değerli Kullanıcı tanımlı Işlevler kullanma</span><span class="sxs-lookup"><span data-stu-id="bd46f-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="bd46f-103">@No__t-0 özniteliğini kullanarak, bir sınıfta tanımlanan bir istemci yöntemini Kullanıcı tanımlı bir işlev ile eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd46f-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="bd46f-104">Yöntemin gövdesi, yöntem çağrısının amacını yakalayan bir ifade oluşturur ve bu ifadeyi çeviri ve yürütme için <xref:System.Data.Linq.DataContext> ' a geçirir.</span><span class="sxs-lookup"><span data-stu-id="bd46f-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd46f-105">Doğrudan yürütme yalnızca işlev bir sorgu dışında çağrıldığında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bd46f-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="bd46f-106">Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı Işlevleri Iç satır Içinde çağırma](how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="bd46f-106">For more information, see [How to: Call User-Defined Functions Inline](how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd46f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd46f-107">Example</span></span>  
 <span data-ttu-id="bd46f-108">Aşağıdaki SQL kodu, skalar değerli Kullanıcı tanımlı bir işlevi `ReverseCustName()` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bd46f-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="bd46f-109">Bu kod için aşağıdaki gibi bir istemci yöntemi eşleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bd46f-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="bd46f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd46f-110">See also</span></span>

- [<span data-ttu-id="bd46f-111">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="bd46f-111">User-Defined Functions</span></span>](user-defined-functions.md)
