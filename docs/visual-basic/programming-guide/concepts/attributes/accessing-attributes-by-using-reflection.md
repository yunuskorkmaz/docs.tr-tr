---
title: "(Visual Basic) yansıma kullanarak özniteliklere erişme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4397200b5a2aa5f337dd3479b5405c1a9f245a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="2dca4-102">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="2dca4-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="2dca4-103">Özel öznitelikler tanımlayın ve bunları kaynak kodunda yerleştirmek olgu ve bu bilgileri alma üzerinde çalışan herhangi bir şekilde olmadan az değerinin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2dca4-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="2dca4-104">Yansıma kullanarak özel öznitelikler içeren tanımlandı bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dca4-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="2dca4-105">Anahtar yöntemi `GetCustomAttributes`, kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan nesneler dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2dca4-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="2dca4-106">Bu yöntem, birden fazla aşırı yüklenmiş sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2dca4-106">This method has several overloaded versions.</span></span> <span data-ttu-id="2dca4-107">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="2dca4-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="2dca4-108">Öznitelik belirtimi gibi:</span><span class="sxs-lookup"><span data-stu-id="2dca4-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="2dca4-109">Bunun için kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="2dca4-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="2dca4-110">Bununla birlikte, kod kadar yürütülmez `SampleClass` öznitelikler için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="2dca4-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="2dca4-111">Çağırma `GetCustomAttributes` üzerinde `SampleClass` neden olan bir `Author` nesnesi oluşturulur ve yukarıdaki olarak başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2dca4-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="2dca4-112">Sınıfın diğer öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2dca4-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="2dca4-113">`GetCustomAttributes`ardından döndürür `Author` nesne ve bir dizi diğer öznitelik nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2dca4-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="2dca4-114">Bu dizi yineleme öznitelikleri her dizi öğesi türüne bağlı olarak uygulanan belirlemek ve öznitelik nesnelerden bilgi ayıklamak.</span><span class="sxs-lookup"><span data-stu-id="2dca4-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dca4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dca4-115">Example</span></span>  
 <span data-ttu-id="2dca4-116">Burada, tam bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2dca4-116">Here is a complete example.</span></span> <span data-ttu-id="2dca4-117">Özel bir öznitelik tanımlı, birkaç varlıklara uygulanan ve yansıma alınır.</span><span class="sxs-lookup"><span data-stu-id="2dca4-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2dca4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dca4-118">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="2dca4-119">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2dca4-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="2dca4-120">Özniteliklerde depolanan bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="2dca4-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="2dca4-121">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dca4-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="2dca4-122">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dca4-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="2dca4-123">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="2dca4-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
