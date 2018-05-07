---
title: XML düğüm türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f62a113865a481276c371f2fce55a5d9486eb00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="types-of-xml-nodes"></a>XML düğüm türleri
Bir XML belgesi düğümlerinin ağaç olarak belleğe okurken düğüm türleri düğümleri için düğümleri oluşturulduğunda vermiştir. XML belge nesne modeli (DOM) düğüm türleri, World Wide Web Konsorsiyumu (W3C) tarafından belirlenen çeşitli türlerde sahiptir ve DOM yapısı modeli 1.1.1 bölümünde listelenir. Aşağıdaki tabloda, bu düğüm türü ve her kısa bir açıklaması için atanmış nesnesini düğüm türleri listelenmektedir.  
  
|DOM düğüm türü|Nesne|Açıklama|  
|-------------------|------------|-----------------|  
|Belge|<xref:System.Xml.XmlDocument>|Ağaçtaki tüm düğümler kapsayıcı. Bu da her zaman aynı kök öğesi değil belge kökü denir.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Bir veya daha fazla düğüm herhangi bir ağaç yapısını olmadan içeren geçici bir paketi.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Temsil eden `<!DOCTYPE…>` düğümü.|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Genişletilmiş varlık başvuru metni temsil eder.|  
|Öğe|<xref:System.Xml.XmlElement>|Bir öğe düğümü temsil eder.|  
|Attr|<xref:System.Xml.XmlAttribute>|Bir öğenin bir özniteliktir.|  
|İnstruction|<xref:System.Xml.XmlProcessingInstruction>|Yönerge işleme bir düğümdür.|  
|Yorum|<xref:System.Xml.XmlComment>|Bir açıklama düğümü.|  
|Metin|<xref:System.Xml.XmlText>|Bir öğe veya öznitelik ait olan metin.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|CDATA temsil eder.|  
|Varlık|<xref:System.Xml.XmlEntity>|Temsil eden `<!ENTITY…>` XML bildirimlerinde belge, bir iç belge türü tanımı (DTD) alt ya da dış DTD ve parametre varlıklar.|  
|Gösterimi|<xref:System.Xml.XmlNotation>|DTD içinde bildirilen bir gösterim temsil eder.|  
  
 Bir öznitelik bile olsa (*attr*) listelenen W3C DOM düzey 1 Bölüm 1.2 temel arabirimlerde bir düğüm olarak, bunu herhangi bir öğe düğümün bir alt olarak kabul edilmez.  
  
 Microsoft .NET Framework nesne modeli kullanmak için kullanılabilir ancak W3C tarafından tanımlanan değil ek düğüm türleri aşağıdaki tabloda gösterilmektedir **XmlNodeType** numaralandırmalar. Bu nedenle, bu düğüm türleri için eşleşen DOM düğüm türü sütun yok.  
  
|Düğüm türü|Açıklama|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Bildirim düğümünü temsil eder `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Önemli boşluk, karışık içeriği boşluk olduğu temsil eder.|  
|<xref:System.Xml.XmlWhitespace>|Bir öğenin içeriğini beyaz alanı temsil eder.|  
|EndElement|Ne zaman döndürülen **XmlReader** bir öğenin sonunu alır.<br /><br /> XML örneği:  **\< /Madde >**<br /><br /> Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Ne zaman döndürülen **XmlReader** yapılan bir çağrı sonucunda varlık değiştirme sonuna alır <xref:System.Xml.XmlReader.ResolveEntity%2A>. Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeType>.|  
  
 XML'de okuyan ve düğüm ve içeriği hakkındaki bilgileri yazdırmak için düğüm türleri üzerinde bir servis talebi yapısı kullanır. bir kod örneği görüntülemek için bkz: <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Düğüm türlerini ve bunların eşdeğer nesne adı, nesne hiyerarşisini üzerinde daha fazla bilgi için bkz: [XML belge nesne modeli (DOM) hiyerarşisi](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Düğüm ağaçta oluşturulan nesneler hakkında daha fazla bilgi için bkz: [nesne hiyerarşisi XML verileri eşleştirmesi](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
