---
title: "Birlikte Çalışma ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5670eb910406626096f776d3b4192e2d58d7ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interop-etw-events"></a>Birlikte Çalışma ETW Olayları
<a name="top"></a>Birlikte çalışma olayları Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [ILStubGenerated olayı](#ilstubgenerated_event)  
  
-   [ILStubCacheHit olayı](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>ILStubGenerated olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`InteropKeyword`(0x2000)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|MSIL saplama oluşturuldu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt16|Modül tanıtıcısı.|  
|StubMethodID|Win: UInt64|Saplama yöntem tanımlayıcısı.|  
|StubFlags|Win: UInt64|Saplama bayrakları:<br /><br /> 0x1 - ters birlikte çalışabilirlik.<br /><br /> 0x2 - COM birlikte çalışma.<br /><br /> 0x4 - NGen.exe tarafından oluşturulan saplama.<br /><br /> 0x8 - temsilci.<br /><br /> 0x10 - değişken arrgument.<br /><br /> 0x20 - yönetilmeyen Aranan.|  
|ManagedInteropMethodToken|Win: UInt32|Yönetilen birlikte çalışabilirlik yöntemi için belirteci.|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Yönetilen birlikte çalışabilirlik yöntemi ad alanı.|  
|ManagedInteropMethodName|Win: UnicodeString|Yönetilen birlikte çalışabilirlik yöntemin adı.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Yönetilen birlikte çalışabilirlik yöntemi imzası.|  
|NativeMethodSignature|Win: UnicodeString|Yerel yöntemi imzası.|  
|StubMethodSignature|Win: UnicodeString|Saplama yöntemi imzası.|  
|StubMethodILCode|Win: UnicodeString|Saplama yöntemi MSIL kodu.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`InteropKeyword`(0x2000)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|MSIL önbellek erişilmedi.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt16|Modül tanıtıcısı.|  
|StubMethodID|Win: UInt64|Saplama yöntem tanımlayıcısı.|  
|ManagedInteropMethodToken|Win: UInt32|Yönetilen birlikte çalışabilirlik yöntemi için belirteci.|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Yönetilen birlikte çalışabilirlik yöntemi ad alanı.|  
|ManagedInteropMethodName|Win: UnicodeString|Yönetilen birlikte çalışabilirlik yöntemin adı.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Yönetilen birlikte çalışabilirlik yöntemi imzası.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
