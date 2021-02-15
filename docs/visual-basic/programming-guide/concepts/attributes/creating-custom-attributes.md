---
description: 'Hakkında daha fazla bilgi edinin: özel öznitelikler oluşturma (Visual Basic)'
title: Özel Öznitelikler Oluşturma
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: e989a4ce219609aafcec90d12f9d460681e98be9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437780"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="34ec1-103">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ec1-103">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="34ec1-104">Doğrudan veya dolaylı olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz <xref:System.Attribute> . Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="34ec1-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="34ec1-105">Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="34ec1-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="34ec1-106">Özel bir `Author` öznitelik sınıfı tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34ec1-106">You might define a custom `Author` attribute class:</span></span>

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

<span data-ttu-id="34ec1-107">Sınıf adı özniteliğin adıdır, `Author` .</span><span class="sxs-lookup"><span data-stu-id="34ec1-107">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="34ec1-108">Öğesinden türetilir `System.Attribute` , bu nedenle özel bir öznitelik sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="34ec1-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="34ec1-109">Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="34ec1-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="34ec1-110">Bu örnekte, `name` bir Konumsal parametredir.</span><span class="sxs-lookup"><span data-stu-id="34ec1-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="34ec1-111">Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="34ec1-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="34ec1-112">Bu durumda, `version` tek adlandırılmış parametredir.</span><span class="sxs-lookup"><span data-stu-id="34ec1-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="34ec1-113">Özniteliği `AttributeUsage` `Author` yalnızca sınıf ve bildirimlerde geçerli hale getirmek için özniteliğinin kullanımını unutmayın `Structure` .</span><span class="sxs-lookup"><span data-stu-id="34ec1-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="34ec1-114">Bu yeni özniteliği şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34ec1-114">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="34ec1-115">`AttributeUsage` , `AllowMultiple` özel bir özniteliği tek kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="34ec1-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="34ec1-116">Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="34ec1-116">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="34ec1-117">Aşağıdaki kod örneğinde, aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="34ec1-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="34ec1-118">Öznitelik sınıfınız bir özellik içeriyorsa, bu özellik oku-yaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34ec1-118">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="34ec1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34ec1-119">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="34ec1-120">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="34ec1-120">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="34ec1-121">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="34ec1-121">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="34ec1-122">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ec1-122">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="34ec1-123">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ec1-123">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="34ec1-124">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ec1-124">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="34ec1-125">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ec1-125">AttributeUsage (Visual Basic)</span></span>](attributeusage.md)
