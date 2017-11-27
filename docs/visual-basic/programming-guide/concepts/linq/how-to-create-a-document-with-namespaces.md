---
title: "Nasıl yapılır: ad alanları (LINQ-XML) ile bir belge oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 038e2924603eba7250620bc2792ec87b8e978787
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="87cd1-102">Nasıl yapılır: ad alanları (LINQ-XML) ile bir belge oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87cd1-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="87cd1-103">Bu konu, Visual Basic'de ad alanları ile bir belge oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87cd1-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="87cd1-104">Visual Basic'te XML değişmez değerleri kullanırken, kullanıcılar bir genel varsayılan XML ad alanı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87cd1-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="87cd1-105">Bu ad alanı XML değişmez değerleri ve XML özellikleri için varsayılan ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="87cd1-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="87cd1-106">Varsayılan XML ad alanı da proje düzeyinde veya dosya düzeyinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="87cd1-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="87cd1-107">Dosya düzeyinde tanımlanmış olması durumunda, varsayılan ad alanı proje düzeyinde geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="87cd1-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="87cd1-108">Ayrıca, diğer ad tanımlayın ve bu ad alanları için ad alanı öneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="87cd1-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="87cd1-109">Varsayılan ad alanlarını ve bir önek ile ad alanlarını kullanarak tanımladığınız `Imports` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="87cd1-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="87cd1-110">Daha fazla bilgi için bkz: [Visual Basic'te XML değişmez değerleri giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="87cd1-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="87cd1-111">Varsayılan XML ad alanı yalnızca öğeleri ve öznitelikleri geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="87cd1-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="87cd1-112">Hiçbir ad alanındaki her zaman varsayılan öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="87cd1-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="87cd1-113">Ancak, bir ad alanındaki bir öznitelik koymak için bir ad alanı öneki kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87cd1-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87cd1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="87cd1-114">Example</span></span>  
 <span data-ttu-id="87cd1-115">Bu örnek, bir ad alanı içeren bir belgeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87cd1-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="87cd1-116">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="87cd1-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="87cd1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="87cd1-117">Example</span></span>  
 <span data-ttu-id="87cd1-118">Bu örnekte, biri varsayılan ad olan içeren iki ad alanı, bir belgeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87cd1-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="87cd1-119">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="87cd1-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="87cd1-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="87cd1-120">Example</span></span>  
 <span data-ttu-id="87cd1-121">Aşağıdaki örnek, ad alanı öneklerini ikisiyle birden çok ad içeren bir belgeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87cd1-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="87cd1-122">Bir XML ağacı serileştirilirken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] böylece her öğe, belirtilen ad alanında gerektiği gibi ad alanı bildirimleri yayar.</span><span class="sxs-lookup"><span data-stu-id="87cd1-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="87cd1-123">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="87cd1-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87cd1-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87cd1-124">See Also</span></span>  
 [<span data-ttu-id="87cd1-125">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="87cd1-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
