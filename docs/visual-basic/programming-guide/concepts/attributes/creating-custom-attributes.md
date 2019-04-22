---
title: Özel öznitelikler (Visual Basic) oluşturma
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 90e8e9b9a3fa8e0b488f41d035b017d6113213b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814360"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="0c6e3-102">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c6e3-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="0c6e3-103">Bir öznitelik sınıfı doğrudan veya dolaylı olarak türetildiği bir sınıf tanımlayarak kendi özel öznitelikler oluşturabilir <xref:System.Attribute>, hızlı ve kolay meta veri özniteliği tanımlarını tanımlayan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="0c6e3-104">Etiket türlerine türü yazan Programcı adıyla istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="0c6e3-105">Özel bir tanımlayabilir `Author` öznitelik sınıfı:</span><span class="sxs-lookup"><span data-stu-id="0c6e3-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="0c6e3-106">Özniteliğin adı, sınıf adıdır `Author`.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="0c6e3-107">Öğesinden türetilen `System.Attribute`, bir özel öznitelik sınıfı olduğu için.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="0c6e3-108">Özel özniteliğin konumsal parametreler oluşturucunun parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="0c6e3-109">Bu örnekte, `name` konumsal bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="0c6e3-110">Parametreleri, tüm genel okuma-yazma alanlar ve Özellikler adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="0c6e3-111">Bu durumda, `version` tek parametre olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="0c6e3-112">Kullanımına dikkat edin `AttributeUsage` yapmak için özniteliği `Author` özniteliği yalnızca sınıf geçerli ve `Structure` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="0c6e3-113">Bu yeni bir öznitelik şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0c6e3-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="0c6e3-114">`AttributeUsage` adlandırılmış bir parametreye sahip `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="0c6e3-115">Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="0c6e3-116">Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="0c6e3-117">Öznitelik sınıfı bir özellik içeriyorsa, bu özellik salt okunur olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6e3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c6e3-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="0c6e3-119">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0c6e3-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="0c6e3-120">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="0c6e3-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="0c6e3-121">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c6e3-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="0c6e3-122">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c6e3-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="0c6e3-123">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="0c6e3-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="0c6e3-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c6e3-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
