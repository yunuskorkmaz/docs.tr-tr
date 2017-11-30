---
title: "Özel öznitelikler (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a24553ae4cc2186e805d76ddb37f38c0322aeac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="59c75-102">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="59c75-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="59c75-103">Doğrudan veya dolaylı olarak türeyen bir sınıf bir öznitelik sınıfı tanımlayarak, kendi özel öznitelikler oluşturabilirsiniz <xref:System.Attribute>, hızlı ve kolay meta verilerde özniteliği tanımlarını tanımlayan hangi yapar.</span><span class="sxs-lookup"><span data-stu-id="59c75-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="59c75-104">Etiket türleri türü yazan programcı için adıyla istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="59c75-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="59c75-105">Özel bir tanımlayabilir `Author` öznitelik sınıfı:</span><span class="sxs-lookup"><span data-stu-id="59c75-105">You might define a custom `Author` attribute class:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="59c75-106">Sınıf adı özniteliğin adıdır `Author`.</span><span class="sxs-lookup"><span data-stu-id="59c75-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="59c75-107">Öğesinden türetilen `System.Attribute`özel bir öznitelik sınıfı gelir.</span><span class="sxs-lookup"><span data-stu-id="59c75-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="59c75-108">Oluşturucusu ait, özel özniteliğin konumsal parametreler parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="59c75-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="59c75-109">Bu örnekte, `name` konumsal bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="59c75-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="59c75-110">Herhangi bir genel okuma-yazma alanlar veya özellikler parametreleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="59c75-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="59c75-111">Bu durumda, `version` tek parametresi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="59c75-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="59c75-112">Kullanımına dikkat edin `AttributeUsage` yapmak için öznitelik `Author` özniteliği yalnızca sınıfında geçerli ve `Structure` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="59c75-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="59c75-113">Bu yeni öznitelik aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59c75-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="59c75-114">`AttributeUsage`adlandırılmış bir parametre içeriyor `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile.</span><span class="sxs-lookup"><span data-stu-id="59c75-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="59c75-115">Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59c75-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="59c75-116">Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="59c75-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="59c75-117">Öznitelik sınıfı bir özellik varsa, bu özelliği oku-yaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59c75-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c75-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59c75-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="59c75-119">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="59c75-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="59c75-120">Özel öznitelikler yazma</span><span class="sxs-lookup"><span data-stu-id="59c75-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="59c75-121">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c75-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="59c75-122">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c75-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="59c75-123">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="59c75-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="59c75-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c75-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
