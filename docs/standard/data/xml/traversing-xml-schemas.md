---
title: XML Şemalarını Çapraz Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: dbe02242f9bb8654e3f12d87b6ff6c2aea1f76b1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710121"
---
# <a name="traversing-xml-schemas"></a>XML Şemalarını Çapraz Geçirme

Şema nesne modeli (SOM) API 'sini kullanarak bir XML şemasına geçiş yapmak SOM 'da depolanan öğelere, özniteliklere ve türlere erişim sağlar. SOM 'a yüklenen bir XML şemasının geçişi, SOM API 'SI kullanılarak bir XML şemasını düzenlemenin ilk adımıdır.

## <a name="traversing-an-xml-schema"></a>XML şemasında geçiş yapma

<xref:System.Xml.Schema.XmlSchema> sınıfının aşağıdaki özellikleri, XML şemasına eklenen tüm genel öğelerin koleksiyonuna erişim sağlar.

|Özellik|Koleksiyonda veya dizide depolanan nesne türü|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport> veya <xref:System.Xml.Schema.XmlSchemaRedefine>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (tüm genel düzey öğeler, öznitelikler ve türlere erişim sağlar).|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (şema ad alanına ait olmayan özniteliklere erişim sağlar)|

> [!NOTE]
> Yukarıdaki tabloda listelenen tüm özellikler, <xref:System.Xml.Schema.XmlSchema.Items%2A> özelliği hariç, şema derlenene kadar kullanılamayan-şema-derleme-bilgi kümesi (PSCı) özelliklerdir. <xref:System.Xml.Schema.XmlSchema.Items%2A> özelliği, şemanın erişim için derlenmesinden önce kullanılabilen ve tüm genel düzey öğeleri, öznitelikleri ve türleri düzenlemek için kullanılabilecek bir ön şema derleme özelliğidir.
>
> <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> özelliği, şema ad alanına ait olmayan tüm özniteliklere erişim sağlar. Bu öznitelikler, şema işlemcisi tarafından işlenmez.

Aşağıdaki kod örneği, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan müşteri şemasının geçiş konusunu gösterir. Kod örneği, yukarıda açıklanan koleksiyonlar kullanılarak şemanın geçiş işlemlerini gösterir ve şemadaki tüm öğeleri ve öznitelikleri konsola yazar.

Örnek, aşağıdaki adımlarda müşteri şemasına erişir.

1. Yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesine müşteri şemasını ekler ve sonra derler. Şemayı okuma veya derleme ile karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilcisi tarafından işlenir.

2. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini çağırarak <xref:System.Xml.Schema.XmlSchemaSet> derlenmiş <xref:System.Xml.Schema.XmlSchema> nesnesini alır. Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.

3. Her bir öğenin adını konsola yazarak şema sonrası derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonunun <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> koleksiyonundaki her bir <xref:System.Xml.Schema.XmlSchemaElement> yineler.

4. <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfını kullanarak `Customer` öğenin karmaşık türünü alır.

5. Karmaşık türün herhangi bir özniteliği varsa, her bir <xref:System.Xml.Schema.XmlSchemaAttribute> Numaralandırılacak bir <xref:System.Collections.IDictionaryEnumerator> alır ve adını konsola yazar.

6. <xref:System.Xml.Schema.XmlSchemaSequence> sınıfını kullanarak karmaşık türün sıra parçacığı alır.

7. <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonundaki her bir <xref:System.Xml.Schema.XmlSchemaElement>, her bir alt öğenin adını konsola yazarak yineler.

Aşağıda kodun tamamı verilmiştir.

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> özelliği <xref:System.Xml.Schema.XmlSchemaSimpleType>veya Kullanıcı tanımlı basit bir tür veya karmaşık bir tür ise <xref:System.Xml.Schema.XmlSchemaComplexType> olabilir. W3C XML şeması önerisi içinde tanımlanan yerleşik veri türleri bunlardan biri ise <xref:System.Xml.Schema.XmlSchemaDatatype> de olabilir. Müşteri şemasında, `Customer` öğesinin <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> <xref:System.Xml.Schema.XmlSchemaComplexType>ve `FirstName` ve `LastName` öğeleri <xref:System.Xml.Schema.XmlSchemaSimpleType>.

[XML şeması oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusundaki kod örneği, `Customer` öğesine özniteliği `CustomerId` eklemek için <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> koleksiyonunu kullandı. Bu bir ön şema derleme özelliğidir. Karşılık gelen şema-derleme-bilgi kümesi özelliği, tür türetmede Devralınanlar dahil olmak üzere karmaşık türün tüm özniteliklerini tutan <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> koleksiyonudur.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
