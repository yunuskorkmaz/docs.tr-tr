---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: c5bb7813a680c89eb90f4ccf4ed6f09a831c8095
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262209"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Syntax  
  
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

 XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxarraylength"></a>MaxArrayLength  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 İzin verilen en büyük dizi uzunluğu.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Her okuma için en fazla izin verilen bayt döndürüldü.  
  
### <a name="maxdepth"></a>MaxDepth  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Her okuma için iç içe geçmiş düğüm derinliği üst sınırı.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Tablo adında izin verilen en fazla karakter.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 XML öğesi içeriğinde izin verilen en fazla karakter.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
