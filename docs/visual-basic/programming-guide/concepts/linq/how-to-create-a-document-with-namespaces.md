---
title: 'Nasıl yapılır: Ad alanları (LINQ to XML) ile bir belge oluşturma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: c61076da5616d98673c4b9258125e3ff0c8821aa
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710452"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="6658b-102">Nasıl yapılır: Ad alanları (LINQ to XML) ile bir belge oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6658b-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6658b-103">Bu konu başlığı altında, Visual Basic ad alanları içeren bir belgenin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6658b-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="6658b-104">Visual Basic XML değişmez değerleri kullanılırken, kullanıcılar bir genel varsayılan XML ad alanı tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6658b-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="6658b-105">Bu ad alanı, XML değişmez değerleri ve XML özellikleri için varsayılan ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="6658b-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="6658b-106">Varsayılan XML ad alanı, proje düzeyinde ya da dosya düzeyinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6658b-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="6658b-107">Dosya düzeyinde tanımlıysa, proje düzeyinde varsayılan ad alanını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6658b-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="6658b-108">Diğer ad alanlarını da tanımlayabilir ve bu ad alanları için ad alanı öneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6658b-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="6658b-109">`Imports` Anahtar sözcüğünü kullanarak, öneki ile hem varsayılan ad alanlarını hem de ad alanlarını tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="6658b-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="6658b-110">Daha fazla bilgi için bkz. [VISUAL BASIC XML değişmez değerlerine giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="6658b-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="6658b-111">Varsayılan XML ad alanının yalnızca öğeler için geçerli olduğunu ve öznitelikler için geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6658b-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="6658b-112">Öznitelikler varsayılan olarak her zaman ad alanı değildir.</span><span class="sxs-lookup"><span data-stu-id="6658b-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="6658b-113">Ancak, bir ad alanına bir özniteliği yerleştirmek için bir ad alanı öneki kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6658b-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6658b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6658b-114">Example</span></span>  
 <span data-ttu-id="6658b-115">Bu örnek, bir ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6658b-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="6658b-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6658b-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="6658b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6658b-117">Example</span></span>  
 <span data-ttu-id="6658b-118">Bu örnekte, biri varsayılan ad alanı olan iki ad alanı içeren bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6658b-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="6658b-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6658b-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="6658b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6658b-120">Example</span></span>  
 <span data-ttu-id="6658b-121">Aşağıdaki örnek, ad alanı önekleri ile birlikte birden çok ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6658b-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="6658b-122">Bir xml ağacını serileştirilirken, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] her bir öğenin belirlenen ad alanında olması için ad alanı bildirimlerini gerektiği gibi yayar.</span><span class="sxs-lookup"><span data-stu-id="6658b-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="6658b-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6658b-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6658b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6658b-124">See also</span></span>

- [<span data-ttu-id="6658b-125">Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6658b-125">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
