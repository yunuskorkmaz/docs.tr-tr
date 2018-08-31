---
title: 'Nasıl yapılır: ad alanları (C#) (LINQ to XML) ile belge oluşturma'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 5937639fc48b82ee155450a3eaa1c7715ee3f9b9
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256732"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Nasıl yapılır: ad alanları (C#) (LINQ to XML) ile belge oluşturma
Bu konuda, ad alanları ile belge oluşturma işlemini gösterir.  
  
## <a name="example"></a>Örnek  
 Bir öğe veya bir ad alanında bir öznitelik oluşturmak için önce bildirmek ve başlatmak bir <xref:System.Xml.Linq.XNamespace> nesne. Bir dize olarak ifade edilen yerel ada sahip ad alanı birleştirmek için Toplama işleci aşırı yüklemesini kullanın.  
  
 Aşağıdaki örnek, bir ad alanı ile bir belge oluşturulur. Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] varsayılan ad alanı bu belgeyle serileştirir.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanı ile bir belge oluşturulur. Ayrıca, ad alanı bir ad alanı öneki ile bildiren bir öznitelik oluşturur. Bir ad alanı öneki bildiren bir öznitelik oluşturmak için burada özniteliğinin adı ad alanı öneki ve bu ad bulunduğu bir öznitelik oluşturun. <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanı. Bu özniteliğin değeri ad alanı URI ' dir.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ad alanları içeren bir belge oluşturulmasını gösterir. Varsayılan ad alanı biridir. Başka bir ad alanı öneki ' dir.  
  
 Kök öğesinde ad alanı öznitelikleri dahil ederek, ad alanlarını serileştirilme şeklini böylece `http://www.adventure-works.com` varsayılan ad alanı ve `www.fourthcoffee.com` "fc" öneki ile seri hale. Varsayılan ad alanı bildiren bir öznitelik oluşturmak için adı "xmlns", ad alanı olmayan bir öznitelik oluşturun. Varsayılan ad alanı URI özniteliğinin değeridir.  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki ad ad alanı öneklerini her ikisini birden içeren bir belge oluşturulur.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a>Örnek  
 Genişletilmiş adlarını bildirme ve oluşturma yerine kullanılacak aynı sonuca ulaşmak için başka bir yolu olan bir <xref:System.Xml.Linq.XNamespace> nesne.  
  
 Bu yaklaşım, performansı etkilere sahiptir. Geçirdiğiniz bir dize, her zaman genişletilmiş bir adı içeren [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gerekir adı ayrıştırmak parçalara ayrılmış ad alanı bulmak ve parçalara ayrılmış adı bulun. Bu işlemin CPU saat sürer. Performans önemliyse bildirme ve kullanma isteyebileceğiniz bir <xref:System.Xml.Linq.XNamespace> açıkça nesne.  
  
 Performans önemli bir sorun olup olmadığını, [parçalara ayırma öncesi XName nesnelerin (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) daha fazla bilgi için  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
