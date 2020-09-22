---
title: "'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 421766918c03c2378bbf906f85c5855f44ffbdea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873741"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="c04e3-102">'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="c04e3-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>

<span data-ttu-id="c04e3-103">Bir ifade, `AddressOf` Yapı yordamını temsil eden bir işlenen ile işlecini kullanır <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="c04e3-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="c04e3-104">**Hata kimliği:** BC32126</span><span class="sxs-lookup"><span data-stu-id="c04e3-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c04e3-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c04e3-105">To correct this error</span></span>  
  
- <span data-ttu-id="c04e3-106">Yan tümcesindeki yordam adını, `AddressOf` üyesi olmayan bir işlenen ile değiştirin <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="c04e3-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
- <span data-ttu-id="c04e3-107">Kullanmak istediğiniz yöntemini sarmalayan bir sınıf yazın <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="c04e3-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="c04e3-108">Aşağıdaki örnekte, `NullableWrapper` sınıfı adlı yeni bir yöntemi tanımlar `GetValueOrDefault` .</span><span class="sxs-lookup"><span data-stu-id="c04e3-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="c04e3-109">Bu yeni yöntem bir üyesi olmadığından, <xref:System.Nullable%601> `nullInstance` için bir bağımsız değişken oluşturmak üzere null yapılabilir bir türün örneği olan öğesine uygulanabilir `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="c04e3-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c04e3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04e3-110">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="c04e3-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="c04e3-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="c04e3-112">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="c04e3-112">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c04e3-113">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="c04e3-113">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
