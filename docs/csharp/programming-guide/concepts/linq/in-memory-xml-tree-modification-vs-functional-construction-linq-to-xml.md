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
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Bellek İçi XML Ağaç Modifikasyonu vs Fonksiyonel Yapı (LINQ to XML) (C#)
Bir XML ağacını yerinde değiştirmek, Bir XML belgesinin şeklini değiştirmek için geleneksel bir yaklaşımdır. Tipik bir uygulama, belgeyi DOM veya [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dom gibi bir veri deposuna yükler; düğümleri eklemek, düğümleri silmek veya düğümlerin içeriğini değiştirmek için bir programlama arabirimi kullanır; ve sonra XML'i bir dosyaya kaydeder veya ağ üzerinden iletir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]birçok senaryoda yararlı olan başka bir yaklaşım sağlar: *fonksiyonel yapı*. İşlevsel yapı, verileri değiştirmeyi bir veri deposunun ayrıntılı manipülasyonu olarak değil, bir dönüşüm sorunu olarak ele alır. Verilerin bir temsilini alıp bir formdan diğerine verimli bir şekilde dönüştürebilirseniz, sonuç, bir veri deposunu alıp başka bir şekil almak için bir şekilde manipüle etmişsiniz gibi aynıdır. İşlevsel yapı yaklaşımının anahtarı, sorguların <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucuların sonuçlarını aktarmaktır.  
  
 Çoğu durumda dönüşüm kodunu veri deposunu işlemek için gereken sürenin çok kısa bir kısmında yazabilirsiniz ve bu kodun daha sağlam ve bakımı daha kolaydır. Bu gibi durumlarda, dönüşüm yaklaşımı daha fazla işlem gücü gerektirebilir, ancak verileri değiştirmek için daha etkili bir yoldur. Bir geliştirici işlevsel yaklaşıma aşinaysa, birçok durumda ortaya çıkan kodu anlamak daha kolaydır. Ağacın her parçasını değiştiren kodu bulmak kolaydır.  
  
 Bir XML ağacını yerinde değiştirdiğiniz yaklaşım birçok DOM programcısı na daha tanıdık geliyor, oysa işlevsel yaklaşım kullanılarak yazılan kod, henüz bu yaklaşımı anlamayan bir geliştiriciye yabancı görünebilir. Yalnızca büyük bir XML ağacında küçük bir değişiklik yapmak zorundaysanız, birçok durumda bir ağacı yerinde değiştirdiğiniz yaklaşım daha az CPU süresi alır.  
  
 Bu konu, her iki yaklaşımla da uygulanan bir örnek sağlar.  
  
## <a name="transforming-attributes-into-elements"></a>Öznitelikleri Öğelere Dönüştürme  
 Bu örnekte, özniteliklerin öğe haline gelmesi için aşağıdaki basit XML belgesini değiştirmek istediğinizi varsayalım. Bu konu ilk olarak geleneksel yerinde modifikasyon yaklaşımını sunar. Daha sonra fonksiyonel inşaat yaklaşımını gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>XML Ağacını Değiştirme  
 Özniteliklerden öğeler oluşturmak için bazı yordam kodu yazabilir ve ardından öznitelikleri aşağıdaki gibi silebilirsiniz:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Fonksiyonel İnşaat Yaklaşımı  
 Bunun aksine, işlevsel bir yaklaşım, kaynak ağaçtan öğeleri ve öznitelikleri seçmek ve yeni ağaca eklendikleri kadar uygun şekilde dönüştürmek için koddan oluşur. İşlevsel yaklaşım aşağıdaki gibi görünür:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Bu örnek, ilk örnekle aynı XML çıktıları. Ancak, işlevsel yaklaşımda yeni XML'in ortaya çıkan yapısını gerçekten görebildiğinize dikkat edin. Öğenin oluşturulmasını, `Root` öğeyi `Child1` kaynak ağaçtan çeken kodu ve öznitelikleri kaynak ağaçtan yeni ağaçtaki öğelere dönüştüren kodu görebilirsiniz.  
  
 Bu durumda işlevsel örnek herhangi bir ilk örnek daha kısa değildir ve gerçekten herhangi bir basit değildir. Ancak, bir XML ağacında yapmak için birçok değişiklik varsa, işlevsel olmayan yaklaşım oldukça karmaşık ve biraz kalın olacak. Buna karşılık, işlevsel yaklaşımı kullanırken, istenen içeriği çekmek için sorguları ve ifadeleri uygun şekilde katıştırarak, yine de yalnızca istenen XML'yi oluşturursunuz. İşlevsel yaklaşım, bakımı daha kolay olan kod verir.  
  
 Bu durumda fonksiyonel yaklaşım muhtemelen oldukça iyi ağaç manipülasyon yaklaşımı olarak gerçekleştirmek olmaz dikkat edin. Ana sorun, işlevsel yaklaşımın daha kısa ömürlü nesneler oluşturmasıdır. Ancak, fonksiyonel yaklaşımın kullanılması daha fazla programcı üretkenliğine olanak sağlıyorsa, denge etkili dir.  
  
 Bu çok basit bir örnektir, ancak iki yaklaşım arasındaki felsefe farkı göstermek için hizmet vermektedir. İşlevsel yaklaşım, daha büyük XML belgelerini dönüştürmek için daha fazla üretkenlik artışı elde eder.  
  