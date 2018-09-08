---
title: XPath Namespace Gezinti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6d4f63dacc09208176b47dbca38783f1e9bc0a1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194729"
---
# <a name="xpath-namespace-navigation"></a>XPath Namespace Gezinti
XPath sorguları ile XML belgeleri kullanmak için doğru adres XML ad alanları ve ad alanları tarafından içerilen öğelerin sahip. Ad alanları, adları, birden fazla bağlamında kullanıldığında oluşabilecek belirsizlikleri önleyebilir. Örneğin, adı `ID` farklı bir XML belgesi öğelerle ilişkili birden fazla tanımlayıcı bakabilirsiniz. Namespace sözdizimi URI'ler, adları ve bir XML belgesinin öğelerini ayırt önekler belirtir.  
  
 Bu konudaki örnek, bir XML belgesi ile gezinme, ön ekleri kullanımını gösterir <xref:System.Xml.XPath.XPathNavigator>. Ad alanları ve söz dizimi hakkında daha fazla bilgi için bkz: [anlama XML ad alanları](https://msdn.microsoft.com/library/aa468565.aspx).  
  
## <a name="namespace-declarations"></a>Namespace bildirimi  
 Namespace bildirimi bir XML belgesinin öğelerini ayrılabilen ve hale adreslenebilir bir örneğini kullanırken <xref:System.Xml.XPath.XPathNavigator>. Namespace ön ekleri, ad alanları ele almak için kısa bir söz dizimi sağlar.  
  
 Ön ekleri, form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Bu sözdizimi ön eki "`e`" biçimsel URI ad alanı için bir kısaltmadır. Tanımlayabilirsiniz `Body` öğesi bir üyesi olarak `Envelope` sözdizimini kullanarak ad alanı: `e:Body`.  
  
 Aşağıdaki XML belgesi olarak başvurulan `response.xml` Gezinti örnekte sonraki bölümde yer.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>Gezinti Namespace ön eke göre  
 Bu bölümdeki kod <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.Xml.XmlNamespaceManager> nesnelerin `Search` öğeden bir önceki bölümdeki XML belgesi. Sorgu `xpath` ad alanı öneklerini her öğe üzerinde yolu içerir. Her öğe içeren ad alanlarını kesin kimliğini belirterek garantiler doğru gitme `Search` öğe tarafından <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi.  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 Tam ad alanları ve adlarını niteleme duyarlılık kolaylık sağlamak amacıyla büyük. Biraz deneme belge tanımı ve kod önceki örneklerde, tam öğe adları olmadan Gezinti istisnalar fırlatıyorsa doğrular. Örneğin, öğe tanımı: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`ve sorgu: dize `xpath = "/s:Envelope/s:Body/Search";` ad alanı öneki olmadan `Search` öğeyi döndürür `null` yerine `Search` öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
