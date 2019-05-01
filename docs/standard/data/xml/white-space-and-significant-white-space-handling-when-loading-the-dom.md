---
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d9bbb14320b84a6d417c5c28026b169092de219
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799339"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
Belge yüklenirken bölünemez boşluğu koruyacak ve oluşturmak için seçeneği ayarlayabilirsiniz **XmlWhitespace** belge ağacında düğümleri. Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliği true. Özellik ayarlanmışsa **false**, varsayılan değer olan, boşluk düğümleri oluşturulmaz. Her zaman önemli boşluk düğümleri korunur, ve **XmlSignificantWhitespace** düğümleri her zaman bellek ayarından bağımsız olarak bu verileri temsil etmek için oluşturulan **PreserveWhitespace** bayrak.  
  
 Belge okuyucudan yüklenirse, ardından ayarıyla **PreserveWhitespace** özellik bayrağını **XmlDocument** sınıfı etkiler oluşturulmasını **XmlWhitespace** düğümleri yalnızca **WhitespaceHandling** özelliği **XmlTextReader** ayarlı değil **WhitespaceHandling.None**. Bu değeri **WhitespaceHandling** bu bayrağının ayarını üzerinde önceliklidir üzerinde okuyucu özelliği **XmlDocument**. Daha fazla bilgi için **XmlSignificantWhitespace**, bkz: <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
