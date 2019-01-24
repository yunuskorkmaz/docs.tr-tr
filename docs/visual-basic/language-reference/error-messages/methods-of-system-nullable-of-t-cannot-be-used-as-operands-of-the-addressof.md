---
title: Yöntemlerinin &#39;System.Nullable (Of T)&#39; işleneni kullanılamaz &#39;AddressOf&#39; işleci
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: c3e34e79f2e91bb55bb2e053ae3e59fd42c4250c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655328"
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a><span data-ttu-id="ffabb-102">Yöntemlerinin &#39;System.Nullable (Of T)&#39; işleneni kullanılamaz &#39;AddressOf&#39; işleci</span><span class="sxs-lookup"><span data-stu-id="ffabb-102">Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator</span></span>
<span data-ttu-id="ffabb-103">Bir ifade kullanıyor `AddressOf` işleci, bir yordamı temsil eden bir işlenen <xref:System.Nullable%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="ffabb-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="ffabb-104">**Hata Kimliği:** BC32126</span><span class="sxs-lookup"><span data-stu-id="ffabb-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ffabb-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ffabb-105">To correct this error</span></span>  
  
-   <span data-ttu-id="ffabb-106">Yordam adı yerine `AddressOf` yan tümcesi bir üyesi değil bir işlenen <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="ffabb-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="ffabb-107">Yazma yöntemi saran bir sınıf <xref:System.Nullable%601> kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="ffabb-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="ffabb-108">Aşağıdaki örnekte, `NullableWrapper` sınıf adlı yeni bir yöntem tanımlar `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="ffabb-109">Bu yeni yöntemi üyesi olmadığından <xref:System.Nullable%601>, için uygulanabilir `nullInstance`, bir bağımsız değişken oluşturmak için boş değer atanabilir bir tür örneği `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="ffabb-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ffabb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffabb-110">See also</span></span>
- <xref:System.Nullable%601>
- [<span data-ttu-id="ffabb-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="ffabb-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="ffabb-112">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="ffabb-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="ffabb-113">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="ffabb-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
