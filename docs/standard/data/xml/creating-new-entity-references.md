---
title: Yeni öğe başvuruları oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fdbcdbff64bcd91c80fbeaec0c41982b68d98f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203388"
---
# <a name="creating-new-entity-references"></a>Yeni öğe başvuruları oluşturma
**CreateEntityReference** yöntemi yeni bir oluşturur **XmlEntityReference** düğümü. Başvurulan varlık adı zaten bildirildi, XML belge nesne modeli (DOM) bakar. Varsa, alt düğümleri **XmlEntityReference** düğüm varlık bildirimi düğümden kopyalanır. Eşleşen hiçbir varlık bildirimi varsa, bir boş metin düğümü tek varlık referans düğümün alt öğesi eklenir. Çünkü alt düğümlerin **XmlEntityReference** düğümü diğer düğümlere kopyalarını, bu alt düğümlerin salt okunurdur ve değiştirilemez.  
  
 Düğümleri kopyalandığında olabilir bir ad alanı kapsamında noktasında varlık başvurusu. Bu ad alanı yapılandırmasını oluşturulan herhangi bir öğe veya öznitelik düğümleri etkiler.  
  
> [!NOTE]
>  DOM alt düğüm ekler **EntityReference** eklediğinizde yalnızca **EntityReference** belge düğümü. Yeni oluşturulan **EntityReference** düğümünüz alt düğüm yok.  
  
 Olsa da **XmlDataDocument** türetilmiş bir sınıf **XmlDocument**, **XmlDataDocument** varlık başvuruları oluşturulmasını desteklemiyor. Bunun nedeni, **EntityReference** alt öğesi olan salt okunur. Alt bir **EntityReference** düğüm, birden fazla bölgeye yayılabilir. Bu durumda, bir satırın bir parçası bir bölümünü içeren bir bölge ile ilişkili bir **EntityReference** salt okunur olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
