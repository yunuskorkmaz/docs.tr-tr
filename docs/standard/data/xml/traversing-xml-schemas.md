---
title: XML Şemalarını Çapraz Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fd81a7eaf299217a17cd8051d77cd7a3695441e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939458"
---
# <a name="traversing-xml-schemas"></a>XML Şemalarını Çapraz Geçirme
Şema nesne modeli (SOM) API 'sini kullanarak bir XML şemasına geçiş yapmak SOM 'da depolanan öğelere, özniteliklere ve türlere erişim sağlar. SOM 'a yüklenen bir XML şemasının geçişi, SOM API 'SI kullanılarak bir XML şemasını düzenlemenin ilk adımıdır.  
  
## <a name="traversing-an-xml-schema"></a>XML şemasında geçiş yapma  
 <xref:System.Xml.Schema.XmlSchema> Sınıfının aşağıdaki özellikleri, XML şemasına eklenen tüm genel öğelerin koleksiyonuna erişim sağlar.  
  
|Özellik|Koleksiyonda veya dizide depolanan nesne türü|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>,veya <xref:System.Xml.Schema.XmlSchemaImport><xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject>(tüm genel düzey öğeler, öznitelikler ve türlere erişim sağlar).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute>(şema ad alanına ait olmayan özniteliklere erişim sağlar)|  
  
> [!NOTE]
> <xref:System.Xml.Schema.XmlSchema.Items%2A> Özelliği hariç, yukarıdaki tabloda listelenen tüm özellikler, şema derlenene kadar kullanılamayan, şema-derleme-bilgi kümesi (pSCI) özelliklerdir. <xref:System.Xml.Schema.XmlSchema.Items%2A> Özelliği, şemanın erişim için derlenmesinden önce kullanılabilen ve tüm genel düzey öğeleri, öznitelikleri ve türleri düzenlemek için kullanılabilecek bir ön şema derleme özelliğidir.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Özelliği, şema ad alanına ait olmayan tüm özniteliklere erişim sağlar. Bu öznitelikler, şema işlemcisi tarafından işlenmez.  
  
 Aşağıdaki kod örneği, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan müşteri şemasının geçiş konusunu gösterir. Kod örneği, yukarıda açıklanan koleksiyonlar kullanılarak şemanın geçiş işlemlerini gösterir ve şemadaki tüm öğeleri ve öznitelikleri konsola yazar.  
  
 Örnek, aşağıdaki adımlarda müşteri şemasına erişir.  
  
1. Müşteri şemasını yeni <xref:System.Xml.Schema.XmlSchemaSet> bir nesneye ekler ve bunu derler. Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilci tarafından işlenir.  
  
2. Özelliği üzerinde <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchema> yineleerekderlenmişnesneyiöğesindenalır<xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> . Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.  
  
3. Her bir öğenin <xref:System.Xml.Schema.XmlSchemaElement> adını konsola <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> yazan, her bir şema sonrası derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu koleksiyonundaki her birini yineler.  
  
4. Sınıfını kullanarak öğenin`Customer` karmaşık türünü alır. <xref:System.Xml.Schema.XmlSchemaComplexType>  
  
5. Karmaşık türün herhangi bir <xref:System.Collections.IDictionaryEnumerator> özniteliği varsa, her biri <xref:System.Xml.Schema.XmlSchemaAttribute> için listeleme ve adını konsola yazma işlemlerini alır.  
  
6. <xref:System.Xml.Schema.XmlSchemaSequence> Sınıfını kullanarak karmaşık türün sıra parçacığı alır.  
  
7. Her bir alt <xref:System.Xml.Schema.XmlSchemaElement> öğenin adını <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> konsola yazarak koleksiyonda her birinin üzerinde dolaşır.  
  
 Aşağıda kodun tamamı verilmiştir.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Özelliği ,<xref:System.Xml.Schema.XmlSchemaSimpleType>veya Kullanıcıtanımlıbasitbir<xref:System.Xml.Schema.XmlSchemaComplexType> tür ya da karmaşık bir tür olabilir. W3C XML şeması önerisi <xref:System.Xml.Schema.XmlSchemaDatatype> içinde tanımlanan yerleşik veri türleri de olabilir. Müşteri <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> şemasında `Customer` , öğesi<xref:System.Xml.Schema.XmlSchemaComplexType>ve ve`LastName`öğeleri . <xref:System.Xml.Schema.XmlSchemaSimpleType> `FirstName`  
  
 [Derleme XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konusundaki kod örneği, özniteliğini <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> `CustomerId` `Customer` öğesine eklemek için koleksiyonunu kullandı. Bu bir ön şema derleme özelliğidir. Karşılık gelen şema sonrası-derleme-Infoset özelliği, tür türetmede Devralınanlar dahil olmak üzere, karmaşık türün tüm özniteliklerini tutan <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> koleksiyondur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
