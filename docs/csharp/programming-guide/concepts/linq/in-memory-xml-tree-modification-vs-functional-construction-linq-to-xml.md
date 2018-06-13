---
title: Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 3e6d86ac11f10d7dbb3d270410415fb23acb2e01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333742"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (C#)
Bir XML ağacı yerinde değiştirme, bir XML belgesi şeklini değiştirmek için geleneksel bir yaklaşımdır. Tipik bir uygulama bir belge DOM gibi bir veri deposu yükler veya [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; düğümlerini eklemek, düğümlerini silebilir veya düğümler; içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML bir dosyaya kaydeder veya bir ağ üzerinden iletir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pek çok durumda yararlıdır başka bir yaklaşım sağlar *: işlev yapım*. İşlev oluşturma değiştirme veri dönüşümünün bir sorun olarak yerine ayrıntılı işleme bir veri deposu olarak değerlendirir. Veri gösterimi alabilir ve verimli bir şekilde bir formdan başka dönüştürmek, bir veri deposu sürdü ve başka bir şekil yapılacak herhangi bir şekilde yönetilebilir gibi sonuç aynıdır. İşlev oluşturma yaklaşımın bir anahtar için sorguların sonuçlarını geçirmektir <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucular.  
  
 Çoğu durumda, veri deposu işlemek için harcanacak zaman kesir transformational kod yazabilirsiniz ve bu kodu daha sağlam ve sürdürmek daha kolay. Transformational yaklaşım daha fazla işlemci gücü, sürebilir olsa bile bu durumlarda, bu verileri değiştirmek için bir daha etkili yoldur. Bir geliştirici işlevsel yaklaşımda tanıdık ise, sonuçta elde edilen çoğu durumda anlamak daha kolay kodudur. Her bölümü ağacının değiştirir kod Bul kolaydır.  
  
 İşlev yaklaşımı kullanılarak yazılan kod henüz bu yaklaşımı anlamıyor bir geliştirici için tanınmayan görünebilir ancak burada bir XML ağaç yerinde değiştirme birçok DOM programcıları için daha tanıdık bir yaklaşımdır. Yalnızca büyük bir XML ağacı küçük bir değişiklik yapmak varsa, burada, çoğu durumda yerinde bir ağaç değişiklik yaklaşımı daha az CPU uzun sürer.  
  
 Bu konu, her iki yaklaşımın ile uygulanan bir örnek sağlar.  
  
## <a name="transforming-attributes-into-elements"></a>Öznitelikleri elemanlara dönüştürme  
 Bu örnekte, böylece öğeler öznitelikleri hale aşağıdaki basit bir XML belge değiştirmek istediğinizi varsayalım. Bu konuda, ilk geleneksel yerinde değişikliği yaklaşım sunulmaktadır. Ardından, işlevsel yapım yaklaşım gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>XML ağaç değiştirme  
 Öznitelikleri öğeleri oluşturmak için yordam bazı kodlar yazmak ve öznitelikler gibi silin:  
  
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
  
### <a name="functional-construction-approach"></a>İşlev oluşturma yaklaşımı  
 Bunun aksine, işlevsel bir yaklaşım çekme ve öğeleri ve özniteliklerinin kaynak ağacından seçme ve bunları yeni ağacına eklendikçe uygun şekilde dönüştürme yeni bir ağaç oluşturacak şekilde kodu oluşur. İşlev yaklaşım aşağıdaki gibi görünür:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Bu örnekte, ilk örnekle aynı XML çıkarır. Ancak, yeni XML işlevsel yaklaşımda elde edilen yapısı gerçekten görebilirsiniz dikkat edin. Oluşturulmasını görebilirsiniz `Root` öğesi, çeker kodu `Child1` öğesinden kaynak ağaç ve yeni ağacındaki öğeler kaynak ağacından öznitelikleri dönüştüren kodu.  
  
 İşlevsel örneği bu durumda her ilk örnek kısa değil ve gerçekten herhangi daha basit değil. Bununla birlikte, bir XML ağacına yapmanız gereken çok sayıda değişikliği varsa, olmayan işlev yaklaşım oldukça karmaşık ve biraz geniş açılı olur. Buna karşılık, işlevsel bir yaklaşım kullanırken, yalnızca form sorgular ve ifadeler, istenen içeriği çıkarmak uygun olarak katıştırma istenen XML hala. İşlev yaklaşım oluşturmanın kodunu üretir.  
  
 Bu durumda işlev yaklaşım büyük olasılıkla oldukça ağaç işleme yaklaşım yanı sıra gerçekleştireceği değil dikkat edin. Ana sorunu işlevsel yaklaşımı daha kısa süreli nesneleri oluşturmasıdır. Ancak, kolaylığını işlevsel yaklaşımı kullanmak için büyük Programcı üretkenlik veriyorsa etkili bir bölümdür.  
  
 Bu çok basit bir örnektir ancak felsefesi iki yaklaşım arasındaki farkı göstermek için kullanılır. İşlevsel bir yaklaşım, daha büyük XML belgelerini dönüştüren büyük üretkenlik kazançlar verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ağaçları (LINQ-XML) değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
