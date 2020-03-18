---
title: XML'den XML parçaları akışı nasıl yapılır (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714648"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>XML'den XML parçaları akışı nasıl yapılır (C#)

Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacını belleğe yüklemek uygun olmayabilir. Bu konu, bir <xref:System.Xml.XmlReader>.  
  
 Nesneleri okumak <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> için bir kullanmak için en etkili yollarından biri kendi özel eksen yöntemi yazmaktır. Eksen yöntemi genellikle bu konudaki <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>örnekte gösterildiği gibi bir koleksiyon döndürür. Özel eksen yönteminde, <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi çağırarak XML parçasını oluşturduktan sonra, koleksiyonu kullanarak döndürün. `yield return` Bu, özel eksen yönteminize ertelenmiş yürütme semantikleri sağlar.  
  
 Bir <xref:System.Xml.XmlReader> nesneden bir XML ağacı <xref:System.Xml.XmlReader> oluşturduğunuzda, bir öğe üzerinde konumlandırılması gerekir. Yöntem, <xref:System.Xml.Linq.XNode.ReadFrom%2A> öğenin yakın etiketini okuyana kadar geri dönmez.  
  
 Kısmi bir <xref:System.Xml.XmlReader>ağaç oluşturmak istiyorsanız, okuyucuyu <xref:System.Xml.Linq.XElement> ağaca dönüştürmek istediğiniz düğümüzerinde anında konumlandırAbilir ve nesneyi oluşturabilirsiniz. <xref:System.Xml.Linq.XElement>  
  
[Üstbilgi bilgilerine (C#) erişebilen XML parçalarının nasıl aktarılabildiğini](./how-to-stream-xml-fragments-with-access-to-header-information.md) konu, bilgi ve daha karmaşık bir belgenin nasıl akışına ilişkin bir örnek içerir.
  
 Büyük [XML belgelerinin akış dönüşümü (C#) nasıl yapılır](./how-to-perform-streaming-transform-of-large-xml-documents.md) konusu, küçük bir bellek ayak izini korurken son derece büyük XML belgelerini dönüştürmek için LINQ'dan XML'e dönüştürmenin bir örneğini içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, özel bir eksen yöntemi oluşturur. Bir LINQ sorgusu kullanarak sorgulayabilirsiniz. Özel eksen yöntemi, `StreamRootChildDoc`yinelenen bir `Child` öğeye sahip bir belgeyi okumak için özel olarak tasarlanmış bir yöntemdir.  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
bbb  
ccc  
```  
  
 Bu örnekte, kaynak belge çok küçüktür. Ancak, milyonlarca `Child` öğe olsa bile, bu örnek hala küçük bir bellek ayak izi olurdu.  
