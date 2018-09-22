---
title: Bellek içi XML ağacı değişikliği ve İşlevsel oluşturma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: fb461d6730260f01f0439b7feb239d51b29ee3c7
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577210"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Bellek içi XML ağacı değişikliği ve İşlevsel oluşturma (LINQ to XML) (C#)
Bir XML ağacı yerde değiştirme, bir XML belgesi şeklini değiştirmek için geleneksel bir yaklaşımdır. Tipik bir uygulama bir belge DOM gibi bir veri deposuna yükler ya da [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; düğümleri eklediğinizde, düğümleri silin veya düğümler; içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML bir dosyaya kaydeder veya bir ağ üzerinden iletir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pek çok senaryoda kullanışlıdır başka bir yaklaşım sağlar: *işlevsel oluşturma*. İşlevsel oluşturma, değiştirme veri dönüşümünün bir sorun, yerine ayrıntılı işleme bir veri deposu olarak değerlendirir. Bir veri temsilini alın ve verimli bir şekilde bir formdan başka bir dönüştürme, bir veri deposu sürdü ve başka bir şekil gerçekleştirilecek şekilde yönetilebilir gibi sonuç aynıdır. İşlevsel oluşturma yaklaşımını anahtarı için sorguların sonuçlarını geçirmektir <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucular.  
  
 Çoğu durumda veri deposu işlemek için harcadığım süreyi kesir dönüşümsel kodu yazabilirsiniz ve bu kodu daha sağlam ve bakımı kolay. Daha fazla işlemci gücü, dönüşümsel yaklaşım sürebilir olsa bile bu gibi durumlarda, bu verileri değiştirmek için bir daha etkili yoludur. Bir geliştirici işlevsel yaklaşım ile ilgili bilgi sahibi ise, çoğu durumda Sonuç kodu anlamak daha kolay olur. Her ağacın parçası değiştiren bir kodun bulmak daha kolaydır.  
  
 İşlevsel yaklaşım kullanılarak yazılmış kod henüz bu yaklaşımı anlamıyor bir geliştirici için tanıdık gelmiyor ancak burada bir XML ağacı yerinde değişiklik birçok DOM programcıları için daha tanıdık bir yaklaşımdır. Yalnızca büyük bir XML ağacı için küçük bir değişiklik yapmak varsa, burada, çoğu durumda bir yerde bir ağaç değişiklik yaklaşım daha az CPU zaman alabilir.  
  
 Bu konu, her iki yaklaşım ile uygulanan bir örnek sağlar.  
  
## <a name="transforming-attributes-into-elements"></a>Öğelerine dönüştürme öznitelikleri  
 Bu örnekte, böylece öznitelikleri öğelerine haline gelir. aşağıdaki basit XML belgesi değiştirmek istediğiniz varsayalım. Bu konuda, ilk yerinde değişikliği geleneksel yaklaşım sunulmaktadır. Ardından, bir işlev oluşturma yaklaşımı da gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>XML ağacı değiştirme  
 Öznitelikleri öğeleri oluşturmak için yordam kod yazma ve öznitelikleri gibi silin:  
  
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
  
### <a name="functional-construction-approach"></a>İşlevsel oluşturma yaklaşımı  
 Bunun aksine, işlevsel bir yaklaşım çekme ve öğeler ve öznitelikler kaynak ağacından seçme ve bunları yeni ağacına eklendikçe uygun şekilde dönüştürme yeni bir ağaç oluşturmak için kod oluşur. İşlevsel yaklaşım aşağıdaki gibi görünür:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Bu örnekte, ilk örnekle aynı XML çıkarır. Ancak, elde edilen işlevsel yaklaşım yeni XML yapısını gerçekten görebilirsiniz dikkat edin. Oluşturulmasını gördüğünüz `Root` öğesinde, kodu çeker `Child1` kaynak ağacının ve kaynak ağacının öznitelikleri öğelere yeni ağacında dönüştüren kod öğesi.  
  
 İşlevsel örneği bu durumda ilk örnek kısa herhangi değil ve gerçekten daha kolay değildir. Ancak, bir XML ağacına yapmak için birçok değişiklik varsa, işlev olmayan bir yaklaşım oldukça karmaşık ve biraz geniş açılı olur. Buna karşılık, işlevsel yaklaşım kullanırken, yalnızca form istenen XML, sorguları ve ifadeler, istenen içeriği çekmek uygun olarak eklemeye devam. İşlevsel yaklaşım oluşturmanın kod üretir.  
  
 Bu durumda işlevsel yaklaşım büyük olasılıkla oldukça ağaç işleme yaklaşım yanı sıra gerçekleştirecek değil dikkat edin. Ana sorunu işlevsel yaklaşım daha kısa süreli nesneleri oluşturmasıdır. Ancak işlevsel yaklaşım kullanarak büyük Programcı verimliliği için izin veriyorsa etkili bir düşüş olur.  
  
 Bu çok basit bir örneği, ancak felsefesi iki yaklaşım arasındaki farkı göstermek için kullanılır. İşlevsel yaklaşım daha büyük XML belgelerini dönüştürmek için büyük üretkenlik artışı sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [(LINQ to XML) XML ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
