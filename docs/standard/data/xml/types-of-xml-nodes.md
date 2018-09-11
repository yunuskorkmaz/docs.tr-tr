---
title: XML düğüm türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623583f16c23b55c16f648fedcd039ca36f73b1f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261963"
---
# <a name="types-of-xml-nodes"></a>XML düğüm türleri
Bir XML belgesi bir ağaç düğümleri olarak belleğe okunduğunda, düğüm için düğüm türleri düğümleri oluşturulduğunda verdi. XML belge nesne modeli (DOM), düğüm türleri, World Wide Web Consortium (W3C) tarafından belirlenen çeşitli türlerde olan ve DOM yapısı modeli 1.1.1 bölümünde listelenir. Aşağıdaki tabloda, bu düğüm türü ve her kısa bir açıklaması için atanan nesne düğüm türleri listelenmektedir.  
  
|DOM düğüm türü|Nesne|Açıklama|  
|-------------------|------------|-----------------|  
|Belge|<xref:System.Xml.XmlDocument>|Ağaçtaki tüm düğümleri kapsayıcı. Olarak da bilinir, her zaman aynı kök öğesi değil belge kökü olan.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Bir veya daha fazla düğüm bir ağaç yapısı olmadan içeren geçici bir paketi.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Temsil eden `<!DOCTYPE…>` düğümü.|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Genişletilmiş varlık başvurusu metni temsil eder.|  
|Öğe|<xref:System.Xml.XmlElement>|Bir öğe düğümü temsil eder.|  
|attr|<xref:System.Xml.XmlAttribute>|Bir öğenin bir özniteliktir.|  
|İnstruction|<xref:System.Xml.XmlProcessingInstruction>|Bir işlem yönergesi düğümü ' dir.|  
|Yorum|<xref:System.Xml.XmlComment>|Bir açıklama düğümü.|  
|Metin|<xref:System.Xml.XmlText>|Bir öğe veya öznitelik ait olan metin.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|CDATA temsil eder.|  
|Varlık|<xref:System.Xml.XmlEntity>|Temsil eden `<!ENTITY…>` bildirimlerinde XML belge, bir iç belge türü tanımı (DTD'nin) alt ya da DTD'ler ve parametre varlık.|  
|Gösterim|<xref:System.Xml.XmlNotation>|DTD'nin içinde bildirilen bir yazım biçimi temsil eder.|  
  
 Olsa bile bir öznitelik (*attr*) listelenen W3C DOM düzey 1 bölümüne 1.2 temel arabirimlerde bir düğüm olarak, herhangi bir öğe düğümün alt öğesi olarak kabul edilmez.  
  
 Microsoft .NET Framework nesne modeli kullanmak için kullanılabilir ancak W3C tarafından tanımlanmayan ek düğüm türleri aşağıdaki tabloda gösterilmektedir **XmlNodeType** numaralandırma. Bu nedenle, bu düğüm türü için eşleşen DOM düğüm türü sütun yok.  
  
|Düğüm türü|Açıklama|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Bildirim düğümü temsil eden `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Önemli boşluk, boşluk içerikte olduğu temsil eder.|  
|<xref:System.Xml.XmlWhitespace>|Boşluk bir öğenin içeriğini temsil eder.|  
|EndElement|Ne zaman iade **XmlReader** sonuna bir öğe alır.<br /><br /> Örnek XML:  **\< /item >**<br /><br /> Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Ne zaman iade **XmlReader** varlık değiştirme için bir arama sonucunda sonuna alır <xref:System.Xml.XmlReader.ResolveEntity%2A>. Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeType>.|  
  
 XML okur ve düğüm ve içeriği hakkındaki bilgileri yazdırmak için düğüm türleri üzerinde büyük bir yapı kullanan bir kod örneği görüntülemek için bkz: <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Düğüm türleri ve denk nesneleri adlarının nesne hiyerarşisi hakkında daha fazla bilgi için bkz. [XML belge nesne modeli (DOM) hiyerarşisi](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Düğüm ağaçta oluşturulan nesneleri hakkında daha fazla bilgi için bkz. [XML verilerine nesne hiyerarşisi eşleme](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
