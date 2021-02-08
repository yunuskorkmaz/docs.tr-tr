---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: parametre alma saklı yordamlarını kullanma'
title: 'Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: eaa2e9c602e2e6baae82648a4237d1098e89896a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785802"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="ca32e-103">Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="ca32e-103">How to: Use Stored Procedures that Take Parameters</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ca32e-104">çıkış parametrelerini başvuru parametrelerine eşler ve değer türleri için parametreyi null yapılabilir olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="ca32e-104">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="ca32e-105">Bir satır kümesi döndüren sorguda giriş parametresinin nasıl kullanılacağına ilişkin bir örnek için bkz. [nasıl yapılır: satır kümelerini döndürme](how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="ca32e-105">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca32e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca32e-106">Example</span></span>  

 <span data-ttu-id="ca32e-107">Aşağıdaki örnek tek bir giriş parametresi (müşteri KIMLIĞI) alır ve bir out parametresi (bu müşterinin toplam satışları) döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca32e-107">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```sql
CREATE PROCEDURE [dbo].[CustOrderTotal]
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="ca32e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca32e-108">Example</span></span>  

 <span data-ttu-id="ca32e-109">Bu saklı yordamı aşağıdaki şekilde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ca32e-109">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ca32e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca32e-110">See also</span></span>

- [<span data-ttu-id="ca32e-111">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="ca32e-111">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="ca32e-112">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="ca32e-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="ca32e-113">Nullable değer türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="ca32e-113">Nullable Value Types (C#)</span></span>](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="ca32e-114">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca32e-114">Nullable Value Types (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
