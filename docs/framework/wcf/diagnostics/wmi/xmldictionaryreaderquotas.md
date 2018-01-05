---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a3afb9b8cfede60c773d146f4d1728d7fe02b75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 XmlDictionaryReaderQuotas sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 XmlDictionaryReaderQuotas sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Dizi uzunluğu izin verilen en fazla.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Her okuma için döndürülen bayt izin verilen en fazla.  
  
### <a name="maxdepth"></a>MaxDepth  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Her biri için en fazla iç içe geçen düğüm derinliği okuyun.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Bir tablo adı izin verilen maksimum karakter.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 XML öğesi içeriği izin verilen maksimum karakter.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
