---
title: XPath Namespace gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fed73c0a9c9bb4fba2644d76f470a8bdcace2b83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xpath-namespace-navigation"></a>XPath Namespace gezinme
XPath sorguları XML belgeleri ile kullanmak için doğru adres XML ad alanları ve ad alanları tarafından bulunan öğeleri olması. Ad alanları adları birden fazla bağlamında kullanıldığında oluşabilecek belirsizlikleri önleyebilir. Örneğin, adı `ID` farklı bir XML belgesi öğelerle ilişkili birden fazla tanımlayıcısına başvurabilir. Namespace sözdizimi URI, adları ve bir XML belgesi öğelerini ayırt öneklerini belirtir.  
  
 Bu konudaki örnek bir XML belgesi gezinme içinde önekleri kullanımını gösteren <xref:System.Xml.XPath.XPathNavigator>. Ad alanları ve sözdizimi hakkında daha fazla bilgi için bkz: [anlama XML ad alanları](https://msdn.microsoft.com/library/aa468565.aspx).  
  
## <a name="namespace-declarations"></a>Namespace bildirimi  
 Namespace bildirimi bir XML belgesi öğelerini ayrılabilen ve olun adreslenebilir örneğini kullanırken <xref:System.Xml.XPath.XPathNavigator>. Namespace önekleri ad alanları adreslemek için kısa bir sözdizimi sağlar.  
  
 Önekleri form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` bu sözdiziminde öneki "`e`" ad alanı resmi URI'sini ifadesinin kısaltmasıdır. Tanımlayabilirsiniz `Body` öğesi bir üyesi olarak `Envelope` sözdizimini kullanarak ad alanı: `e:Body`.  
  
 Aşağıdaki XML belgesi olarak başvurulan `response.xml` sonraki bölümde Gezinti örnekte.  
  
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
  
## <a name="navigation-by-namespace-prefix"></a>Namespace ön eke göre gezinme  
 Bu bölümdeki kod kullanır <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.Xml.XmlNamespaceManager> seçmek için nesneleri `Search` önceki bölümdeki XML belgesinden öğesi. Sorgu `xpath` ad alanı öneklerini her öğe üzerinde yolu içerir. Her öğe içeren ad alanları kesin kimliğini belirten doğru gezinme sağlar `Search` öğesi tarafından <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi.  
  
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
  
 Tam ad alanları ve adları uygun duyarlık kolaylık sağlamak amacıyla büyük. Küçük bir deneme belge tanımı ve önceki örnek kodda Gezinti tam öğe adları olmadan özel durumları oluşturur doğrular. Örneğin, öğe tanımında: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`ve sorgu: dize `xpath = "/s:Envelope/s:Body/Search";` ad alanı öneki olmadan `Search` öğesi döndürür `null` yerine `Search` öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
