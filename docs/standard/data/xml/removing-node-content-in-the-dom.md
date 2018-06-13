---
title: DOM düğümü içeriği kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4acbdb53b20c10362385b468c2eb13ab9b17eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568517"
---
# <a name="removing-node-content-in-the-dom"></a>DOM düğümü içeriği kaldırma
Devralınan düğüm türleri için <xref:System.Xml.XmlCharacterData>, hangi <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, ve <xref:System.Xml.XmlSignificantWhitespace> düğüm türlerini kullanarak karakterlerini kaldırabilirsiniz <xref:System.Xml.XmlCharacterData.DeleteData%2A> aralığını kaldırır yöntemi karakter düğümünden. İçerik tamamen kaldırmak istiyorsanız, içeriğin bulunduğu düğümü kaldırın. Düğüm tutmak istediğiniz, ancak içeriğin yanlış olduğundan, içeriği değiştirin. Bir düğümün içeriğini değiştirme hakkında daha fazla bilgi için bkz: [değiştirme düğümleri, içerik ve bir XML belgesi değerleri](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
