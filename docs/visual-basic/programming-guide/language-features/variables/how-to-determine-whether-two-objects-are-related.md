---
title: 'Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: b33815d58b0ef40f7f75a6a41bb4b1eeef591859
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072229"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="ed5d7-102">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed5d7-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="ed5d7-103">İki nesneyi, varsa, varsa aralarındaki ilişkiyi belirleyebilir şekilde karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="ed5d7-104"><xref:System.Type.IsInstanceOfType%2A>Sınıfın yöntemi, <xref:System.Type?displayProperty=nameWithType> `True` belirtilen sınıf geçerli sınıftan devralırsa veya geçerli tür belirtilen sınıf tarafından desteklenen bir arabirimse döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="ed5d7-105">Bir nesnenin başka bir nesnenin sınıfından veya arabiriminden devralıp devrmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="ed5d7-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="ed5d7-106">Düşündüğünüz nesnede, temel türünde olabilir, <xref:System.Object.GetType%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="ed5d7-107"><xref:System.Type?displayProperty=nameWithType>Tarafından döndürülen nesnedeki <xref:System.Object.GetType%2A> <xref:System.Type.IsInstanceOfType%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="ed5d7-108">İçin bağımsız değişken listesinde <xref:System.Type.IsInstanceOfType%2A> , türetilmiş türden olabileceğini düşündüğünüz nesneyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="ed5d7-109"><xref:System.Type.IsInstanceOfType%2A>`True`bağımsız değişken türü nesne türünden devralırsa döndürür <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ed5d7-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="ed5d7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed5d7-110">Example</span></span>

 <span data-ttu-id="ed5d7-111">Aşağıdaki örnek, bir nesnenin başka bir nesnenin sınıfından türetilmiş bir sınıfı temsil edip etmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

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

<span data-ttu-id="ed5d7-112">Çağrısındaki iki nesne değişkeninin beklenmedik yerleşimini Note <xref:System.Type.IsInstanceOfType%2A> .</span><span class="sxs-lookup"><span data-stu-id="ed5d7-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="ed5d7-113">Beklenen temel tür sınıfı oluşturmak için kullanılır <xref:System.Type?displayProperty=nameWithType> ve beklenen türetilmiş tür yönteme bir bağımsız değişken olarak geçirilir <xref:System.Type.IsInstanceOfType%2A> .</span><span class="sxs-lookup"><span data-stu-id="ed5d7-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed5d7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="ed5d7-115">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ed5d7-115">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ed5d7-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ed5d7-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="ed5d7-117">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="ed5d7-117">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="ed5d7-118">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="ed5d7-118">How to: Determine Whether Two Objects Are Identical</span></span>](how-to-determine-whether-two-objects-are-identical.md)
