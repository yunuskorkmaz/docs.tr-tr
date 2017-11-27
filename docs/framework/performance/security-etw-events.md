---
title: "Güvenlik ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a>Güvenlik ETW Olayları
<a name="top"></a>Güvenlik olayları, güçlü ad doğrulaması ve Authenticode doğrulama sırasında ortaya çıkar.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a>StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`SecurityKeyword`(0x400)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Güçlü ad doğrulaması başlangıcı.|  
|`StrongNameVerificationStop_V1`|182|Güçlü ad doğrulaması sonu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|VerificationFlags|Win: UInt32|Doğrulama bayraklar.|  
|ErrorCode|Win: UInt32|HResult hata kodu.|  
|FullyQualifiedAssemblyName|Win: UnicodeString|Tam nitelikli derleme adı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a>AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`SecurityKeyword`(0x400)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode doğrulama başlangıcı.|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode doğrulama sonu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|VerificationFlags|Win: UInt32|Doğrulama bayraklar.|  
|ErrorCode|Win: UInt32|HResult hata kodu.|  
|ModulePath|Win: UnicodeString|Modül yolu.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
