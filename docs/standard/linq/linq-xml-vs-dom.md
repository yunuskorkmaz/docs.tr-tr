---
title: LINQ to XML ile DOM Karşılaştırması
description: LINQ to XML ve DOM arasında önemli farklılıklar vardır. LINQ to XML, oluşturdukları XML ağaçlarının yapısını daha iyi gösteren işlevsel oluşturma ve XML sabit değerlerini destekler.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553325"
---
# <a name="linq-to-xml-vs-dom"></a>LINQ to XML ile DOM Karşılaştırması

Bu makalede, LINQ to XML ve geçerli önceden baskın XML programlama API 'SI, W3C Belge Nesne Modeli (DOM) arasındaki bazı önemli farklılıklar açıklanmaktadır.

## <a name="new-ways-to-construct-xml-trees"></a>XML ağaçları oluşturmak için yeni yollar

W3C DOM 'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir deyişle, bir belge oluşturur, öğeler oluşturur ve sonra öğeleri belgeye eklersiniz.

Örneğin, aşağıdaki örnek, DOM 'ın Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için tipik bir yol kullanır <xref:System.Xml.XmlDocument> .

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

Bu kodlama stili, XML ağacının yapısını gizler. LINQ to XML, yapıyı daha iyi gösteren alternatif bir yaklaşım olan *işlevsel oluşturma*da destekler. Bu yaklaşım <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucularla yapılabilir. Visual Basic, XML değişmez değerleri ile de yapılabilir. Bu örnekte, işlevsel oluşturma kullanılarak aynı XML ağacının oluşturulması gösterilmektedir:

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

XML ağacını oluşturmak için kodun girintilendiği, temel alınan XML 'nin yapısını gösterir. Visual Basic sürümü XML sabit değerlerini kullanır.

Daha fazla bilgi için bkz. [xml ağaçları](functional-construction.md).

## <a name="work-directly-with-xml-elements"></a>Doğrudan XML öğeleriyle çalışma

XML ile programlama yaptığınızda, birincil odağınızı genellikle XML öğelerinde ve belki de özniteliklerde bulabilirsiniz. LINQ to XML, doğrudan XML öğeleri ve özniteliklerle çalışabilirsiniz. Örneğin, şunları yapabilirsiniz:

- Bir belge nesnesi kullanmadan XML öğeleri oluşturun. Bu, XML ağaçlarının parçaları ile çalışmanız gerektiğinde programlamayı basitleştirir.
- `T:System.Xml.Linq.XElement`Nesneleri doğrudan BIR XML dosyasından yükleyin.
- `T:System.Xml.Linq.XElement`Nesneleri bir dosyaya veya akışa serileştirme.

Bu, XML belgesinin XML ağacı için bir mantıksal kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın. DOM 'da, öğeler ve öznitelikler dahil XML düğümlerinin bir XML belgesi bağlamında oluşturulması gerekir. DOM 'da bir ad öğesi oluşturmak için bir kod parçası aşağıda verilmiştir:

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

Birden çok belge genelinde bir öğe kullanmak istiyorsanız düğümleri belgeler arasında içeri aktarmanız gerekir. LINQ to XML bu karmaşıklık katmanını önler.

LINQ to XML kullanırken, <xref:System.Xml.Linq.XDocument> yalnızca belgenin kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız sınıfını kullanırsınız.

## <a name="simplified-handling-of-names-and-namespaces"></a>Adları ve ad alanlarını Basitleştirilmiş olarak işleme

Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır. LINQ to XML, ad alanı önekleriyle uğraşmak için gereksinimi ortadan kaldırarak adları ve ad alanlarını basitleştirir. Ad alanı öneklerini denetlemek istiyorsanız, kullanabilirsiniz. Ancak ad alanı öneklerini açıkça denetistemediğinize karar verirseniz LINQ to XML, gerektiğinde serileştirme sırasında ad alanı öneklerini atayacaktır veya varsayılan ad alanlarını kullanarak serileştirilir. Varsayılan ad alanları kullanılırsa, sonuçta elde edilen belgede ad alanı önekleri olmayacaktır. Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

