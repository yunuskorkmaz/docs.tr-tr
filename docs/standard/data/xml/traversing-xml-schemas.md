---
title: XML Şemalarını Çapraz Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: 0951e83c3035de751801d194696eb64993260ef8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289843"
---
# <a name="traversing-xml-schemas"></a>XML Şemalarını Çapraz Geçirme

Şema nesne modeli (SOM) API 'sini kullanarak bir XML şemasına geçiş yapmak SOM 'da depolanan öğelere, özniteliklere ve türlere erişim sağlar. SOM 'a yüklenen bir XML şemasının geçişi, SOM API 'SI kullanılarak bir XML şemasını düzenlemenin ilk adımıdır.

## <a name="traversing-an-xml-schema"></a>XML şemasında geçiş yapma

Sınıfının aşağıdaki özellikleri, <xref:System.Xml.Schema.XmlSchema> XML şemasına eklenen tüm genel öğelerin koleksiyonuna erişim sağlar.

|Özellik|Koleksiyonda veya dizide depolanan nesne türü|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude> , <xref:System.Xml.Schema.XmlSchemaImport> veya<xref:System.Xml.Schema.XmlSchemaRedefine>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject>(tüm genel düzey öğeler, öznitelikler ve türlere erişim sağlar).|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute>(şema ad alanına ait olmayan özniteliklere erişim sağlar)|

> [!NOTE]
> Özelliği hariç, yukarıdaki tabloda listelenen tüm özellikler, <xref:System.Xml.Schema.XmlSchema.Items%2A> şema derlenene kadar kullanılamayan, şema-derleme-bilgi kümesi (PSCı) özelliklerdir. <xref:System.Xml.Schema.XmlSchema.Items%2A>Özelliği, şemanın erişim için derlenmesinden önce kullanılabilen ve tüm genel düzey öğeleri, öznitelikleri ve türleri düzenlemek için kullanılabilecek bir ön şema derleme özelliğidir.
>
> <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>Özelliği, şema ad alanına ait olmayan tüm özniteliklere erişim sağlar. Bu öznitelikler, şema işlemcisi tarafından işlenmez.

Aşağıdaki kod örneği, [XML şemaları oluşturma](building-xml-schemas.md) konusunda oluşturulan müşteri şemasının geçiş konusunu gösterir. Kod örneği, yukarıda açıklanan koleksiyonlar kullanılarak şemanın geçiş işlemlerini gösterir ve şemadaki tüm öğeleri ve öznitelikleri konsola yazar.

Örnek, aşağıdaki adımlarda müşteri şemasına erişir.

1. Müşteri şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesneye ekler ve bunu derler. Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları temsilci tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> .

2. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> Özelliği üzerinde yineleerek derlenmiş nesneyi öğesinden alır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> . Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.

3. Her bir <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> öğenin adını konsola yazan, her bir şema sonrası derleme koleksiyonu koleksiyonundaki her birini yineler.

4. Sınıfını kullanarak öğenin karmaşık türünü alır `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> .

5. Karmaşık türün herhangi bir özniteliği varsa, <xref:System.Collections.IDictionaryEnumerator> her biri için listeleme <xref:System.Xml.Schema.XmlSchemaAttribute> ve adını konsola yazma işlemlerini alır.

6. Sınıfını kullanarak karmaşık türün sıra parçacığı alır <xref:System.Xml.Schema.XmlSchemaSequence> .

7. <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> Her bir alt öğenin adını konsola yazarak koleksiyonda her birinin üzerinde dolaşır.

Aşağıda kodun tamamı verilmiştir.

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType>Özelliği <xref:System.Xml.Schema.XmlSchemaSimpleType> , veya <xref:System.Xml.Schema.XmlSchemaComplexType> Kullanıcı tanımlı basit bir tür ya da karmaşık bir tür olabilir. <xref:System.Xml.Schema.XmlSchemaDatatype>W3C XML şeması önerisi içinde tanımlanan yerleşik veri türleri de olabilir. Müşteri şemasında, <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> `Customer` öğesi ve <xref:System.Xml.Schema.XmlSchemaComplexType> `FirstName` ve `LastName` öğeleri <xref:System.Xml.Schema.XmlSchemaSimpleType> .

[Derleme XML şemaları](building-xml-schemas.md) konusundaki kod örneği, <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> özniteliğini öğesine eklemek için koleksiyonunu kullandı `CustomerId` `Customer` . Bu bir ön şema derleme özelliğidir. Karşılık gelen şema sonrası-derleme-Infoset özelliği, <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> tür türetmede Devralınanlar dahil olmak üzere, karmaşık türün tüm özniteliklerini tutan koleksiyondur.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](building-xml-schemas.md)
- [XML Şemalarını Düzenleme](editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](post-schema-compilation-infoset.md)
