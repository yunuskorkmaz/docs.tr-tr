---
title: LINQ-XML vs. DOM (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 049b60477c7c6de2254dfc355a741a4beb1a725f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ-XML vs. DOM (C#)
Bu bölümde arasındaki bazı temel farklar açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli baskın XML programlama API, W3C belge nesne modeli (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>XML ağaçları oluşturmak için yeni yöntemler  
 W3C DOM'da, aşağıdan bir XML ağacı oluşturmak; diğer bir deyişle, bir belge oluşturun, öğeleri oluşturmak ve ardından öğeleri belgeye ekleyin.  
  
 Örneğin, aşağıdaki DOM, Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için tipik bir yol olabilir <xref:System.Xml.XmlDocument>:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 Kodlama bu stili görsel olarak XML ağaç yapısı hakkında daha bilgi sağlamaz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML ağacı oluşturmak için bu yaklaşım destekler, ancak ayrıca alternatif bir yaklaşım destekler *işlevsel yapım*. İşlev oluşturma kullanan <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> bir XML ağacı yapı oluşturucuları.  
  
 İşte kullanarak aynı XML ağaç nasıl oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlev oluşturma:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",   
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 XML ağacını oluşturmak için kod girintileme temel alınan XML yapısını gösterdiğine dikkat edin.  
  
 Daha fazla bilgi için bkz: [XML ağaçları (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Doğrudan XML öğeleri ile çalışma  
 XML ile program birincil odağı genellikle XML öğeleri ve belki de öznitelikleri olur. İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz. Örneğin, aşağıdakileri yapabilirsiniz:  
  
-   XML öğeleri, bir belge nesnesi kullanmadan oluşturun. Bu XML ağaçları parçaları ile çalışmak olduğunda programlama kolaylaştırır.  
  
-   Yük `T:System.Xml.Linq.XElement` nesneleri doğrudan bir XML dosyası.  
  
-   Seri hale `T:System.Xml.Linq.XElement` nesneleri bir dosyaya veya bir akış.  
  
 Bu XML belge için XML ağacı mantıksal bir kapsayıcı olarak kullanıldığını W3C DOM karşılaştırın. DOM'da, XML düğümlerini, öğeleri ve öznitelikleri içeren bir XML belgesi bağlamında oluşturulması gerekir. Name öğesi DOM'da oluşturmak için kod parçacığını şöyledir:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Bir öğenin birden çok belge boyunca kullanmak istiyorsanız, düğümleri belgeler arasında içeri aktarmanız gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Bu katman karmaşıklık önler.  
  
 LINQ-XML kullanırken, kullandığınız <xref:System.Xml.Linq.XDocument> yalnızca belge kök düzeyinde bir açıklama veya işlem yönergesi eklemek istiyorsanız sınıfı.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Basitleştirilmiş işleme adları ve ad alanları  
 Adları, ad alanları ve ad alanı öneklerini işleme genellikle bir karmaşık XML programlama parçasıdır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]adları ve ad alanları ile ad alanı öneklerini dağıtılacak gereksinimi ortadan kaldırarak basitleştirir. Ad alanı öneklerini denetlemek istiyorsanız, şunları yapabilirsiniz. Ancak, ad alanı öneklerini açıkça denetlemek karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gereklidir veya değillerse varsayılan ad alanlarını kullanma seri ad alanı öneklerini seri hale getirme sırasında atar. Varsayılan ad kullandıysanız, sonuçta elde edilen belgede ad alanı öneklerini olacaktır. Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 DOM başka bir sorun, bir düğümün adı değiştirmenize izin vermez, olmasıdır. Bunun yerine, yeni bir düğüm oluşturmak ve tüm alt düğümleri, kopyalama özgün düğüm kimliği kaybetme gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ayarlamanıza olanak sağlayarak bu sorunu önler <xref:System.Xml.Linq.XName> bir düğümde özelliği.  
  
## <a name="static-method-support-for-loading-xml"></a>XML yükleme desteği statik yöntemi  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML yerine örnek yöntemleri statik yöntemler kullanarak yük olanak sağlar. Bu, yükleme ve ayrıştırma basitleştirir. Daha fazla bilgi için bkz: [nasıl yapılır: yük XML dosyasından (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>DTD yapıları desteğinin kaldırılması  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Daha fazla XML varlıkları ve varlık başvuruları desteği kaldırarak programlama basitleştirir. Varlık Yönetimi karmaşıktır ve nadiren kullanılır. Destek kaldırma performansı artırır ve programlama arabirimi basitleştirir. Zaman bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulur, tüm DTD varlıklar genişletilir.  
  
## <a name="support-for-fragments"></a>Parçaları için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için eşdeğer bir sağlamaz `XmlDocumentFragment` sınıfı. Çoğu durumda, ancak `XmlDocumentFragment` kavram olarak yazılan bir sorgunun sonucu tarafından işlenebilir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XNode>, veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>XPathNavigator desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için destek sağlar <xref:System.Xml.XPath.XPathNavigator> uzantı yöntemleri aracılığıyla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı. Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Boşluk ve girinti desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]beyaz alan daha basit bir şekilde işler DOM'den  
  
 Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil. Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur. Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil. Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz. İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma boşluk koruma ve XML serileştirme zaman biçimlendirme devre dışı bırakma bunu yapabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]boşluk olarak depolayan bir <xref:System.Xml.Linq.XText> özelleştirilmiş sahip olmak yerine düğümü <xref:System.Xml.XmlNodeType.Whitespace> düğüm türü DOM yapar.  
  
## <a name="support-for-annotations"></a>Ek açıklamalar için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]öğeleri açıklamalarının genişletilebilir bir kümesini destekler. Bu, şema bilgileri, bir kullanıcı Arabirimi bağlı öğe olup olmadığı hakkında bilgi veya diğer tür uygulamaya özgü bilgileri gibi bir öğe hakkında çeşitli bilgi izlemek için yararlıdır. Daha fazla bilgi için bkz: [LINQ-XML ek açıklamaları](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).  
  
## <a name="support-for-schema-information"></a>Şema bilgileri için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]genişletme yöntemleri aracılığıyla için XSD doğrulaması desteği sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı. Bir XML ağacı bir XSD ile uyumlu doğrulayabilirsiniz. XML ağaç sonrası doğrulama schema bilgi (PSVI) ile doldurabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: kullanarak XSD doğrulamak](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) ve <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
