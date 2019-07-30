---
title: 'Nasıl yapılır: Iki nesnenin Ilgili olup olmadığını belirleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626559"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="1f2dd-102">Nasıl yapılır: Iki nesnenin Ilgili olup olmadığını belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f2dd-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="1f2dd-103">İki nesneyi, varsa, varsa aralarındaki ilişkiyi belirleyebilir şekilde karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="1f2dd-104">Sınıfın yöntemi, belirtilen sınıf geçerli sınıftan devralırsa veya geçerli tür belirtilen sınıf tarafından desteklenen bir arabirimse döndürür `True`. <xref:System.Type.IsInstanceOfType%2A> <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1f2dd-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="1f2dd-105">Bir nesnenin başka bir nesnenin sınıfından veya arabiriminden devralıp devrmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="1f2dd-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="1f2dd-106">Düşündüğünüz nesnede, temel türünde olabilir, <xref:System.Object.GetType%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="1f2dd-107"><xref:System.Type.IsInstanceOfType%2A> Tarafından <xref:System.Type?displayProperty=nameWithType> döndürülen<xref:System.Object.GetType%2A>nesnedeki yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="1f2dd-108">İçin <xref:System.Type.IsInstanceOfType%2A>bağımsız değişken listesinde, türetilmiş türden olabileceğini düşündüğünüz nesneyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="1f2dd-109"><xref:System.Type.IsInstanceOfType%2A>bağımsız `True` değişken türü <xref:System.Type?displayProperty=nameWithType> nesne türünden devralırsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="1f2dd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f2dd-110">Example</span></span>
 <span data-ttu-id="1f2dd-111">Aşağıdaki örnek, bir nesnenin başka bir nesnenin sınıfından türetilmiş bir sınıfı temsil edip etmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

<span data-ttu-id="1f2dd-112">Çağrısındaki iki nesne değişkeninin beklenmedik yerleşimini Note <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="1f2dd-113">Beklenen temel tür <xref:System.Type?displayProperty=nameWithType> sınıfı oluşturmak için kullanılır ve beklenen türetilmiş tür <xref:System.Type.IsInstanceOfType%2A> yönteme bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f2dd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f2dd-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="1f2dd-115">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1f2dd-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="1f2dd-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="1f2dd-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="1f2dd-117">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="1f2dd-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="1f2dd-118">Nasıl yapılır: Iki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="1f2dd-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
