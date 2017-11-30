---
title: "İşlev yapımı (LINQ-XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c68fb71fd59d08574cee9eec933cee25e504d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>İşlev yapımı (LINQ-XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]adlı XML öğeleri oluşturmak için güçlü bir yol sağlar *işlevsel yapım*. Bir XML ağacı tek bir deyimde oluşturabilme işlevsel yapıdır.  
  
 Birkaç temel özellikleri vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel yapım etkinleştirmek programlama arabirimi:  
  
-   <xref:System.Xml.Linq.XElement> Oluşturucusu çeşitli içerik için bağımsız değişkenleri alır. Örneğin, başka bir geçirebilirsiniz <xref:System.Xml.Linq.XElement> bir alt öğesi olur nesnesi. Geçirebilirsiniz bir <xref:System.Xml.Linq.XAttribute> öğesinin özniteliği hale nesnesi. Veya herhangi bir dizeye dönüştürülür ve öğenin metin içeriğini olur, nesne türü geçirebilirsiniz.  
  
-   <xref:System.Xml.Linq.XElement> Oluşturucusu geçen bir `params` türünde dizi <xref:System.Object>, böylece oluşturucuya herhangi bir sayıda nesnelerini geçirebilirsiniz. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
-   Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>nesne koleksiyonunda numaralandırılan ve koleksiyondaki tüm öğeleri eklenir. Koleksiyon içeriyorsa <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri, koleksiyondaki her öğe ayrı olarak eklenir. Sonuçlarını geçirmenize olanak tanır bu önemlidir, çünkü bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu oluşturucuya.  
  
 Bir örnek verilmiştir:  
  
 Bir XML ağacı oluşturmak için ve ayrıca sonuçlarını kullanan kodu yazmak için XML değişmez değerleri kullanarak kod yazmak için bu özellikleri etkinleştirmek [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular bir XML ağacı oluşturduğunuzda:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
