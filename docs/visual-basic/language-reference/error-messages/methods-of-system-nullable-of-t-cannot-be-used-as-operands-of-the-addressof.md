---
title: Yöntemlerinin &#39;System.Nullable (Of T)&#39; işlenenleri olarak kullanılamaz &#39;AddressOf&#39; işleci
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 3a3e4fc033f47fb6a72076dff79f1eece8d01a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594126"
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a><span data-ttu-id="18ec4-102">Yöntemlerinin &#39;System.Nullable (Of T)&#39; işlenenleri olarak kullanılamaz &#39;AddressOf&#39; işleci</span><span class="sxs-lookup"><span data-stu-id="18ec4-102">Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator</span></span>
<span data-ttu-id="18ec4-103">Bir ifade kullanıyor `AddressOf` , bir yordamı temsil eden işleneni işleciyle <xref:System.Nullable%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="18ec4-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="18ec4-104">**Hata Kimliği:** BC32126</span><span class="sxs-lookup"><span data-stu-id="18ec4-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18ec4-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="18ec4-105">To correct this error</span></span>  
  
-   <span data-ttu-id="18ec4-106">Yordam adıyla değiştirin `AddressOf` yan tümcesiyle birlikte bir üyesi olmayan işleneni <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="18ec4-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="18ec4-107">Yöntemi saran bir sınıf yazma <xref:System.Nullable%601> kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="18ec4-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="18ec4-108">Aşağıdaki örnekte, `NullableWrapper` sınıfı tanımlayan adlı yeni bir yöntem `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="18ec4-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="18ec4-109">Bu yeni yöntemin bir üyesi olmadığından <xref:System.Nullable%601>, için uygulanabilir `nullInstance`, için bağımsız değişken oluşturmak için boş değer atanabilir bir tür örneği `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="18ec4-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="18ec4-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18ec4-110">See Also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="18ec4-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="18ec4-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="18ec4-112">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="18ec4-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="18ec4-113">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="18ec4-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
