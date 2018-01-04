---
title: "XML şemaları çapraz geçiş yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ceca36b5e988751dff34b5574978aa0ae2da1259
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="traversing-xml-schemas"></a>XML şemaları çapraz geçiş yapma
Şema nesne modeli (SOM) API kullanarak bir XML Şeması geçiş öğeleri, öznitelikleri ve SOM. depolanan türleri erişim sağlar Bir XML çapraz geçiş yapan SOM yüklenen şema ayrıca SOM API kullanarak bir XML şeması düzenleme ilk adımdır.  
  
## <a name="traversing-an-xml-schema"></a>Bir XML Şeması çapraz geçiş yapma  
 Aşağıdaki özellikleri <xref:System.Xml.Schema.XmlSchema> sınıfı için XML Şeması eklenen tüm genel öğeleri koleksiyonu erişim sağlar.  
  
|Özellik|Koleksiyon veya dizisinde depolanan nesne türü|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, veya<xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject>(tüm genel düzey öğeleri, öznitelikleri ve türleri erişim sağlar).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute>(şema ad alanına ait olmayan öznitelikler için erişim sağlayan)|  
  
> [!NOTE]
>  Yukarıdaki tabloda listelenen tüm özellikleri dışında <xref:System.Xml.Schema.XmlSchema.Items%2A> özelliği, şema derlenmiş kadar bulunmayan sonrası-Schema-derleme-bilgi (PSCI) özelliklerdir. <xref:System.Xml.Schema.XmlSchema.Items%2A> Şema erişmek ve tüm genel düzey öğeleri, öznitelikleri ve türleri düzenlemek için derlenmiş önce kullanılabilir bir öncesi schema derleme özelliği bir özelliktir.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Özelliği şema ad alanına ait değil tüm öznitelikleri erişim sağlar. Bu öznitelikler şema işlemcisi tarafından işlenmez.  
  
 Aşağıdaki kod örneğinde oluşturulan müşteri şeması çapraz geçiş yapan gösterilmektedir [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu. Kod örneği, yukarıda açıklanan koleksiyonları kullanarak şema çapraz geçiş yapan gösterir ve tüm öğeleri ve özniteliklerinin şemada konsola yazar.  
  
 Örnek aşağıdaki adımlarda müşteri şeması erişir.  
  
1.  Müşteri şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler. Şema doğrulama uyarıları ve okuma veya şema derleme karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2.  Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Sonrası-Schema-derleme-bilgi (PSCI) özellikleri, şema derlendiğinden erişilebilir.  
  
3.  Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> sonrası-schema-derleme koleksiyonu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> her öğenin adı konsola yazma koleksiyonu.  
  
4.  Karmaşık türü alır `Customer` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.  
  
5.  Karmaşık türü öznitelikleri varsa alır bir <xref:System.Collections.IDictionaryEnumerator> her Numaralandırılacak <xref:System.Xml.Schema.XmlSchemaAttribute> ve adını konsola yazar.  
  
6.  Karmaşık tür kullanmanın dizisi parçacık alır <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.  
  
7.  Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> her alt öğenin adı konsola yazma koleksiyonu.  
  
 Tam kod örnek verilmiştir.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Özelliği <xref:System.Xml.Schema.XmlSchemaSimpleType>, veya <xref:System.Xml.Schema.XmlSchemaComplexType> kullanıcı tanımlı bir basit tür veya karmaşık bir tür ise. Ayrıca olabilir <xref:System.Xml.Schema.XmlSchemaDatatype> W3C XML Şeması öneri tanımlanan yerleşik türleri biri olduğunda. Müşteri şemasında <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> , `Customer` öğesi <xref:System.Xml.Schema.XmlSchemaComplexType>ve `FirstName` ve `LastName` öğeler <xref:System.Xml.Schema.XmlSchemaSimpleType>.  
  
 Aşağıdaki kod örneğinde [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) kullanılan konu <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> öznitelik eklemek için koleksiyon `CustomerId` için `Customer` öğesi. Bu bir öncesi schema derleme özelliğidir. Karşılık gelen sonrası-Schema-derleme-bilgi özelliği <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> karmaşık türde türü türetme devralınan olanlar da dahil olmak üzere tüm öznitelikleri tutan koleksiyonu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
