---
title: "Boşluk ve DOM yüklenirken önemli boşluk işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Boşluk ve DOM yüklenirken önemli boşluk işleme
Belge yüklenirken boşluk korumak ve oluşturmak için seçeneği ayarlayabilirsiniz **XmlWhitespace** belge ağacında düğümlerin. Beyaz alan düğümleri oluşturmak için **PreserveWhitespace** özelliğinin true. Özellik ayarlanmışsa **yanlış**, varsayılan, boşluk düğümleri oluşturulmaz. Her zaman önemli boşluk düğümleri korunur, ve **XmlSignificantWhitespace** düğümleri her zaman oluşturulan ayarından bağımsız olarak bu verileri temsil etmek için bellek **PreserveWhitespace** bayrak.  
  
 Belge bir reader yüklerse, ardından ayarıyla **PreserveWhitespace** özelliği bayrak **XmlDocument** sınıfı etkiler oluşturulmasını **XmlWhitespace** düğümler yalnızca **WhitespaceHandling** özelliği **XmlTextReader** ayarlanmazsa **WhitespaceHandling.None**. Bu değeri **WhitespaceHandling** bu bayrağı ayarı üzerinden önceliklidir üzerinde okuyucu özellikte **XmlDocument**. Daha fazla bilgi için **XmlSignificantWhitespace**, bkz: <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
