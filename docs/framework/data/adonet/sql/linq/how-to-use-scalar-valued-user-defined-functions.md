---
title: 'Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: faf8d6e94c88575f6cb73003fa5bed87650d7d54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196942"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="05b86-102">Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma</span><span class="sxs-lookup"><span data-stu-id="05b86-102">How to: Use Scalar-Valued User-Defined Functions</span></span>

<span data-ttu-id="05b86-103">Özniteliğini kullanarak, bir sınıfta tanımlanan istemci yöntemini Kullanıcı tanımlı bir işlev ile eşleyebilirsiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="05b86-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="05b86-104">Yöntemin gövdesi, yöntem çağrısının amacını yakalayan bir ifade oluşturur ve bu ifadeyi <xref:System.Data.Linq.DataContext> çeviri ve yürütmeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="05b86-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05b86-105">Doğrudan yürütme yalnızca işlev bir sorgu dışında çağrıldığında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="05b86-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="05b86-106">Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı Işlevleri Iç satır Içinde çağırma](how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="05b86-106">For more information, see [How to: Call User-Defined Functions Inline](how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b86-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="05b86-107">Example</span></span>  

 <span data-ttu-id="05b86-108">Aşağıdaki SQL kodu, skaler değerli Kullanıcı tanımlı bir işlev gösterir `ReverseCustName()` .</span><span class="sxs-lookup"><span data-stu-id="05b86-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="05b86-109">Bu kod için aşağıdaki gibi bir istemci yöntemi eşleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05b86-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="05b86-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05b86-110">See also</span></span>

- [<span data-ttu-id="05b86-111">Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="05b86-111">User-Defined Functions</span></span>](user-defined-functions.md)
