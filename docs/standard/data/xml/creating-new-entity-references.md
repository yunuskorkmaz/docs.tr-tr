---
title: Yeni Öğe Başvuruları Oluşturma
ms.date: 03/30/2017
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 5d1411b38ee79705cad3375aea1b95265c1ab61a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829329"
---
# <a name="creating-new-entity-references"></a>Yeni Öğe Başvuruları Oluşturma
**CreateEntityReference** yöntemi yeni bir **XmlEntityReference** düğümü oluşturur. XML Belge Nesne Modeli (DOM), başvurulmakta olan varlık adının zaten bildirilip toplanmadığını görmek için bakar. Varsa, **XmlEntityReference** düğümünün alt düğümleri varlık bildirimi düğümünden kopyalanır. Eşleşen bir varlık bildirimi yoksa, bir boş metin düğümü varlık başvurusu düğümünün tek alt öğesi olarak iliştirilir. **XmlEntityReference** düğümünün alt düğümleri diğer düğümlerin kopyaları olduğundan, bu alt düğümler salt okunurdur ve değiştirilemez.  
  
 Düğümler kopyalandığında, Varlık başvurusunun noktasındaki kapsamda bir ad alanı olabilir. Bu ad alanı, oluşturulan herhangi bir öğe veya öznitelik düğümünün yapılandırmasını etkiler.  
  
> [!NOTE]
> DOM, yalnızca **EntityReference** düğümünü belgeye eklediğinizde alt düğümleri **EntityReference** 'a ekler. Yeni oluşturulan **EntityReference** düğümlerinde alt düğüm yok.  
  
 **XmlDataDocument** , **XmlDocument**'ın türetilmiş bir sınıfı olsa da, **XmlDataDocument** varlık başvurularının oluşturulmasını desteklemez. Bunun nedeni, **EntityReference** alt öğelerinden salt okunurdur. Bir **EntityReference** düğümünün alt öğeleri birden fazla bölgeye yayılabilirler. Bu durumda, bir **EntityReference** 'ın parçasını içeren Bölgeyle ilişkili bir satırın parçası salt okunurdur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
