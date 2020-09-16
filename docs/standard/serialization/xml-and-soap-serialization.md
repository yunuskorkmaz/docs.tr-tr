---
title: XML ve SOAP Serileştirme
description: Bu genel bakış, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için kullanılabilen XML serileştirmesini açıklar.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: f7ad7732f929ac3599942c5440b173ea226cca87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544992"
---
# <a name="xml-and-soap-serialization"></a>XML ve SOAP serileştirmesi

XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini, parametreleri ve dönüş değerlerini belirli bir XML şeması tanım dili (XSD) belgesine uygun bir XML akışına dönüştürür (seri hale getirir). XML serileştirme, genel özellikler ve depolama ya da taşıma için bir seri biçimine (Bu örnekte XML) dönüştürülen alanları kesin olarak belirlenmiş sınıflarla sonuçlanır.

XML açık bir standart olduğu için XML akışı, platformdan bağımsız olarak, gerektiğinde herhangi bir uygulama tarafından işlenebilir. Örneğin, ASP.NET kullanılarak oluşturulan XML Web Hizmetleri, XML <xref:System.Xml.Serialization.XmlSerializer> Web hizmeti uygulamaları arasında verileri Internet üzerinden veya intranetlerde GEÇIREN XML akışları oluşturmak için sınıfını kullanır. Buna karşılık, seri durumdan çıkarma böyle bir XML akışı alır ve nesneyi yeniden oluşturur.

XML serileştirme Ayrıca, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için de kullanılabilir. SOAP, özellikle XML kullanan yordam çağrılarını aktarmak için tasarlanan XML tabanlı bir protokoldür.

Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- [ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
