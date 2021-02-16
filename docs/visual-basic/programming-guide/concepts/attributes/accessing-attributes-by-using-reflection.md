---
description: 'Hakkında daha fazla bilgi edinin: yansıma kullanarak özniteliklere erişme (Visual Basic)'
title: Yansıma Kullanarak Özniteliklere Erişme
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e585bb427456f1187eaf8c39937eaa67651d9309
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437871"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="62d94-103">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62d94-103">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="62d94-104">Özel öznitelikleri tanımlayabilir ve bunları kaynak kodunuza yerleştirebilirsiniz. Bu bilgiler, bu bilgileri alma ve üzerinde işlem yapmaya gerek kalmadan çok az değer elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="62d94-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="62d94-105">Yansıma kullanarak özel özniteliklerle tanımlanan bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d94-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="62d94-106">Anahtar yöntemi `GetCustomAttributes` , kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan bir nesne dizisi döndüren ' dir.</span><span class="sxs-lookup"><span data-stu-id="62d94-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="62d94-107">Bu yöntemin birkaç aşırı yüklü sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="62d94-107">This method has several overloaded versions.</span></span> <span data-ttu-id="62d94-108">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="62d94-108">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="62d94-109">Şöyle bir öznitelik belirtimi:</span><span class="sxs-lookup"><span data-stu-id="62d94-109">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="62d94-110">kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="62d94-110">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="62d94-111">Ancak, kod `SampleClass` öznitelikleri için sorgulanana kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="62d94-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="62d94-112">' In çağrılması `GetCustomAttributes` `SampleClass` `Author` , bir nesnenin yukarıya oluşturulmasını ve başlatılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="62d94-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="62d94-113">Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62d94-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="62d94-114">`GetCustomAttributes` sonra `Author` nesneyi ve dizideki diğer öznitelik nesnelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="62d94-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="62d94-115">Daha sonra bu dizinin üzerinde yineleyebilir, her bir dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d94-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="62d94-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="62d94-116">Example</span></span>

<span data-ttu-id="62d94-117">Aşağıda bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62d94-117">Here is a complete example.</span></span> <span data-ttu-id="62d94-118">Özel bir öznitelik tanımlanır, birkaç varlığa uygulanır ve yansıma aracılığıyla alınır.</span><span class="sxs-lookup"><span data-stu-id="62d94-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a><span data-ttu-id="62d94-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62d94-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="62d94-120">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="62d94-120">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="62d94-121">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="62d94-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="62d94-122">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62d94-122">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="62d94-123">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62d94-123">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="62d94-124">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62d94-124">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
