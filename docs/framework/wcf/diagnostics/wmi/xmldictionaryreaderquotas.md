---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f24865fb0affa7b4516a14fc05b905995826e82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597677"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 XmlDictionaryReaderQuotas sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Dizi uzunluğu izin verilen en fazla.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Her okuma için döndürülen bayt sayısı izin verilen en fazla.  
  
### <a name="maxdepth"></a>MaxDepth  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Her biri için en fazla iç içe geçen düğüm derinliği okuyun.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Tablo adınında izin verilen en fazla karakter.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 XML öğesi içeriğinde izin verilen en fazla karakter.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
