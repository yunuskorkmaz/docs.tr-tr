---
title: 'Nasıl yapılır: ad alanları (LINQ to XML) ile belge oluşturma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751898"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="93146-102">Nasıl yapılır: ad alanları (LINQ to XML) ile belge oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93146-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="93146-103">Bu konuda, Visual Basic'de ad alanları ile belge oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93146-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="93146-104">Visual Basic'de XML değişmez değerlerini kullanarak, kullanıcıların bir genel varsayılan XML ad alanı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93146-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="93146-105">Bu ad alanı, hem XML sabit değerleri ve XML özellikleri için varsayılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="93146-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="93146-106">Varsayılan XML ad alanı, proje düzeyinde veya dosya düzeyinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="93146-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="93146-107">Dosya düzeyinde tanımlanmışsa, varsayılan ad alanı proje düzeyinde geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="93146-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="93146-108">Ayrıca, diğer ad alanları tanımlayın ve bu ad alanları için ad alanı öneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="93146-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="93146-109">Varsayılan ad alanları hem de ad alanı öneki kullanarak tanımladığınız `Imports` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="93146-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="93146-110">Daha fazla bilgi için [Visual Basic'te XML değişmez değerlerine giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="93146-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="93146-111">Varsayılan XML ad alanı yalnızca öğeler ve öznitelikler için geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="93146-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="93146-112">Varsayılan ad alanı yok olarak her zaman öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="93146-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="93146-113">Ancak, bir ad alanında bir öznitelik koymak için bir ad alanı öneki kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93146-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93146-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="93146-114">Example</span></span>  
 <span data-ttu-id="93146-115">Bu örnek, bir ad uzayını içeren bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93146-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="93146-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="93146-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="93146-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="93146-117">Example</span></span>  
 <span data-ttu-id="93146-118">Bu örnekte, biri varsayılan ad alanı iki ad alanları içeren bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93146-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="93146-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="93146-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="93146-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="93146-120">Example</span></span>  
 <span data-ttu-id="93146-121">Aşağıdaki örnek, birden çok ad ad alanı öneklerini her ikisini birden içeren bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93146-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="93146-122">Bir XML ağacı serileştirilirken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] her öğe, ayrılmış ad alanı içinde olması gerektiği gibi ad alanı bildirimi yayar.</span><span class="sxs-lookup"><span data-stu-id="93146-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="93146-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="93146-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93146-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93146-124">See Also</span></span>  
 [<span data-ttu-id="93146-125">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="93146-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
