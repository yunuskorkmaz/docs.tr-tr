---
title: Birlikte Çalışma ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fb458958f55a3f9fb2b79d87f0ee32d4a028e457
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611780"
---
# <a name="interop-etw-events"></a>Birlikte Çalışma ETW Olayları
<a name="top"></a> Birlikte çalışma olayları, Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi toplayın.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [ILStubGenerated olay](#ilstubgenerated_event)  
  
-   [ILStubCacheHit olay](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>ILStubGenerated olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|MSIL saplama oluşturuldu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Kazanma: UInt16|Modül tanımlayıcısı.|  
|StubMethodID|Kazanma: UInt64|Saplama yöntem tanımlayıcısı.|  
|StubFlags|Kazanma: UInt64|Saptama için bayraklar:<br /><br /> 0x1 - ters birlikte çalışma.<br /><br /> 0x2 - COM birlikte çalışma.<br /><br /> 0x4 - NGen.exe ile oluşturulan saptama.<br /><br /> 0x8 - temsilci.<br /><br /> 0x10 - değişken arrgument.<br /><br /> 0x20 - yönetilmeyen çağrılan.|  
|ManagedInteropMethodToken|Kazanma: UInt32|Yönetilen birlikte çalışma yöntemi için belirteci.|  
|ManagedInteropMethodNameSpace|Kazanma: UnicodeString|Yönetilen birlikte çalışma yöntemi ad alanı.|  
|ManagedInteropMethodName|Kazanma: UnicodeString|Yönetilen birlikte çalışma yöntemi adı.|  
|ManagedInteropMethodSignature|Kazanma: UnicodeString|Yönetilen birlikte çalışabilirlik metodun imzası.|  
|NativeMethodSignature|Kazanma: UnicodeString|Yerel yöntem imzası.|  
|StubMethodSignature|Kazanma: UnicodeString|Saplama metodu imzası.|  
|StubMethodILCode|Kazanma: UnicodeString|Saplama yöntemin MSIL kodu.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|MSIL önbellek ' erişilmedi.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Kazanma: UInt16|Modül tanımlayıcısı.|  
|StubMethodID|Kazanma: UInt64|Saplama yöntem tanımlayıcısı.|  
|ManagedInteropMethodToken|Kazanma: UInt32|Yönetilen birlikte çalışma yöntemi için belirteci.|  
|ManagedInteropMethodNameSpace|Kazanma: UnicodeString|Yönetilen birlikte çalışma yöntemi ad alanı.|  
|ManagedInteropMethodName|Kazanma: UnicodeString|Yönetilen birlikte çalışma yöntemi adı.|  
|ManagedInteropMethodSignature|Kazanma: UnicodeString|Yönetilen birlikte çalışabilirlik metodun imzası.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
