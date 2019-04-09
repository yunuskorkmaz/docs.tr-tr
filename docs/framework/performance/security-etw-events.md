---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134036"
---
# <a name="security-etw-events"></a>Güvenlik ETW Olayları
<a name="top"></a> Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulama sırasında üretilir.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a>StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Tanımlayıcı ad doğrulamasının başlangıcı.|  
|`StrongNameVerificationStop_V1`|182|Tanımlayıcı ad doğrulamasının sonu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|VerificationFlags|Kazanma: UInt32|Doğrulama bayraklar.|  
|ErrorCode|Kazanma: UInt32|HResult hata kodu.|  
|FullyQualifiedAssemblyName|Kazanma: UnicodeString|Tam derleme adı.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a>AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode doğrulama başlangıcı.|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode doğrulama sonu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|VerificationFlags|Kazanma: UInt32|Doğrulama bayraklar.|  
|ErrorCode|Kazanma: UInt32|HResult hata kodu.|  
|ModulePath|Kazanma: UnicodeString|Modül yolu.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
