---
title: LINQ to XML vs DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f6a89bba1ff2753f04406a060beb37bf2bf6552c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344792"
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ to XML vs DOM (C#)
Bu bölümde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli önceden baskın XML programlama API 'SI, W3C Belge Nesne Modeli (DOM) arasındaki bazı önemli farklılıklar açıklanmaktadır.  
  
## <a name="new-ways-to-construct-xml-trees"></a>XML ağaçları oluşturmak için yeni yollar  
 W3C DOM 'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir deyişle, bir belge oluşturur, öğeler oluşturur ve sonra öğeleri belgeye eklersiniz.  
  
 Örneğin, aşağıdaki, DOM 'ın Microsoft uygulamasını kullanarak bir XML ağacı oluşturmanın tipik bir yoludur <xref:System.Xml.XmlDocument>:  
  
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
  
 Bu kodlama stili, XML ağacının yapısı hakkında görsel olarak çok fazla bilgi sağlamaz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir XML ağacı oluşturmak için bu yaklaşımı destekler, ancak alternatif bir yaklaşım, *işlevsel oluşturma*da destekler. İşlevsel oluşturma, bir XML ağacı oluşturmak için <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucularını kullanır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma kullanarak aynı XML ağacını nasıl oluşturabileceğiniz aşağıda açıklanmıştır:  
  
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
  
 XML ağacını oluşturmak için kodun girintilendiği, temel alınan XML 'nin yapısını gösterir.  
  
 Daha fazla bilgi için bkz. [xml ağaçları oluşturmaC#()](./linq-to-xml-overview.md).  
  
## <a name="working-directly-with-xml-elements"></a>Doğrudan XML öğeleriyle çalışma  
 XML ile programlama yaptığınızda, birincil odağınızı genellikle XML öğelerinde ve belki de özniteliklerde bulabilirsiniz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve özniteliklerle çalışabilirsiniz. Örneğin şunları yapabilirsiniz:  
  
- Bir belge nesnesi kullanmadan XML öğeleri oluşturun. Bu, XML ağaçlarının parçaları ile çalışmanız gerektiğinde programlamayı basitleştirir.  
  
- Nesneleri doğrudan bir XML dosyasından yükleme `T:System.Xml.Linq.XElement`.  
  
- `T:System.Xml.Linq.XElement` nesnelerini bir dosyaya veya akışa serileştirme.  
  
 Bu, XML belgesinin XML ağacı için bir mantıksal kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın. DOM 'da, öğeler ve öznitelikler dahil XML düğümlerinin bir XML belgesi bağlamında oluşturulması gerekir. DOM 'da bir ad öğesi oluşturmak için kodun bir parçası aşağıda verilmiştir:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Birden çok belge genelinde bir öğe kullanmak istiyorsanız düğümleri belgeler arasında içeri aktarmanız gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bu karmaşıklık katmanını önler.  
  
 LINQ to XML kullanırken, yalnızca belgenin kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız <xref:System.Xml.Linq.XDocument> sınıfını kullanırsınız.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Adları ve ad alanlarını Basitleştirilmiş olarak Işleme  
 Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanı önekleriyle uğraşmak için gereksinimi ortadan kaldırarak adları ve ad alanlarını basitleştirir. Ad alanı öneklerini denetlemek istiyorsanız, kullanabilirsiniz. Ancak ad alanı öneklerini açıkça denetistemediğinize karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], gerektiğinde serileştirme sırasında ad alanı öneklerini atayacaktır veya varsayılan ad alanlarını kullanarak serileştirilir. Varsayılan ad alanları kullanılırsa, sonuçta elde edilen belgede ad alanı önekleri olmayacaktır. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 DOM ile ilgili başka bir sorun da bir düğümün adını değiştirmenize izin vermez. Bunun yerine, yeni bir düğüm oluşturmanız ve tüm alt düğümleri buna kopyalamanız ve özgün düğüm kimliğini kaybetmemeniz gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir düğümdeki <xref:System.Xml.Linq.XName> özelliğini ayarlamanıza olanak tanıyarak bu sorunu önler.  
  
## <a name="static-method-support-for-loading-xml"></a>XML yükleme için statik yöntem desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenize imkan tanır. Bu, yükleme ve ayrıştırma işlemlerini basitleştirir. Daha fazla bilgi için bkz. [XML 'i dosyadan yükleme (C#)](./how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>DTD yapıları için desteği kaldırma  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] varlıklar ve varlık başvuruları desteğini kaldırarak XML programlamayı basitleştirir. Varlıkların yönetimi karmaşıktır ve nadiren kullanılır. Desteğinin kaldırılması performansı artırır ve programlama arabirimini basitleştirir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulduktan sonra tüm DTD varlıkları genişletilir.  
  
## <a name="support-for-fragments"></a>Parçalar için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], `XmlDocumentFragment` sınıfı için bir eşdeğer sağlamaz. Ancak çoğu durumda `XmlDocumentFragment` kavramı, <xref:System.Xml.Linq.XNode><xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601> olarak yazılmış bir sorgunun sonucu tarafından işlenebilir.  
  
## <a name="support-for-xpathnavigator"></a>XPathNavigator desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla <xref:System.Xml.XPath.XPathNavigator> için destek sağlar. Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Boşluk ve girintileme desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], DOM 'dan daha fazla boşluk işler.  
  
 Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.  
  
 Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyarak bunu yapabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], DOM gibi özelleştirilmiş bir <xref:System.Xml.XmlNodeType.Whitespace> düğüm türüne sahip olmak yerine, alanı <xref:System.Xml.Linq.XText> bir düğüm olarak depolar.  
  
## <a name="support-for-annotations"></a>Ek açıklamalar için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleri, genişletilebilir bir ek açıklama kümesini destekler. Bu, şema bilgileri, öğenin bir kullanıcı arabirimine bağlanıp bağlanmayacağı veya başka bir uygulamaya özgü bilgi türü gibi bir öğeyle ilgili çeşitli bilgileri izlemek için yararlıdır. Daha fazla bilgi için bkz. [LINQ to XML ek açıklamaları](./linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Şema bilgileri için destek  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla XSD doğrulaması için destek sağlar. Bir XML ağacının bir XSD ile uyumlu olduğunu doğrulayabilirsiniz. XML ağacını şema-doğrulama sonrası bilgi kümesi (PSVı) ile doldurabilirsiniz. Daha fazla bilgi için bkz. XSD ve <xref:System.Xml.Schema.Extensions>[kullanarak doğrulama](./how-to-validate-using-xsd-linq-to-xml.md) .
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](./linq-to-xml-overview.md)
