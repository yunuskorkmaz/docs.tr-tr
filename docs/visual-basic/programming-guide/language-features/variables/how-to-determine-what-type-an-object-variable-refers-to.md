---
title: 'Nasıl yapılır: Bir nesne değişkeninin (Visual Basic) hangi türe başvurduğunu belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: dc6f54719d4f30be00b7b85f0ab18c4cb02b0d7c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816414"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="53f5a-102">Nasıl yapılır: Bir nesne değişkeninin (Visual Basic) hangi türe başvurduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="53f5a-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="53f5a-103">Bir nesne değişkeni başka bir yere depolanmış veriler için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="53f5a-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="53f5a-104">Çalışma zamanı sırasında bu veri türünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53f5a-104">The type of that data can change during run time.</span></span> <span data-ttu-id="53f5a-105">Herhangi bir anda kullanabileceğiniz <xref:System.Type.GetTypeCode%2A> geçerli çalışma zamanı türü belirlemek için yöntemi veya [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) geçerli olmadığını anlamak için çalışma zamanı türü belirtilen bir tür ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="53f5a-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="53f5a-106">Tam bir nesne değişkeni şu anda türünü belirlemek için başvuruyor</span><span class="sxs-lookup"><span data-stu-id="53f5a-106">To determine the exact type an object variable currently refers to</span></span>  
  
1.  <span data-ttu-id="53f5a-107">Nesne değişkeni üzerinde çağrı <xref:System.Object.GetType%2A> almak için yöntemi bir <xref:System.Type?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="53f5a-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <span data-ttu-id="53f5a-108">Üzerinde <xref:System.Type?displayProperty=nameWithType> sınıfı, paylaşılan yöntemi çağırın <xref:System.Type.GetTypeCode%2A> alınacak <xref:System.TypeCode> nesnenin türü için değer sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="53f5a-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="53f5a-109">Test edebilirsiniz <xref:System.TypeCode> hangi numaralandırma üyelerini, gibi ilgilendiğiniz karşı numaralandırma değeri `Double`.</span><span class="sxs-lookup"><span data-stu-id="53f5a-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="53f5a-110">Bir nesne olup olmadığını belirlemek için değişkenin türü ile belirtilen bir türün uyumlu</span><span class="sxs-lookup"><span data-stu-id="53f5a-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="53f5a-111">Kullanım `TypeOf` işleci ile birlikte [işleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) nesnesi ile test etmek için bir `TypeOf`... `Is` ifade.</span><span class="sxs-lookup"><span data-stu-id="53f5a-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="53f5a-112">`TypeOf`... `Is` ifade döndürür `True` çalışma zamanı nesne türü belirtilen tür ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="53f5a-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="53f5a-113">Uyumluluk için ölçüt, belirtilen türün bir sınıf, yapı veya arabirim olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="53f5a-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="53f5a-114">Genel olarak, nesneyi aynı türde ise, devralan veya belirtilen türün uyguladığı türleri uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="53f5a-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="53f5a-115">Daha fazla bilgi için [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="53f5a-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53f5a-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="53f5a-116">Compiling the Code</span></span>  
 <span data-ttu-id="53f5a-117">Belirtilen türde bir değişkenin veya ifadenin olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="53f5a-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="53f5a-118">Bu sınıf, yapı veya arabirim gibi tanımlanan bir tür adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53f5a-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="53f5a-119">Bu gibi iç türleri içerir `Integer` ve `String`.</span><span class="sxs-lookup"><span data-stu-id="53f5a-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f5a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53f5a-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="53f5a-121">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="53f5a-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="53f5a-122">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="53f5a-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="53f5a-123">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="53f5a-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
