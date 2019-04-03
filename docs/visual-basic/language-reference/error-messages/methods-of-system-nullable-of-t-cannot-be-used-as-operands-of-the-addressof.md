---
title: "'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 54d66a60d20a6add4c2b4a160f87b58b5a1d00e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817272"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="7a43a-102">'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="7a43a-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>
<span data-ttu-id="7a43a-103">Bir ifade kullanıyor `AddressOf` işleci, bir yordamı temsil eden bir işlenen <xref:System.Nullable%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="7a43a-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="7a43a-104">**Hata Kimliği:** BC32126</span><span class="sxs-lookup"><span data-stu-id="7a43a-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a43a-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7a43a-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7a43a-106">Yordam adı yerine `AddressOf` yan tümcesi bir üyesi değil bir işlenen <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="7a43a-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="7a43a-107">Yazma yöntemi saran bir sınıf <xref:System.Nullable%601> kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="7a43a-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="7a43a-108">Aşağıdaki örnekte, `NullableWrapper` sınıf adlı yeni bir yöntem tanımlar `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="7a43a-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="7a43a-109">Bu yeni yöntemi üyesi olmadığından <xref:System.Nullable%601>, için uygulanabilir `nullInstance`, bir bağımsız değişken oluşturmak için boş değer atanabilir bir tür örneği `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="7a43a-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a43a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a43a-110">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="7a43a-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="7a43a-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="7a43a-112">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="7a43a-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="7a43a-113">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="7a43a-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
