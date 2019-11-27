---
title: 'Nasıl yapılır: konuma göre alt öğeleri bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: c3062963c6144dfafed8b49410208f480c273ec9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349077"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: konuma göre alt öğeleri bulma (XPath-LINQ to XML) (Visual Basic)
Bazen, konumlarına göre öğeleri bulmak isteyebilirsiniz. İkinci öğeyi bulmak isteyebilirsiniz veya beşinci öğe aracılığıyla üçüncü öğeyi bulmak isteyebilirsiniz.  
  
 XPath ifadesi:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Bu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgusunu geç bir şekilde yazmak için iki yaklaşım vardır. <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> işleçlerini kullanabilir veya bir dizini alan <xref:System.Linq.Enumerable.Where%2A> aşırı yüklemeyi kullanabilirsiniz. <xref:System.Linq.Enumerable.Where%2A> aşırı yüklemeyi kullandığınızda, iki bağımsız değişken alan bir lambda ifadesi kullanırsınız. Aşağıdaki örnek, konum temelinde seçim yapmak için her iki yöntemi gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, dördüncü `Test` öğesi ile ikincisini bulur. Sonuç, öğelerin bir koleksiyonudur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: test yapılandırması (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
