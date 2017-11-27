---
title: "Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3652933a5d25b298167f54525800eceee16264e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a>Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)
Bir XML ağacı yerinde değiştirme, bir XML belgesi şeklini değiştirmek için geleneksel bir yaklaşımdır. Tipik bir uygulama bir belge DOM gibi bir veri deposu yükler veya [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; düğümlerini eklemek, düğümlerini silebilir veya düğümler; içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML bir dosyaya kaydeder veya bir ağ üzerinden iletir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pek çok durumda yararlıdır başka bir yaklaşım sağlar*: işlev yapım*. İşlev oluşturma değiştirme veri dönüşümünün bir sorun olarak yerine ayrıntılı işleme bir veri deposu olarak değerlendirir. Veri gösterimi alabilir ve verimli bir şekilde bir formdan başka dönüştürmek, bir veri deposu sürdü ve başka bir şekil yapılacak herhangi bir şekilde yönetilebilir gibi sonuç aynıdır. İşlev oluşturma yaklaşımın bir anahtar için sorguların sonuçlarını geçirmektir <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucular.  
  
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
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
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
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 Bu örnekte, ilk örnekle aynı XML çıkarır. Ancak, yeni XML işlevsel yaklaşımda elde edilen yapısı gerçekten görebilirsiniz dikkat edin. Oluşturulmasını görebilirsiniz `Root` öğesi, çeker kodu `Child1` öğesinden kaynak ağaç ve yeni ağacındaki öğeler kaynak ağacından öznitelikleri dönüştüren kodu.  
  
 İşlevsel örneği bu durumda her ilk örnek kısa değil ve gerçekten herhangi daha basit değil. Bununla birlikte, bir XML ağacına yapmanız gereken çok sayıda değişikliği varsa, olmayan işlev yaklaşım oldukça karmaşık ve biraz geniş açılı olur. Buna karşılık, işlevsel bir yaklaşım kullanırken, yalnızca form sorgular ve ifadeler, istenen içeriği çıkarmak uygun olarak katıştırma istenen XML hala. İşlev yaklaşım oluşturmanın kodunu üretir.  
  
 Bu durumda işlev yaklaşım büyük olasılıkla oldukça ağaç işleme yaklaşım yanı sıra gerçekleştireceği değil dikkat edin. Ana sorunu işlevsel yaklaşımı daha kısa süreli nesneleri oluşturmasıdır. Ancak, kolaylığını işlevsel yaklaşımı kullanmak için büyük Programcı üretkenlik veriyorsa etkili bir bölümdür.  
  
 Bu çok basit bir örnektir ancak felsefesi iki yaklaşım arasındaki farkı göstermek için kullanılır. İşlevsel bir yaklaşım, daha büyük XML belgelerini dönüştüren büyük üretkenlik kazançlar verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ağaçları (LINQ-XML) değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
