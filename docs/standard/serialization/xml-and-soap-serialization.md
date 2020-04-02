---
title: XML ve SOAP Serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: dcb2ed1703473be582a12f430d2e051d8a420230
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588370"
---
# <a name="xml-and-soap-serialization"></a>XML ve SOAP serileştirme

XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini ve yöntemlerin parametrelerini ve dönüş değerlerini belirli bir XML Şema tanım dili (XSD) belgesine uygun bir XML akışına dönüştürür (serileştirir). XML serileştirme, depolama veya taşıma için seri biçimine (bu durumda XML) dönüştürülen ortak özelliklere ve alanlara sahip güçlü bir şekilde yazılan sınıflara neden olur.

XML açık bir standart olduğundan, XML akışı platformdan bağımsız olarak gerektiğinde herhangi bir uygulama tarafından işlenebilir. Örneğin, ASP.NET kullanılarak oluşturulan XML <xref:System.Xml.Serialization.XmlSerializer> Web hizmetleri, Internet'teki veya intranet'lerde XML Web hizmeti uygulamaları arasında veri aktaran XML akışları oluşturmak için sınıfı kullanır. Tersine, deserialization böyle bir XML akışı alır ve nesne yi yeniden yapılandırır.

XML serileştirme, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için de kullanılabilir. SOAP, XML kullanarak yordam çağrılarını taşımak için özel olarak tasarlanmış XML tabanlı bir protokoldür.

Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)
- [ASP.NET ve XML Web Hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
