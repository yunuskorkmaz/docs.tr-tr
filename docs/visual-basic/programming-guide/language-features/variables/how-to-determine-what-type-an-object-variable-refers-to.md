---
title: "Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5dd6785ecd48be3f0455de63b9e3f13a485ddbb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="3cf87-102">Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cf87-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="3cf87-103">Bir nesne değişkeni başka bir yerde depolanan veriler için bir işaretçi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3cf87-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="3cf87-104">Bu veri türü, çalışma zamanı sırasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cf87-104">The type of that data can change during run time.</span></span> <span data-ttu-id="3cf87-105">Herhangi bir anda kullandığınız <xref:System.Type.GetTypeCode%2A> geçerli çalışma zamanı tür belirlemek için yöntemi veya [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) geçerli olmadığını öğrenmek için çalışma zamanı türü belirtilen türle uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="3cf87-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="3cf87-106">Tam bir nesne değişkeni şu anda türünü belirlemek için başvurur</span><span class="sxs-lookup"><span data-stu-id="3cf87-106">To determine the exact type an object variable currently refers to</span></span>  
  
1.  <span data-ttu-id="3cf87-107">Nesne değişkeni üzerinde çağrısı <xref:System.Object.GetType%2A> alma yöntemi bir <xref:System.Type?displayProperty=nameWithType> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3cf87-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <span data-ttu-id="3cf87-108">Üzerinde <xref:System.Type?displayProperty=nameWithType> sınıfı, paylaştırılmış yöntem çağrısı <xref:System.Type.GetTypeCode%2A> almak için <xref:System.TypeCode> numaralandırma değeri nesnenin türü.</span><span class="sxs-lookup"><span data-stu-id="3cf87-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="3cf87-109">Test edebilirsiniz <xref:System.TypeCode> hangi numaralandırma üyeleri, gibi ilgilendiğiniz karşı numaralandırma değeri `Double`.</span><span class="sxs-lookup"><span data-stu-id="3cf87-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="3cf87-110">Bir nesne olup olmadığını belirlemek için değişkenin türü belirtilen türle uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="3cf87-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="3cf87-111">Kullanım `TypeOf` birlikte işleci [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) nesnesi ile test etmek için bir `TypeOf`... `Is` ifade.</span><span class="sxs-lookup"><span data-stu-id="3cf87-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="3cf87-112">`TypeOf`... `Is` ifadesi döndürür `True` çalışma zamanında nesne türü belirtilen tür ile uyumlu ise.</span><span class="sxs-lookup"><span data-stu-id="3cf87-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="3cf87-113">Uyumluluk için ölçüt belirtilen türün bir sınıf, yapı veya arabirimi olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3cf87-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="3cf87-114">Genel olarak, nesne aynı türde ise, devraldığı veya belirtilen türe uygulayan türler uyumludur.</span><span class="sxs-lookup"><span data-stu-id="3cf87-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="3cf87-115">Daha fazla bilgi için bkz: [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3cf87-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cf87-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3cf87-116">Compiling the Code</span></span>  
 <span data-ttu-id="3cf87-117">Belirtilen türde bir değişken veya ifadeyi olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3cf87-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="3cf87-118">Bu sınıf, yapı veya arabirim gibi tanımlanmış bir türü adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3cf87-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="3cf87-119">Bu gibi iç türleri içerir `Integer` ve `String`.</span><span class="sxs-lookup"><span data-stu-id="3cf87-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf87-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3cf87-120">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [<span data-ttu-id="3cf87-121">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="3cf87-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="3cf87-122">Nesne değişkeni değerleri</span><span class="sxs-lookup"><span data-stu-id="3cf87-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="3cf87-123">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="3cf87-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
