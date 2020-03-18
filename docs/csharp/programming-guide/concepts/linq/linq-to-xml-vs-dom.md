---
title: LINQ - XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168395"
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ - XML vs. DOM (C#)
Bu bölümde, geçerli baskın [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML programlama API'si, W3C Document Object Model (DOM) arasındaki bazı temel farklar açıklanmaktadır.  
  
## <a name="new-ways-to-construct-xml-trees"></a>XML Ağaçları Oluşturmanın Yeni Yolları  
 W3C DOM'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir şekilde, bir belge oluşturursunuz, öğeler oluşturursunuz ve sonra öğeleri belgeye eklersiniz.  
  
 Örneğin, aşağıdaki, DOM Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak <xref:System.Xml.XmlDocument>için tipik bir yol olacaktır:  
  
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
  
 Bu kodlama stili, XML ağacının yapısı hakkında görsel olarak çok fazla bilgi sağlamaz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML ağacı oluşturmak için bu yaklaşımı destekler, ama aynı zamanda alternatif bir yaklaşım, *fonksiyonel inşaat*destekler. Fonksiyonel yapı <xref:System.Xml.Linq.XElement> bir <xref:System.Xml.Linq.XAttribute> XML ağacı oluşturmak için ve yapıcılar kullanır.  
  
 İşlevsel yapıyı kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aynı XML ağacını nasıl oluşturacağınız aşağıda açıklanmıştır:  
  
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
  
 XML ağacını oluşturmak için kodu girintisi altta yatan XML yapısını gösterir dikkat edin.  
  
 Daha fazla bilgi için Bkz. [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md).  
  
## <a name="working-directly-with-xml-elements"></a>Doğrudan XML Elemanları ile Çalışma  
 XML ile program yaptığınızda, birincil odak genellikle XML öğeleri ve belki de öznitelikleri üzerindedir. , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz. Örneğin, aşağıdakileri yapabilirsiniz:  
  
- Belge nesnesi hiç kullanmadan XML öğeleri oluşturun. Bu, XML ağaçlarının parçalarıyla çalışmanız gerektiğinde programlamayı kolaylaştırır.  
  
- Nesneleri `T:System.Xml.Linq.XElement` doğrudan bir XML dosyasından yükleyin.  
  
- Nesneleri `T:System.Xml.Linq.XElement` bir dosyaya veya akışa seri hale getirmek.  
  
 Bunu, XML belgesinin XML ağacı için mantıksal bir kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın. DOM'da, öğeler ve öznitelikler de dahil olmak üzere XML düğümleri, bir XML belgesi bağlamında oluşturulmalıdır. Burada, DOM'da bir ad öğesi oluşturmak için kodun bir parçası ver:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Birden çok belge arasında bir öğe kullanmak istiyorsanız, düğümleri belgeler arasında almanız gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]karmaşıklığı bu katmanı önler.  
  
 LINQ'u XML'e kullanırken, sınıfı yalnızca belgenin <xref:System.Xml.Linq.XDocument> kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız kullanırsınız.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Adların ve Ad Alanlarının Basitleştirilmiş Kullanımı  
 Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ad alanı önekleri ile başa çıkma gereksinimini ortadan kaldırarak adları ve ad alanlarını basitleştirir. Ad alanı önekleri denetlemek istiyorsanız, yapabilirsiniz. Ancak ad alanı öneklerini açıkça denetlememeye karar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] verirseniz, gerekirse serileştirme sırasında ad alanı önekleri atar veya değilse varsayılan ad alanları kullanarak serihale eder. Varsayılan ad alanları kullanılırsa, ortaya çıkan belgede ad alanı önekleri olmaz. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 DOM ile ilgili bir diğer sorun da düğüm adını değiştirmenize izin vermemedir. Bunun yerine, yeni bir düğüm oluşturmanız ve özgün düğüm kimliğini kaybederek tüm alt düğümleri kopyalamanız gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Xml.Linq.XName> özelliği bir düğüm üzerinde ayarlamanızı sağlayarak bu sorunu önler.  
  
