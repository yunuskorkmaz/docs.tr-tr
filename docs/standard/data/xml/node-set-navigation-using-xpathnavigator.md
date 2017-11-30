---
title: "Düğüm kümesi Gezinti XPathNavigator kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Düğüm kümesi Gezinti XPathNavigator kullanma
Düğümler üzerinden gidebilirsiniz bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> düğüm kümesi gezinti yöntemlerini kullanarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı. Tüm düğümleri veya seçili bir seçim yöntemlerini biri tarafından döndürülen düğümleri kümesi üzerinden gidebilirsiniz <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
## <a name="element-node-set-navigation"></a>Öğe düğüm kümesi gezinme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı öğe düğümlerinin gezinmek için kullanılan birkaç yöntem sağlar. Aşağıdaki tabloda kullanılabilir Gezinti yöntemleri ve nasıl hareket açıklaması gösterir; Bu öznitelik ve ad alanı düğümleri gitmek için kullanılan yöntemler içermez.  
  
 Düğümler seçme hakkında daha fazla bilgi için bir <xref:System.Xml.XPath.XPathNavigator> nesne için bkz: [seçme, Evaluating ve eşleşen XML XPathNavigator kullanarak verileri](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Öznitelik ve ad alanı düğümleri gezinme hakkında daha fazla bilgi için bkz: [özniteliği ve Namespace düğümü Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> aynı konumuna <xref:System.Xml.XPath.XPathNavigator> belirtilen.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün bir alt düğümü.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk eşdüzey düğümü.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk alt düğümü.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> belge sırada belirtilen öğeye.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> türü bir özniteliğin sahip düğümüne `ID` eşleşen bir değeri ile verilen <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün sonraki eşdüzey düğümü.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün üst düğüme.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün önceki Eşdüzey Düğüm için.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> XML belgesinin kök düğüme.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Yorumlar ve işleme yönergesi düğümü gezinme  
 Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıfı yöntemleri yorumları taşıma veya bir XML belgesi diğer düğümlerden yönergeleri işlemek için geçerli.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [XPathNavigator kullanarak XML veri ayıklamak](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
