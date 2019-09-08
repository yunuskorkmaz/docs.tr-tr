---
title: 'Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793068"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="63324-102">Nasıl yapılır: Parametre Alan Saklı Yordamlar Kullanma</span><span class="sxs-lookup"><span data-stu-id="63324-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="63324-103">çıkış parametrelerini başvuru parametrelerine eşler ve değer türleri için parametreyi null yapılabilir olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="63324-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="63324-104">Bir satır kümesi döndüren sorguda giriş parametresinin nasıl kullanılacağına ilişkin bir örnek için bkz [. nasıl yapılır: Satır kümelerini](how-to-return-rowsets.md)döndürün.</span><span class="sxs-lookup"><span data-stu-id="63324-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63324-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="63324-105">Example</span></span>  
 <span data-ttu-id="63324-106">Aşağıdaki örnek tek bir giriş parametresi (müşteri KIMLIĞI) alır ve bir out parametresi (bu müşterinin toplam satışları) döndürür.</span><span class="sxs-lookup"><span data-stu-id="63324-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="63324-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="63324-107">Example</span></span>  
 <span data-ttu-id="63324-108">Bu saklı yordamı aşağıdaki şekilde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63324-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="63324-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63324-109">See also</span></span>

- [<span data-ttu-id="63324-110">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="63324-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="63324-111">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="63324-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="63324-112">Boş Değer Atanabilir Tipleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="63324-112">Using Nullable Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="63324-113">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="63324-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
