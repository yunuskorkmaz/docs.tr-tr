---
title: 'Nasıl yapılır: Ad alanları (C#) Ile bir belge oluşturma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 180dc5138f8f21b3e52e4a8b3cee4748cafdd0f5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593887"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Nasıl yapılır: Ad alanları (C#) Ile bir belge oluşturma (LINQ to XML)
Bu konu başlığı altında, ad alanları ile belgelerin nasıl oluşturulacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir ad alanında olan bir öğe veya öznitelik oluşturmak için, önce bir <xref:System.Xml.Linq.XNamespace> nesne bildirir ve başlatın. Daha sonra, ad alanını bir dize olarak ifade edilen yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanabilirsiniz.  
  
 Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur. Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bu belgeyi varsayılan bir ad alanıyla seri hale getirir.  
  
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
 Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur. Ayrıca ad alanı öneki olan ad alanını bildiren bir öznitelik oluşturur. Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliğin adının ad alanı öneki olduğu ve bu ad <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanında olduğu bir öznitelik oluşturursunuz. Bu özniteliğin değeri, ad alanının URI 'sidir.  
  
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
 Aşağıdaki örnek, iki ad alanı içeren bir belge oluşturmayı gösterir. Bunlardan biri varsayılan ad alanıdır. Diğeri öneki olan bir ad alanıdır.  
  
 Ad alanı özniteliklerini kök öğesine ekleyerek, ad alanları varsayılan ad alanı olacak şekilde `http://www.adventure-works.com` serileştirilir ve `www.fourthcoffee.com` bir "FC" önekiyle serileştirilir. Varsayılan ad alanını bildiren bir öznitelik oluşturmak için, ad alanı olmadan "xmlns" adlı bir öznitelik oluşturursunuz. Özniteliğin değeri varsayılan ad alanı URI 'sidir.  
  
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
 Aşağıdaki örnek, ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.  
  
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
 Aynı sonucu gerçekleştirmenin başka bir yolu da bir <xref:System.Xml.Linq.XNamespace> nesne bildirmek ve oluşturmak yerine genişletilmiş adlar kullanmaktır.  
  
 Bu yaklaşımın performans etkileri vardır. Genişletilmiş bir adı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]içeren bir dizeyi her geçirdiğinizde, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adı ayrıştırmalıdır, atomlanmış ad alanını bulun ve atomlanmış adı bulun. Bu işlem CPU süresini alır. Performans önemliyse, açıkça bir <xref:System.Xml.Linq.XNamespace> nesne bildirmek ve kullanmak isteyebilirsiniz.  
  
 Performans önemli bir sorun ise, daha fazla bilgi için bkz. [XName nesnelerinin ön atomitei (C#LINQ to XML) ()](./pre-atomization-of-xname-objects-linq-to-xml.md)  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md)
