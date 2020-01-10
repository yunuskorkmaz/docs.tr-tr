---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: c443bda8cdc2c6b32760e9dcba8b81a29d81660b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715935"
---
# <a name="security-etw-events"></a>Güvenlik ETW Olayları

Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulaması sırasında oluşturulur.  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Tanımlayıcı ad doğrulaması başlangıcı.|  
|`StrongNameVerificationStop_V1`|182|Tanımlayıcı ad doğrulama sonu.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Doğrulamaları ıationflags|Win: UInt32|Doğrulama bayrakları.|  
|ErrorCode|Win: UInt32|HResult hata kodu.|  
|FullyQualifiedAssemblyName|Win: UnicodeString|Tam nitelikli derleme adı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode doğrulaması başlangıcı.|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode doğrulamasının sonu.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Doğrulamaları ıationflags|Win: UInt32|Doğrulama bayrakları.|  
|ErrorCode|Win: UInt32|HResult hata kodu.|  
|ModulePath|Win: UnicodeString|Modül yolu.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
