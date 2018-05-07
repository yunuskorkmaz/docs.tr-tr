---
title: 'Nasıl yapılır: ad alanları (C#) (LINQ-XML) ile bir belge oluşturun'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: ab572e0af79d51205167ad60b1b80e8ba6b43707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Nasıl yapılır: ad alanları (C#) (LINQ-XML) ile bir belge oluşturun
Bu konuda, ad alanları ile belgeleri oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bir öğenin veya bir ad alanındaki bir öznitelik oluşturmak için önce bildirme ve başlatma bir <xref:System.Xml.Linq.XNamespace> nesnesi. Toplama işleci aşırı sonra yerel adıyla bir dize olarak ifade edilen ad birleştirmek için kullanın.  
  
 Aşağıdaki örnek bir belge içeren bir ad oluşturur. Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir varsayılan ad alanı bu belgeyle serileştirir.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir belge içeren bir ad oluşturur. Ayrıca, bir ad alanı öneki ad bildiren bir öznitelik oluşturur. Bir ad alanı öneki bildiren bir öznitelik oluşturmak için burada özniteliğin adını ad alanı öneki ve bu adı kullanılıyor bir öznitelik oluşturun <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanı. Bu öznitelik ad alanı URI değeri.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki ad alanı içeren bir belge oluşturulmasını gösterir. Varsayılan ad alanını biridir. Başka bir ad alanı öneki ' dir.  
  
 Kök öğesinin ad alanı öznitelikleri dahil ederek, ad alanlarının serileştirilir böylece http://www.adventure-works.com varsayılan ad alanı ve www.fourthcoffee.com "fc" önekiyle seri. Bir varsayılan ad alanını tanımlayan bir öznitelik oluşturmak için bir öznitelik adı "xmlns", bir ad olmadan ile oluşturun. Varsayılan ad alanı URI'si öznitelik değeri.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
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
 Aşağıdaki örnek, iki ad alanı, ad alanı öneklerini her ikisi de içeren bir belgeyi oluşturur.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
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
 Genişletilmiş adları bildirme ve oluşturma yerine kullanmak için aynı sonucu gerçekleştirmenin başka bir yolu olan bir <xref:System.Xml.Linq.XNamespace> nesnesi.  
  
 Bu yaklaşım performans etkilere sahiptir. Geçirdiğiniz bir dize, her zaman genişletilmiş bir adı olan içeren [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gerekir adı ayrıştırılamıyor atomized ad alanını bulun ve atomized adı bulunamadı. Bu işlem CPU saat sürer. Performans önemliyse, bildirme ve kullanma isteyebilirsiniz bir <xref:System.Xml.Linq.XNamespace> açıkça nesne.  
  
 Performans önemli bir sorun olup olmadığını [öncesi Atomization XName nesnelerin (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) daha fazla bilgi için  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
