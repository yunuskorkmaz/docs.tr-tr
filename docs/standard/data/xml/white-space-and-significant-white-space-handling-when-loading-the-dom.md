---
title: Boşluk ve DOM yüklenirken önemli boşluk işleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8e2279023029b5047cc7d9b4d0d97ac1f21e3f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569076"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Boşluk ve DOM yüklenirken önemli boşluk işleme
Belge yüklenirken boşluk korumak ve oluşturmak için seçeneği ayarlayabilirsiniz **XmlWhitespace** belge ağacında düğümlerin. Beyaz alan düğümleri oluşturmak için **PreserveWhitespace** özelliğinin true. Özellik ayarlanmışsa **yanlış**, varsayılan, boşluk düğümleri oluşturulmaz. Her zaman önemli boşluk düğümleri korunur, ve **XmlSignificantWhitespace** düğümleri her zaman oluşturulan ayarından bağımsız olarak bu verileri temsil etmek için bellek **PreserveWhitespace** bayrak.  
  
 Belge bir reader yüklerse, ardından ayarıyla **PreserveWhitespace** özelliği bayrak **XmlDocument** sınıfı etkiler oluşturulmasını **XmlWhitespace** düğümler yalnızca **WhitespaceHandling** özelliği **XmlTextReader** ayarlanmazsa **WhitespaceHandling.None**. Bu değeri **WhitespaceHandling** bu bayrağı ayarı üzerinden önceliklidir üzerinde okuyucu özellikte **XmlDocument**. Daha fazla bilgi için **XmlSignificantWhitespace**, bkz: <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
