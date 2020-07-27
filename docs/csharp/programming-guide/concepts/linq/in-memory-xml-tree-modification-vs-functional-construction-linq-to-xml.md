---
title: Bellek içi XML ağacı değişikliği ile Işlevsel oluşturma (LINQ to XML) (C#)
description: Bu örnekler, bir XML belgesinin şeklini yerinde değiştirerek ve C# içinde LINQ to XML işlevsel oluşturma kullanarak değiştirir.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165789"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Bellek içi XML ağacı değişikliği ile Işlevsel oluşturma (LINQ to XML) (C#)
Bir XML ağacını yerinde değiştirmek, bir XML belgesinin şeklini değiştirmenin geleneksel bir yaklaşımdır. Tipik bir uygulama, bir belgeyi DOM veya gibi bir veri deposuna yükler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ; düğüm eklemek, düğümleri silmek ya da düğümlerin içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML 'i bir dosyaya kaydeder veya bir ağ üzerinden iletir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]birçok senaryoda faydalı olan başka bir yaklaşımı sağlar: *işlevsel oluşturma*. İşlevsel oluşturma, verileri bir veri deposunun ayrıntılı olarak değiştirilmesi yerine dönüşümde bir sorun olarak değiştirir. Verilerin bir temsilini alıp bir formdan diğerine verimli bir şekilde dönüştürebiliyorsanız, sonuç bir veri deposu alıp başka bir şekil almak için bir şekilde işleneceğinden aynı olur. İşlevsel oluşturma yaklaşımına bir anahtar, sorguların sonuçlarını <xref:System.Xml.Linq.XDocument> ve oluşturuculara geçirmektir <xref:System.Xml.Linq.XElement> .  
  
 Çoğu durumda, dönüştürme kodunu veri mağazasının yönetilmesi için gereken sürede yazabilir ve bu kodun daha sağlam ve bakımını daha kolay olur. Bu durumlarda, dönüştürme yaklaşımının daha fazla işlem gücü sürmesine rağmen, verileri değiştirmek için daha etkili bir yoldur. Bir geliştirici işlevsel yaklaşımı kullanıyorsa, sonuçta elde edilen kodun çoğu anlaşılması daha kolay olur. Ağacın her bölümünü değiştiren kodu bulmak kolaydır.  
  
 Bir XML ağacını yerinde değiştirdiğiniz yaklaşımda birçok DOM programcısı daha tanıdık gelecektir. işlevsel yaklaşım kullanılarak yazılan kod, bu yaklaşımı henüz anlayamamış bir geliştiriciye tanıdık görünebilir. Büyük bir XML ağacında yalnızca küçük bir değişiklik yapmanız gerekiyorsa, bir ağacı birçok durumda değiştirdiğiniz yaklaşım daha az CPU süresi alır.  
  
 Bu konu, her iki yaklaşımdan de uygulanan bir örnek sağlar.  
  
## <a name="transforming-attributes-into-elements"></a>Öznitelikleri öğelere dönüştürme  
 Bu örnekte, özniteliklerin öğe haline gelmesi için aşağıdaki basit XML belgesini değiştirmek istediğinizi varsayalım. Bu konu öncelikle geleneksel yerinde değişiklik yaklaşımını gösterir. Ardından işlevsel oluşturma yaklaşımını gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>XML ağacını değiştirme  
 Özniteliklerden öğe oluşturmak için bazı yordamsal kodlar yazabilir ve ardından aşağıdaki gibi öznitelikleri silebilirsiniz:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Bu kod şu çıkışı oluşturur:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>İşlevsel oluşturma yaklaşımı  
 Bunun aksine, işlevsel bir yaklaşım, yeni bir ağaç oluşturmak, kaynak ağaçtan öğe ve öznitelik seçmek ve seçmek ve bunları yeni ağaca eklendikçe uygun şekilde dönüştürmek için koddan oluşur. İşlevsel yaklaşım aşağıdaki gibi görünür:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Bu örnek, ilk örnekle aynı XML 'e çıktı verir. Bununla birlikte, yeni XML 'nin ortaya çıkan yapısını işlevsel yaklaşımda görbildiğinize dikkat edin. `Root`Öğesinin oluşturulmasını, `Child1` kaynak ağacından öğeyi çeken kodu ve kaynak ağaç içindeki öznitelikleri yeni ağaç içindeki öğelere dönüştüren kodu görebilirsiniz.  
  
 Bu örnekte işlevsel örnek, ilk örnekte daha kısa değildir ve gerçekten daha basit değildir. Ancak, bir XML ağacına yaptığınız birçok değişiklik varsa, işlevsel olmayan yaklaşım oldukça karmaşık ve biraz daha kolay hale gelir. Buna karşılık, işlevsel yaklaşımı kullanırken, istenen içeriği çekmek için istenen XML 'yi, uygun şekilde ekleme sorgularını ve ifadeleri yazmanız yeterlidir. İşlevsel yaklaşım, bakımı daha kolay olan kodu verir.  
  
 Bu durumda, işlevsel yaklaşımın büyük olasılıkla ağaç işleme yaklaşımının çok iyi gerçekleştirmediğine dikkat edin. Ana sorun, işlevsel yaklaşımın daha kısa süreli nesneler oluşturmasıdır. Ancak, işlevsel yaklaşımın kullanılması daha fazla programcı verimliliğine izin veriyorsa zorunluluğunu getirir geçerli bir değer.  
  
 Bu çok basit bir örnektir, ancak iki yaklaşım arasındaki FI 'teki farkı göstermek için kullanılır. İşlevsel yaklaşım, büyük XML belgelerini dönüştürmek için daha fazla verimlilik artışı sağlar.  
  