DOM ile ilgili başka bir sorun da bir düğümün adını değiştirmenize izin vermez. Bunun yerine, yeni bir düğüm oluşturmanız ve tüm alt düğümleri buna kopyalamanız ve özgün düğüm kimliğini kaybetmemeniz gerekir. LINQ to XML, bir düğümdeki özelliği ayarlamanıza olanak tanıyarak bu sorunu önler <xref:System.Xml.Linq.XName> .

## <a name="static-method-support-for-loading-xml"></a>XML yükleme için statik yöntem desteği

LINQ to XML, örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenize imkan tanır. Bu, yükleme ve ayrıştırma işlemlerini basitleştirir. Daha fazla bilgi için bkz. [XML dosyasından XML yükleme](load-xml-file.md).

## <a name="removal-of-support-for-dtd-constructs"></a>DTD yapıları için desteği kaldırma

LINQ to XML varlıklar ve varlık başvuruları desteğini kaldırarak XML programlamayı basitleştirir. Varlıkların yönetimi karmaşıktır ve nadiren kullanılır. Desteğinin kaldırılması performansı artırır ve programlama arabirimini basitleştirir. LINQ to XML ağaç doldurulduktan sonra tüm DTD varlıkları genişletilir.

## <a name="support-for-fragments"></a>Parçalar için destek

LINQ to XML sınıfı için eşdeğer değildir `XmlDocumentFragment` . Ancak çoğu durumda `XmlDocumentFragment` kavram, <xref:System.Collections.Generic.IEnumerable%601> veya ' nin yazıldığı bir sorgunun sonucu tarafından işlenebilir <xref:System.Xml.Linq.XNode> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> .

## <a name="support-for-xpathnavigator"></a>XPathNavigator desteği

LINQ to XML <xref:System.Xml.XPath.XPathNavigator> ad alanındaki genişletme yöntemlerine yönelik destek sağlar <xref:System.Xml.XPath?displayProperty=nameWithType> . Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.

## <a name="support-for-white-space-and-indentation"></a>Boşluk ve girintileme desteği

LINQ to XML, DOM 'dan daha fazla boşluk işler.

Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (yani, beyaz boşluğu korumadan), XML üzerinde bazı işlemler yapın ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu, LINQ to XML için varsayılan davranıştır.

Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. LINQ to XML, bunu şu şekilde yapabilirsiniz:

- XML 'i yüklediğinizde veya ayrıştırdığınızda boşluk koruma.
- XML 'yi seri hale alırken biçimlendirmeyi devre dışı bırakma.

LINQ to XML, <xref:System.Xml.Linq.XText> Dom gibi özelleştirilmiş bir düğüm türüne sahip olmak yerine, boşluk olarak bir düğüm olarak depolar <xref:System.Xml.XmlNodeType.Whitespace> .

## <a name="support-for-annotations"></a>Ek açıklamalar için destek

LINQ to XML öğeleri, genişletilebilir bir ek açıklama kümesini destekler. Bu, şema bilgileri, öğenin bir kullanıcı arabirimine bağlanıp bağlanmayacağı veya başka bir uygulamaya özgü bilgi türü gibi bir öğeyle ilgili çeşitli bilgileri izlemek için yararlıdır. Daha fazla bilgi için bkz. [LINQ to XML ek açıklamaları](linq-xml-annotations.md).

## <a name="support-for-schema-information"></a>Şema bilgileri için destek

LINQ to XML, ad alanındaki genişletme yöntemleri aracılığıyla XSD doğrulaması için destek sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> . Bir XML ağacının bir XSD ile uyumlu olduğunu doğrulayabilirsiniz. XML ağacını şema-doğrulama sonrası bilgi kümesi (PSVı) ile doldurabilirsiniz. Daha fazla bilgi için bkz. [XSD kullanarak doğrulama](validate-xsd.md) ve <xref:System.Xml.Schema.Extensions> .

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML genel bakış](linq-xml-overview.md)
