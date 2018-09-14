---
title: XML şemalarını çapraz geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f2da2849bdf9ce922a89bf25e1758d868ee5ea8
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527798"
---
# <a name="traversing-xml-schemas"></a>XML şemalarını çapraz geçirme
Şema nesne modeli (SOM) API kullanarak bir XML Şeması geçiş öğeleri, öznitelikleri ve SOM. içinde depolanan türleri erişim sağlar Bir XML geçiş SOM yüklenen şema ayrıca SOM API'sini kullanarak bir XML şeması düzenleme ilk adımdır.  
  
## <a name="traversing-an-xml-schema"></a>Bir XML Şeması geçiş yapma  
 Aşağıdaki özellikleri <xref:System.Xml.Schema.XmlSchema> sınıfı için XML Şeması eklenen tüm genel öğeler koleksiyonu erişim sağlar.  
  
|Özellik|Koleksiyon veya dizi depolanan nesne türü|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, veya <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (tüm genel düzeyi öğeler, öznitelikler ve türler erişim sağlar).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (şema ad alanına ait olmayan öznitelikleri erişim sağlar)|  
  
> [!NOTE]
>  Yukarıdaki tabloda listelenen tüm özellikler dışında <xref:System.Xml.Schema.XmlSchema.Items%2A> özelliği, şema derlenen kadar bulunmayan sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özelliklerdir. <xref:System.Xml.Schema.XmlSchema.Items%2A> Şema erişmek ve tüm genel düzeyi öğeler, öznitelikler ve türler düzenlemek için derlenmiş önce kullanılabilir bir öncesi schema derleme özelliği bir özelliktir.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Özelliği, şema ad alanına ait olmayan tüm öznitelikler erişim sağlar. Bu öznitelikler şema işlemcisi tarafından işlenmez.  
  
 Aşağıdaki kod örneği, oluşturulan müşteri şema geçiş gösterir [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu. Kod örneği, yukarıda açıklanan koleksiyonları kullanarak şema geçiş gösterir ve tüm öğeleri ve öznitelikleri şemada konsola yazar.  
  
 Aşağıdaki adımlarda, müşteri şema örnek erişir.  
  
1.  Yeni bir müşteri şema ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler. Herhangi bir şema doğrulama uyarıları ve okuma veya şema derleme hatalarla karşılaşıldı işlenir <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2.  Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinden <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Şema derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.  
  
3.  Her yinelenir <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> sonrası-schema-derleme koleksiyonu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu her öğenin adını konsola yazar.  
  
4.  Karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.  
  
5.  Karmaşık tür herhangi bir özniteliği varsa, alır bir <xref:System.Collections.IDictionaryEnumerator> her Numaralandırılacak <xref:System.Xml.Schema.XmlSchemaAttribute> ve adını konsola yazar.  
  
6.  Karmaşık tür kullanarak dizisi parçacık alır <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.  
  
7.  Her yinelenir <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyon her alt öğenin adını konsola yazar.  
  
 Tam kod örneği verilmiştir.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Özelliği <xref:System.Xml.Schema.XmlSchemaSimpleType>, veya <xref:System.Xml.Schema.XmlSchemaComplexType> kullanıcı tanımlı bir basit türü veya karmaşık bir tür ise. Ayrıca olabilir <xref:System.Xml.Schema.XmlSchemaDatatype> W3C XML Şeması öneri de tanımlanan yerleşik veri türleri biri ise. Müşteri şemasında <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> , `Customer` öğesi <xref:System.Xml.Schema.XmlSchemaComplexType>ve `FirstName` ve `LastName` öğeler <xref:System.Xml.Schema.XmlSchemaSimpleType>.  
  
 Aşağıdaki kod örneğinde [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) kullanılan konu <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> öznitelik eklemek için koleksiyon `CustomerId` için `Customer` öğesi. Bu bir öncesi schema derleme özelliğidir. Karşılık gelen sonrası-Schema-derleme-bilgi özelliği <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> koleksiyonunun karmaşık türün tür türetme devralınır olanlar da dahil olmak üzere tüm özniteliklerini içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