## <a name="static-method-support-for-loading-xml"></a>XML Yükleme için Statik Yöntem Desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenizi sağlar. Bu yükleme ve ayrışma kolaylaştırır. Daha fazla bilgi için, [bir dosyadan (C#) XML nasıl yüklenir'](./how-to-load-xml-from-a-file.md)e bakın.  
  
## <a name="removal-of-support-for-dtd-constructs"></a>DTD Yapıları için Desteğin Kaldırılması  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]varlıklar ve varlık başvuruları için desteği kaldırarak XML programlamayı daha da basitleştirir. Varlıkların yönetimi karmaşıktır ve nadiren kullanılır. Desteklerini kaldırmak performansı artırır ve programlama arabirimini basitleştirir. Bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulduğunda, tüm DTD varlıkları genişletilir.  
  
## <a name="support-for-fragments"></a>Parçalar için Destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]`XmlDocumentFragment` sınıf için bir eşdeğer sağlamaz. Ancak, çoğu durumda, `XmlDocumentFragment` kavram <xref:System.Collections.Generic.IEnumerable%601> olarak yazılan bir sorgunun sonucu olarak <xref:System.Xml.Linq.XNode>işlenebilir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, veya .  
  
## <a name="support-for-xpathnavigator"></a>XPathNavigator desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ad alanında <xref:System.Xml.XPath.XPathNavigator> uzantı yöntemleri aracılığıyla destek sağlar. <xref:System.Xml.XPath?displayProperty=nameWithType> Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Beyaz Alan ve Girintinasyon desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dom daha basit beyaz boşluk işler.  
  
 Ortak bir senaryo girintisi XML okumak, herhangi bir beyaz boşluk metin düğümleri olmadan bir bellek XML ağacı oluşturmak (yani, beyaz boşluk koruyarak değil), XML bazı işlemler gerçekleştirmek ve sonra girintiyle XML kaydetmek. XML'yi biçimlendirme yle seri hale aldığınızda, XML ağacında yalnızca önemli beyaz boşluk korunur. Bu, '' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.  
  
 Başka bir yaygın senaryo okumak ve zaten kasıtlı olarak girintilmiş xml değiştirmektir. Bu girintiyi herhangi bir şekilde değiştirmek istemeyebilirsiniz. XML'i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]yüklerken veya ayrıştırırken beyaz alanı koruyarak ve XML'i seri hale rirken biçimlendirmeyi devre dışı bırakarak bunu yapabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]DOM'un yaptığı <xref:System.Xml.Linq.XText> gibi, özel bir <xref:System.Xml.XmlNodeType.Whitespace> düğüm türüne sahip olmak yerine beyaz alanı düğüm olarak depolar.  
  
## <a name="support-for-annotations"></a>Ek Açıklamalar için Destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]öğeler genişletilebilir ek açıklamaları destekler. Bu, şema bilgileri, öğenin kullanıcı arabirimi bağlantısına bağlı olup olmadığı veya uygulamaya özgü başka herhangi bir tür de dahil olmak üzere bir öğe hakkındaki çeşitli bilgileri izlemek için yararlıdır. Daha fazla bilgi [için Linq'den XML Ek Açıklamaları'na](./linq-to-xml-annotations.md)bakın.  
  
## <a name="support-for-schema-information"></a>Şema Bilgi Desteği  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Xml.Schema?displayProperty=nameWithType> ad alanında uzantı yöntemleri aracılığıyla XSD doğrulaması için destek sağlar. Bir XML ağacının Bir XSD ile uyumlu olduğunu doğrulayabilirsiniz. XML ağacını şema sonrası doğrulama bilgi kümesi (PSVI) ile doldurabilirsiniz. Daha fazla bilgi [için, XSD](./how-to-validate-using-xsd-linq-to-xml.md) <xref:System.Xml.Schema.Extensions>ve .
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](./linq-to-xml-overview.md)
