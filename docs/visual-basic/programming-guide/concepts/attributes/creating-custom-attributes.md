---
title: Özel öznitelikler (Visual Basic) oluşturma
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 9af0832e04308bf1942fc955afe5a67161096465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642899"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="46426-102">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="46426-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="46426-103">Doğrudan veya dolaylı olarak türeyen bir sınıf bir öznitelik sınıfı tanımlayarak, kendi özel öznitelikler oluşturabilirsiniz <xref:System.Attribute>, hızlı ve kolay meta verilerde özniteliği tanımlarını tanımlayan hangi yapar.</span><span class="sxs-lookup"><span data-stu-id="46426-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="46426-104">Etiket türleri türü yazan programcı için adıyla istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="46426-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="46426-105">Özel bir tanımlayabilir `Author` öznitelik sınıfı:</span><span class="sxs-lookup"><span data-stu-id="46426-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="46426-106">Sınıf adı özniteliğin adıdır `Author`.</span><span class="sxs-lookup"><span data-stu-id="46426-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="46426-107">Öğesinden türetilen `System.Attribute`özel bir öznitelik sınıfı gelir.</span><span class="sxs-lookup"><span data-stu-id="46426-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="46426-108">Oluşturucusu ait, özel özniteliğin konumsal parametreler parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="46426-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="46426-109">Bu örnekte, `name` konumsal bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="46426-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="46426-110">Herhangi bir genel okuma-yazma alanlar veya özellikler parametreleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="46426-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="46426-111">Bu durumda, `version` tek parametresi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="46426-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="46426-112">Kullanımına dikkat edin `AttributeUsage` yapmak için öznitelik `Author` özniteliği yalnızca sınıfında geçerli ve `Structure` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="46426-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="46426-113">Bu yeni öznitelik aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="46426-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="46426-114">`AttributeUsage` adlandırılmış bir parametre içeriyor `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile.</span><span class="sxs-lookup"><span data-stu-id="46426-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="46426-115">Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="46426-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="46426-116">Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="46426-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="46426-117">Öznitelik sınıfı bir özellik varsa, bu özelliği oku-yaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46426-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46426-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46426-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="46426-119">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46426-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="46426-120">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="46426-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="46426-121">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46426-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="46426-122">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46426-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="46426-123">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="46426-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="46426-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46426-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
