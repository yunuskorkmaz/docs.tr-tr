---
title: 'Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 05ecc467f75fbeda785b4bac1c3b8b1ceeb173b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174335"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="9d25e-102">Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="9d25e-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9d25e-103">çıkış parametrelerini başvuru parametrelerine eşler ve değer türleri için parametreyi nullable olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d25e-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="9d25e-104">Bir satır kümesini döndüren bir sorguda giriş parametresinin nasıl kullanılacağına dair bir örnek için [bkz.](how-to-return-rowsets.md)</span><span class="sxs-lookup"><span data-stu-id="9d25e-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d25e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d25e-105">Example</span></span>  
 <span data-ttu-id="9d25e-106">Aşağıdaki örnek, tek bir giriş parametresi (müşteri kimliği) alır ve bir çıkış parametresi (bu müşterinin toplam satışları) döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d25e-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="9d25e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d25e-107">Example</span></span>  
 <span data-ttu-id="9d25e-108">Bu depolanan yordamı aşağıdaki gibi çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="9d25e-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9d25e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d25e-109">See also</span></span>

- [<span data-ttu-id="9d25e-110">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9d25e-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="9d25e-111">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="9d25e-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="9d25e-112">Nullable Değer Türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="9d25e-112">Nullable Value Types (C#)</span></span>](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="9d25e-113">Boş Değer Atanabilen Değer Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d25e-113">Nullable Value Types (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
