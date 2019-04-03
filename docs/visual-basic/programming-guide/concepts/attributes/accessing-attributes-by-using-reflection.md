---
title: (Visual Basic) yansıma kullanarak özniteliklere erişme
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e5cbce8529cc7554a8edacb2d83dabb73a495eec
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827659"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="cdb67-102">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="cdb67-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="cdb67-103">Özel öznitelikler tanımlamak ve bunları kaynak kodunuzu getirin olgu üzerinde çalışan ve bu bilgileri alınırken bir şekilde olmadan küçük değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="cdb67-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="cdb67-104">Yansıma kullanarak özel öznitelik tanımlandı bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdb67-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="cdb67-105">Anahtar yöntemi `GetCustomAttributes`, kaynak kod özniteliklerini çalışma zamanı eşdeğerleri olan nesneler dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="cdb67-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="cdb67-106">Bu yöntem, birden fazla aşırı yüklenmiş sürümleri vardır.</span><span class="sxs-lookup"><span data-stu-id="cdb67-106">This method has several overloaded versions.</span></span> <span data-ttu-id="cdb67-107">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="cdb67-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="cdb67-108">Bir öznitelik belirtimi gibi:</span><span class="sxs-lookup"><span data-stu-id="cdb67-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="cdb67-109">Bunun için kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="cdb67-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="cdb67-110">Ancak, kod kadar yürütülmez `SampleClass` öznitelikleri için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="cdb67-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="cdb67-111">Çağırma `GetCustomAttributes` üzerinde `SampleClass` neden olan bir `Author` nesne oluşturulur ve yukarıdaki gibi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="cdb67-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="cdb67-112">Sınıfın diğer öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cdb67-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="cdb67-113">`GetCustomAttributes` ardından döndürür `Author` ve diğer öznitelik nesneleri bir dizideki nesne.</span><span class="sxs-lookup"><span data-stu-id="cdb67-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="cdb67-114">Bu dizi yineleme hangi özniteliklerin her dizi öğesi türüne bağlı olarak uygulanan belirlemek ve öznitelik nesnelerden bilgiler ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="cdb67-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb67-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="cdb67-115">Example</span></span>  
 <span data-ttu-id="cdb67-116">Tam bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cdb67-116">Here is a complete example.</span></span> <span data-ttu-id="cdb67-117">Özel bir öznitelik tanımlı, birden fazla varlıklarına uygulanan ve yansıma alınır.</span><span class="sxs-lookup"><span data-stu-id="cdb67-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cdb67-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdb67-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="cdb67-119">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cdb67-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="cdb67-120">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="cdb67-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="cdb67-121">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdb67-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="cdb67-122">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdb67-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="cdb67-123">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="cdb67-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
