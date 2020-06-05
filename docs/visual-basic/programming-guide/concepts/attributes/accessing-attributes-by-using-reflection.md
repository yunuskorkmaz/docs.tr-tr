---
title: Yansıma Kullanarak Özniteliklere Erişme
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: c0da5c4ae00eb2bc80b10f63f4bfd39763445e55
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400764"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="a3c45-102">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c45-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="a3c45-103">Özel öznitelikleri tanımlayabilir ve bunları kaynak kodunuza yerleştirebilirsiniz. Bu bilgiler, bu bilgileri alma ve üzerinde işlem yapmaya gerek kalmadan çok az değer elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="a3c45-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="a3c45-104">Yansıma kullanarak özel özniteliklerle tanımlanan bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3c45-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="a3c45-105">Anahtar yöntemi `GetCustomAttributes` , kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan bir nesne dizisi döndüren ' dir.</span><span class="sxs-lookup"><span data-stu-id="a3c45-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="a3c45-106">Bu yöntemin birkaç aşırı yüklü sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="a3c45-106">This method has several overloaded versions.</span></span> <span data-ttu-id="a3c45-107">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="a3c45-107">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="a3c45-108">Şöyle bir öznitelik belirtimi:</span><span class="sxs-lookup"><span data-stu-id="a3c45-108">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="a3c45-109">kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="a3c45-109">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="a3c45-110">Ancak, kod `SampleClass` öznitelikleri için sorgulanana kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="a3c45-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="a3c45-111">' In çağrılması `GetCustomAttributes` `SampleClass` `Author` , bir nesnenin yukarıya oluşturulmasını ve başlatılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3c45-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="a3c45-112">Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a3c45-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="a3c45-113">`GetCustomAttributes`sonra `Author` nesneyi ve dizideki diğer öznitelik nesnelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3c45-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="a3c45-114">Daha sonra bu dizinin üzerinde yineleyebilir, her bir dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3c45-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="a3c45-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3c45-115">Example</span></span>

<span data-ttu-id="a3c45-116">Aşağıda bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a3c45-116">Here is a complete example.</span></span> <span data-ttu-id="a3c45-117">Özel bir öznitelik tanımlanır, birkaç varlığa uygulanır ve yansıma aracılığıyla alınır.</span><span class="sxs-lookup"><span data-stu-id="a3c45-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3c45-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3c45-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="a3c45-119">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a3c45-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a3c45-120">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="a3c45-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="a3c45-121">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c45-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="a3c45-122">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c45-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="a3c45-123">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c45-123">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
