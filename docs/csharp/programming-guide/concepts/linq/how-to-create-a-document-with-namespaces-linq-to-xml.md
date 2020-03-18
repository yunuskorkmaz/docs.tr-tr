---
title: Ad alanları (C#) (LINQ - XML) içeren bir belge oluşturma
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141327"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Ad alanları (C#) (LINQ - XML) içeren bir belge oluşturma
Bu konu, ad boşlukları içeren belgelerin nasıl oluşturulacak olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
 Ad alanında bulunan bir öğe veya öznitelik oluşturmak için önce bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirir ve baş harfe bildirirsiniz. Daha sonra ad alanını dize olarak ifade edilen yerel adla birleştirmek için ekleme işleci aşırı yüklenmesini kullanırsınız.  
  
 Aşağıdaki örnek, tek bir ad alanına sahip bir belge oluşturur. Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] varsayılan ad alanı ile bu belgeyi serihale eder.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir ad alanına sahip bir belge oluşturur. Ayrıca, ad alanı önekiyle ad alanını bildiren bir öznitelik de oluşturur. Önek ile bir ad alanı bildiren bir öznitelik oluşturmak için, öznitelik adı ad alanı önek ve bu ad <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanı içinde olduğu bir öznitelik oluşturun. Bu özniteliğin değeri ad alanının URI'sidir.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki ad alanı içeren bir belge nin oluşturulması gösterilmektedir. Bunlardan biri varsayılan ad alanıdır. Başka bir önek ile bir ad alanıdır.  
  
 Ad alanı öznitelikleri kök öğesine dahil edilerek, ad `http://www.adventure-works.com` alanları varsayılan ad `www.fourthcoffee.com` alanı olacak şekilde seri hale getirilir ve "fc" önekiyle seri hale getirilir. Varsayılan ad alanı bildiren bir öznitelik oluşturmak için, ad alanı olmadan "xmlns" adında bir öznitelik oluşturursunuz. Özniteliğin değeri varsayılan ad alanı URI'dir.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
 Aşağıdaki örnek, her ikisi de ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
 Aynı sonucu gerçekleştirmenin başka bir yolu da, bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve oluşturmak yerine genişletilmiş adları kullanmaktır.  
  
 Bu yaklaşımın performans etkileri vardır. Genişletilmiş bir ad içeren bir dize [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geçmek her zaman , adını ayrıştırmak gerekir, atomize ad alanı bulmak ve atomize adı bulmak. Bu işlem CPU zaman alır. Performans önemliyse, bir <xref:System.Xml.Linq.XNamespace> nesneyi açıkça beyan etmek ve kullanmak isteyebilirsiniz.  
  
 Performans önemli bir konuysa, daha fazla bilgi için [XName Nesnelerinin (LINQ-XML) (C#) Ön AtomizeLeştirilmesi'ne](./pre-atomization-of-xname-objects-linq-to-xml.md) bakın  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İsim Alanlarına Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md)
