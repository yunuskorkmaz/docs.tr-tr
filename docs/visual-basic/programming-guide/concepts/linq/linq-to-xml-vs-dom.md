---
title: LINQ to XML ile DOM (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 8a7d15a8eca8e7d9bcbba068305357ff766a9d9d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623075"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML ile DOM (Visual Basic)
Bu bölümde arasındaki bazı temel farklar açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli hakim XML programlama API, W3C belge nesne modeli (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>XML ağaçlarını oluşturmak için yeni yollar  
 W3C DOM, aşağıdan bir XML ağacı oluşturmak; diğer bir deyişle, bir belge oluşturun, öğeleri oluşturmak ve sonra belgeyi öğeleri ekleyin.  
  
 DOM, Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için normal bir şekilde aşağıdaki gibi olur <xref:System.Xml.XmlDocument>:  
  
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
  
 Kodlama bu stil, görsel olarak XML ağacının yapısı hakkında daha bilgi sağlamaz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML ağacı oluşturmak için bu yaklaşımı destekler, ancak ayrıca alternatif bir yaklaşım destekler *işlevsel oluşturma*. İşlevsel oluşturma, Visual Basic'te, bir XML ağacı oluşturmak için XML sabit değerleri kullanır.  
  
 İşte nasıl kullanarak aynı XML ağacı oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma:  
  
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
  
 Girintileme kodu XML ağacı oluşturmak için temel alınan XML yapısını gösterdiğine dikkat edin.  
  
 Daha fazla bilgi için [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Doğrudan XML öğeleri ile çalışma  
 XML ile program, birincil odak noktası genellikle XML öğeleri ve belki de öznitelikleri olur. İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz. Örneğin, aşağıdakileri yapabilirsiniz:  
  
- XML öğeleri, bir belge nesnesi kullanmadan oluşturun. Bu XML ağaçlarını parçalarını ile çalışacak şekilde olduğunda programlama kolaylaştırır.  
  
- Yük `T:System.Xml.Linq.XElement` doğrudan XML dosyasından nesneleri.  
  
- Seri hale getirme `T:System.Xml.Linq.XElement` nesneleri bir dosyaya veya bir akış.  
  
 W3C XML belgesi için XML ağacı mantıksal kapsayıcı olarak kullanılır DOM karşılaştırın. DOM'da, XML düğüm öğeleri ve öznitelikleri dahil olmak üzere, bir XML belgesi bağlamında oluşturulması gerekir. DOM'da bir name öğesi oluşturmak için kodun bir parçasını şu şekildedir:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Bir öğe arasında birden çok belge kullanmak istiyorsanız, düğümleri belgeler arasında içeri aktarmanız gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Bu katman, karmaşıklığı ortadan kaldırır.  
  
 LINQ to XML kullanarak, kullandığınız <xref:System.Xml.Linq.XDocument> belgenin kök düzeyinde bir açıklama veya işleme yönergesi eklemek isterseniz sınıfı.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Basitleştirilmiş işleme adları ve ad alanları  
 Adları, ad alanları ve ad alanı öneklerini işleme genellikle karmaşık, bir XML programlama parçasıdır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adları ve ad alanları ile ad alanı öneklerini başa çıkma gereksinimi ortadan kaldırarak basitleştirir. Ad alanı ön ekleri denetlemek istiyorsanız, bunu yapabilirsiniz. Ancak, ad alanı öneklerini açıkça denetlemek karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gereklidir veya yoksa varsayılan ad alanlarını kullanarak serileştirmek seri hale getirme sırasında ad alanı öneklerini atar. Varsayılan ad kullandıysanız, sonuçta elde edilen belgede hiçbir ad alanı öneklerini olacaktır. Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu düğümün adını değiştirmenize izin vermez, DOM başka bir sorun var. Bunun yerine, yeni bir düğüm oluştur ve tüm alt düğümleri, kopyalama özgün düğüm kimliğini kaybetme gerekir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Ayarlanacak sağlayarak bu sorunu önler <xref:System.Xml.Linq.XName> düğümünde özelliği.  
  
## <a name="static-method-support-for-loading-xml"></a>XML yüklenirken statik yöntemi desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML yerine örnek yöntemleri statik yöntemler kullanarak devredebilmenize olanak tanır. Bu, yükleme ve ayrıştırma kolaylaştırır. Daha fazla bilgi için [nasıl yapılır: XML dosyasından (Visual Basic) yükleme](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>DTD yapıları desteğinin kaldırılması  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Daha fazla XML varlıkları ve varlık başvuruları desteği kaldırarak programlama basitleştirir. Varlık Yönetimi karmaşıktır ve nadiren kullanılır. Destek kaldırma performansı artırır ve programlama arabirimi basitleştirir. Olduğunda bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç eklendiğinden, tüm DTD'nin varlıkları genişletilir.  
  
## <a name="support-for-fragments"></a>Parçaları için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için eşdeğer sağlamaz `XmlDocumentFragment` sınıfı. Çoğu durumda, ancak `XmlDocumentFragment` kavram olarak yazılmış bir sorgu sonucunu tarafından işlenebilir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XNode>, veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>XPathNavigator desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için destek sağlar <xref:System.Xml.XPath.XPathNavigator> alanında uzantı yöntemlerini aracılığıyla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı. Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Boşluk ve girinti desteği  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] daha basit, boşluk işleme yerli daha  
  
 Sık karşılaşılan bir senaryodur girintili XML oku, herhangi bir boşluk metin düğümleri (diğer bir deyişle, beyaz boşluk olmayan koruma) olmadan bir bellek içi XML ağacı oluşturmak, bazı XML işlemleri ve XML girintilemeli kaydedin sağlamaktır. Biçimlendirme ile XML serileştirme, yalnızca önemli boşluk XML ağacındaki korunur. Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Başka bir yaygın bir senaryo, okuma ve değiştirme kasıtlı olarak girintili zaten XML sağlamaktır. Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz. İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma beyaz alanı koruma ve XML serileştirme seçildiğinde biçimlendirmeyi devre dışı bırakma bunu yapabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] boşluk olarak depolayan bir <xref:System.Xml.Linq.XText> özelleştirilmiş yerine düğüm, <xref:System.Xml.XmlNodeType.Whitespace> DOM düğüm türü yapar.  
  
## <a name="support-for-annotations"></a>Ek açıklamalar için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleri ek açıklamalarını genişletilebilir bir kümesini destekler. Bu şema bilgileri, bir kullanıcı Arabirimi için bağlı öğe olup olmadığını hakkında bilgi veya diğer tür uygulamaya özgü bilgileri gibi bir öğe hakkında diğer bilgileri izlemek için yararlıdır. Daha fazla bilgi için [LINQ to XML ek açıklamaları](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Şema bilgileri için destek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Uzantı yöntemleri aracılığıyla XSD doğrulaması için destek sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı. Bir XML ağacı bir XSD ile uyumlu olduğunu doğrulayabilirsiniz. XML ağacı sonrası schema doğrulama bilgi kümesi (PSVI) ile doldurabilirsiniz. Daha fazla bilgi için [nasıl yapılır: XSD kullanarak doğrulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
