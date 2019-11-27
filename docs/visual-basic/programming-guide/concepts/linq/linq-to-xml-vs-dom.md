---
title: LINQ to XML vs. DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: b25993fba4d878beb881dfdc46effe5a8ab3485b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331697"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML vs DOM (Visual Basic)
Bu bölümde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli önceden baskın XML programlama API 'SI, W3C Belge Nesne Modeli (DOM) arasındaki bazı önemli farklılıklar açıklanmaktadır.  
  
## <a name="new-ways-to-construct-xml-trees"></a>XML ağaçları oluşturmak için yeni yollar  
 W3C DOM 'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir deyişle, bir belge oluşturur, öğeler oluşturur ve sonra öğeleri belgeye eklersiniz.  
  
 Örneğin, aşağıdaki, DOM 'ın Microsoft uygulamasını kullanarak bir XML ağacı oluşturmanın tipik bir yoludur <xref:System.Xml.XmlDocument>:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 Bu kodlama stili, XML ağacının yapısı hakkında görsel olarak çok fazla bilgi sağlamaz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir XML ağacı oluşturmak için bu yaklaşımı destekler, ancak alternatif bir yaklaşım, *işlevsel oluşturma*da destekler. Visual Basic, işlevsel oluşturma bir XML ağacı oluşturmak için XML değişmez değerlerini kullanır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma kullanarak aynı XML ağacını nasıl oluşturabileceğiniz aşağıda açıklanmıştır:  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 XML ağacını oluşturmak için kodun girintilendiği, temel alınan XML 'nin yapısını gösterir.  
  
 Daha fazla bilgi için bkz. [xml ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Doğrudan XML öğeleriyle çalışma  
 XML ile programlama yaptığınızda, birincil odağınızı genellikle XML öğelerinde ve belki de özniteliklerde bulabilirsiniz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve özniteliklerle çalışabilirsiniz. Örneğin şunları yapabilirsiniz:  
  
- Bir belge nesnesi kullanmadan XML öğeleri oluşturun. Bu, XML ağaçlarının parçaları ile çalışmanız gerektiğinde programlamayı basitleştirir.  
  
- Nesneleri doğrudan bir XML dosyasından yükleme `T:System.Xml.Linq.XElement`.  
  
- `T:System.Xml.Linq.XElement` nesnelerini bir dosyaya veya akışa serileştirme.  
  
 Bu, XML belgesinin XML ağacı için bir mantıksal kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın. DOM 'da, öğeler ve öznitelikler dahil XML düğümlerinin bir XML belgesi bağlamında oluşturulması gerekir. DOM 'da bir ad öğesi oluşturmak için kodun bir parçası aşağıda verilmiştir:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Birden çok belge genelinde bir öğe kullanmak istiyorsanız düğümleri belgeler arasında içeri aktarmanız gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bu karmaşıklık katmanını önler.  
  
 LINQ to XML kullanırken, yalnızca belgenin kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız <xref:System.Xml.Linq.XDocument> sınıfını kullanırsınız.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Adları ve ad alanlarını Basitleştirilmiş olarak Işleme  
 Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanı önekleriyle uğraşmak için gereksinimi ortadan kaldırarak adları ve ad alanlarını basitleştirir. Ad alanı öneklerini denetlemek istiyorsanız, kullanabilirsiniz. Ancak ad alanı öneklerini açıkça denetistemediğinize karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], gerektiğinde serileştirme sırasında ad alanı öneklerini atayacaktır veya varsayılan ad alanlarını kullanarak serileştirilir. Varsayılan ad alanları kullanılırsa, sonuçta elde edilen belgede ad alanı önekleri olmayacaktır. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 DOM ile ilgili başka bir sorun da bir düğümün adını değiştirmenize izin vermez. Bunun yerine, yeni bir düğüm oluşturmanız ve tüm alt düğümleri buna kopyalamanız ve özgün düğüm kimliğini kaybetmemeniz gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir düğümdeki <xref:System.Xml.Linq.XName> özelliğini ayarlamanıza olanak tanıyarak bu sorunu önler.  
  
## <a name="static-method-support-for-loading-xml"></a>XML yükleme için statik yöntem desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenize imkan tanır. Bu, yükleme ve ayrıştırma işlemlerini basitleştirir. Daha fazla bilgi için bkz. [nasıl yapılır: dosyadan XML yükleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
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
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleri, genişletilebilir bir ek açıklama kümesini destekler. Bu, şema bilgileri, öğenin bir kullanıcı arabirimine bağlanıp bağlanmayacağı veya başka bir uygulamaya özgü bilgi türü gibi bir öğeyle ilgili çeşitli bilgileri izlemek için yararlıdır. Daha fazla bilgi için bkz. [LINQ to XML ek açıklamaları](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Şema bilgileri için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla XSD doğrulaması için destek sağlar. Bir XML ağacının bir XSD ile uyumlu olduğunu doğrulayabilirsiniz. XML ağacını şema-doğrulama sonrası bilgi kümesi (PSVı) ile doldurabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: xsd ve <xref:System.Xml.Schema.Extensions>kullanarak doğrulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
