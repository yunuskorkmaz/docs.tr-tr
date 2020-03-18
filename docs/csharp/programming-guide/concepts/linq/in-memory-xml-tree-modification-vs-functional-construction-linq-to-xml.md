---
title: Bellek İçi XML Ağaç Modifikasyonu vs Fonksiyonel Yapı (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484560"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="2f639-102">Bellek İçi XML Ağaç Modifikasyonu vs Fonksiyonel Yapı (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f639-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2f639-103">Bir XML ağacını yerinde değiştirmek, Bir XML belgesinin şeklini değiştirmek için geleneksel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="2f639-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="2f639-104">Tipik bir uygulama, belgeyi DOM veya [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dom gibi bir veri deposuna yükler; düğümleri eklemek, düğümleri silmek veya düğümlerin içeriğini değiştirmek için bir programlama arabirimi kullanır; ve sonra XML'i bir dosyaya kaydeder veya ağ üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="2f639-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2f639-105">birçok senaryoda yararlı olan başka bir yaklaşım sağlar: *fonksiyonel yapı*.</span><span class="sxs-lookup"><span data-stu-id="2f639-105">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="2f639-106">İşlevsel yapı, verileri değiştirmeyi bir veri deposunun ayrıntılı manipülasyonu olarak değil, bir dönüşüm sorunu olarak ele alır.</span><span class="sxs-lookup"><span data-stu-id="2f639-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="2f639-107">Verilerin bir temsilini alıp bir formdan diğerine verimli bir şekilde dönüştürebilirseniz, sonuç, bir veri deposunu alıp başka bir şekil almak için bir şekilde manipüle etmişsiniz gibi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2f639-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="2f639-108">İşlevsel yapı yaklaşımının anahtarı, sorguların <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucuların sonuçlarını aktarmaktır.</span><span class="sxs-lookup"><span data-stu-id="2f639-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="2f639-109">Çoğu durumda dönüşüm kodunu veri deposunu işlemek için gereken sürenin çok kısa bir kısmında yazabilirsiniz ve bu kodun daha sağlam ve bakımı daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2f639-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="2f639-110">Bu gibi durumlarda, dönüşüm yaklaşımı daha fazla işlem gücü gerektirebilir, ancak verileri değiştirmek için daha etkili bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="2f639-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="2f639-111">Bir geliştirici işlevsel yaklaşıma aşinaysa, birçok durumda ortaya çıkan kodu anlamak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2f639-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="2f639-112">Ağacın her parçasını değiştiren kodu bulmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2f639-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="2f639-113">Bir XML ağacını yerinde değiştirdiğiniz yaklaşım birçok DOM programcısı na daha tanıdık geliyor, oysa işlevsel yaklaşım kullanılarak yazılan kod, henüz bu yaklaşımı anlamayan bir geliştiriciye yabancı görünebilir.</span><span class="sxs-lookup"><span data-stu-id="2f639-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="2f639-114">Yalnızca büyük bir XML ağacında küçük bir değişiklik yapmak zorundaysanız, birçok durumda bir ağacı yerinde değiştirdiğiniz yaklaşım daha az CPU süresi alır.</span><span class="sxs-lookup"><span data-stu-id="2f639-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="2f639-115">Bu konu, her iki yaklaşımla da uygulanan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f639-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="2f639-116">Öznitelikleri Öğelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2f639-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="2f639-117">Bu örnekte, özniteliklerin öğe haline gelmesi için aşağıdaki basit XML belgesini değiştirmek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="2f639-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="2f639-118">Bu konu ilk olarak geleneksel yerinde modifikasyon yaklaşımını sunar.</span><span class="sxs-lookup"><span data-stu-id="2f639-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="2f639-119">Daha sonra fonksiyonel inşaat yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f639-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="2f639-120">XML Ağacını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2f639-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="2f639-121">Özniteliklerden öğeler oluşturmak için bazı yordam kodu yazabilir ve ardından öznitelikleri aşağıdaki gibi silebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2f639-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="2f639-122">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2f639-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="2f639-123">Fonksiyonel İnşaat Yaklaşımı</span><span class="sxs-lookup"><span data-stu-id="2f639-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="2f639-124">Bunun aksine, işlevsel bir yaklaşım, kaynak ağaçtan öğeleri ve öznitelikleri seçmek ve yeni ağaca eklendikleri kadar uygun şekilde dönüştürmek için koddan oluşur.</span><span class="sxs-lookup"><span data-stu-id="2f639-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="2f639-125">İşlevsel yaklaşım aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="2f639-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="2f639-126">Bu örnek, ilk örnekle aynı XML çıktıları.</span><span class="sxs-lookup"><span data-stu-id="2f639-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="2f639-127">Ancak, işlevsel yaklaşımda yeni XML'in ortaya çıkan yapısını gerçekten görebildiğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2f639-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="2f639-128">Öğenin oluşturulmasını, `Root` öğeyi `Child1` kaynak ağaçtan çeken kodu ve öznitelikleri kaynak ağaçtan yeni ağaçtaki öğelere dönüştüren kodu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f639-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="2f639-129">Bu durumda işlevsel örnek herhangi bir ilk örnek daha kısa değildir ve gerçekten herhangi bir basit değildir.</span><span class="sxs-lookup"><span data-stu-id="2f639-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="2f639-130">Ancak, bir XML ağacında yapmak için birçok değişiklik varsa, işlevsel olmayan yaklaşım oldukça karmaşık ve biraz kalın olacak.</span><span class="sxs-lookup"><span data-stu-id="2f639-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="2f639-131">Buna karşılık, işlevsel yaklaşımı kullanırken, istenen içeriği çekmek için sorguları ve ifadeleri uygun şekilde katıştırarak, yine de yalnızca istenen XML'yi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="2f639-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="2f639-132">İşlevsel yaklaşım, bakımı daha kolay olan kod verir.</span><span class="sxs-lookup"><span data-stu-id="2f639-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="2f639-133">Bu durumda fonksiyonel yaklaşım muhtemelen oldukça iyi ağaç manipülasyon yaklaşımı olarak gerçekleştirmek olmaz dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2f639-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="2f639-134">Ana sorun, işlevsel yaklaşımın daha kısa ömürlü nesneler oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2f639-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="2f639-135">Ancak, fonksiyonel yaklaşımın kullanılması daha fazla programcı üretkenliğine olanak sağlıyorsa, denge etkili dir.</span><span class="sxs-lookup"><span data-stu-id="2f639-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="2f639-136">Bu çok basit bir örnektir, ancak iki yaklaşım arasındaki felsefe farkı göstermek için hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="2f639-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="2f639-137">İşlevsel yaklaşım, daha büyük XML belgelerini dönüştürmek için daha fazla üretkenlik artışı elde eder.</span><span class="sxs-lookup"><span data-stu-id="2f639-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  