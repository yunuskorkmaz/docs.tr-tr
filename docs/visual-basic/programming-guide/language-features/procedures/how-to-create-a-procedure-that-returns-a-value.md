---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 3d28162d2a2103477a20b08fc03c937de8b5a475
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071878"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="c2cfd-102">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2cfd-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="c2cfd-103">`Function`Çağırma koduna bir değer döndürmek için bir yordam kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="c2cfd-104">Bir değer döndüren bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c2cfd-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="c2cfd-105">Diğer herhangi bir yordamın dışında, bir ifadesini ve `Function` ardından bir `End Function` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="c2cfd-106">İfadesinde, `Function` `Function` yordamın adı ile anahtar sözcüğünü ve ardından parantez içindeki parametre listesini izleyin.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="c2cfd-107">`As`Döndürülen değerin veri türünü belirtmek için bir yan tümcesiyle ayraçları izleyin.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="c2cfd-108">Yordamın kod deyimlerini `Function` ve deyimlerini arasına yerleştirin `End Function` .</span><span class="sxs-lookup"><span data-stu-id="c2cfd-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="c2cfd-109">`Return`Çağırma koduna değeri döndürmek için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="c2cfd-110">Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="c2cfd-111">Aşağıdaki örnekte, için tipik bir çağrı gösterilmektedir `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="c2cfd-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c2cfd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2cfd-112">See also</span></span>

- [<span data-ttu-id="c2cfd-113">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c2cfd-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c2cfd-114">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c2cfd-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="c2cfd-115">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="c2cfd-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="c2cfd-116">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="c2cfd-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c2cfd-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c2cfd-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c2cfd-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c2cfd-118">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="c2cfd-119">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="c2cfd-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="c2cfd-120">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="c2cfd-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
