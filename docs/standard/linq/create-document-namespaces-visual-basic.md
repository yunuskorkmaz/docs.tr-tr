---
title: Visual Basic LINQ to XML ad alanları içeren bir belge oluşturma
description: Ön ek içeren varsayılan ad alanları veya ad alanları içeren belgeler oluşturmak için Visual Basic XML sabit değerlerini kullanın.
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553509"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="1448a-103">Visual Basic ad alanları içeren bir belge oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1448a-103">How to create a document with namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="1448a-104">Bu makalede, Visual Basic ad alanları içeren bir belge oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1448a-104">This article shows how to create a document with namespaces in Visual Basic.</span></span>

<span data-ttu-id="1448a-105">Visual Basic XML değişmez değerleri kullanılırken, kullanıcılar bir genel varsayılan XML ad alanı tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1448a-105">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="1448a-106">Bu ad alanı, XML değişmez değerleri ve XML özellikleri için varsayılan ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="1448a-106">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="1448a-107">Varsayılan XML ad alanı, proje düzeyinde ya da dosya düzeyinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1448a-107">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="1448a-108">Dosya düzeyinde tanımlıysa, proje düzeyinde varsayılan ad alanını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1448a-108">If it's defined at the file level, it overrides the default namespace at the project level.</span></span>

<span data-ttu-id="1448a-109">Diğer ad alanlarını da tanımlayabilir ve bu ad alanları için ad alanı öneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1448a-109">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span> <span data-ttu-id="1448a-110">`Imports`Her iki ad alanı türünü tanımlamak için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1448a-110">You use the `Imports` keyword to define both types of namespace.</span></span>

<span data-ttu-id="1448a-111">Daha fazla bilgi için bkz. [Visual Basic xml sabit değerleri](xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="1448a-111">For more information, see [XML literals in Visual Basic](xml-literals.md).</span></span>

<span data-ttu-id="1448a-112">Varsayılan XML ad alanının yalnızca öğeler için geçerli olduğunu ve öznitelikler için geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1448a-112">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="1448a-113">Varsayılan ad alanındaki öznitelikler varsayılan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1448a-113">Attributes are by default in the default namespace.</span></span> <span data-ttu-id="1448a-114">Ancak, bir ad alanına bir özniteliği yerleştirmek için bir ad alanı öneki kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1448a-114">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>

## <a name="example-create-a-document-that-has-a-namespace"></a><span data-ttu-id="1448a-115">Örnek: ad alanı bulunan bir belge oluşturma</span><span class="sxs-lookup"><span data-stu-id="1448a-115">Example: Create a document that has a namespace</span></span>

<span data-ttu-id="1448a-116">Bu örnek, bir ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1448a-116">This example creates a document that contains a namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="1448a-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1448a-117">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="1448a-118">Örnek: biri öneki olan iki ad alanı olan bir belge oluşturun</span><span class="sxs-lookup"><span data-stu-id="1448a-118">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="1448a-119">Bu örnekte iki ad alanı içeren bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1448a-119">This example creates a document that contains two namespaces.</span></span> <span data-ttu-id="1448a-120">Biri varsayılan ad alanıdır, diğeri bir ön eke sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1448a-120">One is the default namespace, the other has a prefix.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="1448a-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1448a-121">This example produces the following output:</span></span>

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="1448a-122">Örnek: iki ad alanı olan, her ikisi de önekle bir belge oluşturun</span><span class="sxs-lookup"><span data-stu-id="1448a-122">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="1448a-123">Aşağıdaki örnek, ad alanı önekleri olan iki ad alanını içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1448a-123">The following example creates a document that contains two namespaces, both having namespace prefixes.</span></span>

<span data-ttu-id="1448a-124">Bir XML ağacını serileştirilirken, LINQ to XML her bir öğenin belirlenen ad alanında olması için ad alanı bildirimleri gerektiği gibi yayar.</span><span class="sxs-lookup"><span data-stu-id="1448a-124">When serializing an XML tree, LINQ to XML emits namespace declarations as required so that each element is in its designated namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="1448a-125">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1448a-125">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="1448a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1448a-126">See also</span></span>

- [<span data-ttu-id="1448a-127">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="1448a-127">Namespaces overview</span></span>](namespaces-overview.md)
