---
title: Birlikte Çalışma ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
ms.openlocfilehash: 80fd1f7487dbe3925b875e728eaeddac86927ad4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716014"
---
# <a name="interop-etw-events"></a>Birlikte Çalışma ETW Olayları
Birlikte çalışma olayları, Microsoft ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.  

## <a name="ilstubgenerated-event"></a>ILStubGenerated olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|MSIL saplaması oluşturulmuştur.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt16|Modül tanımlayıcısı.|  
|StubMethodID|Win: UInt64|Saplama yöntemi tanımlayıcısı.|  
|StubFlags|Win: UInt64|Saplama bayrakları:<br /><br /> 0x1-ters çalışabilirliği.<br /><br /> 0x2-COM birlikte çalışma.<br /><br /> 0x4-NGen. exe tarafından oluşturulan saplama.<br /><br /> 0x8-temsilci.<br /><br /> 0x10-değişken bağımsız değişkeni.<br /><br /> 0x20-yönetilmeyen aranan.|  
|ManagedInteropMethodToken|Win: UInt32|Managed Interop yöntemi için belirteç.|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Managed Interop yönteminin ad alanı.|  
|ManagedInteropMethodName|Win: UnicodeString|Yönetilen birlikte çalışma yönteminin adı.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Managed Interop yönteminin imzası.|  
|NativeMethodSignature|Win: UnicodeString|Yerel Yöntem imzası.|  
|StubMethodSignature|Win: UnicodeString|Saplama yöntemi imzası.|  
|StubMethodILCode|Win: UnicodeString|Saplama yöntemi için MSIL kodu.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="ilstubcachehit-event"></a>ILStubCacheHit olayı  

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|MSIL önbelleğine erişildi.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt16|Modül tanımlayıcısı.|  
|StubMethodID|Win: UInt64|Saplama yöntemi tanımlayıcısı.|  
|ManagedInteropMethodToken|Win: UInt32|Managed Interop yöntemi için belirteç.|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Managed Interop yönteminin ad alanı.|  
|ManagedInteropMethodName|Win: UnicodeString|Yönetilen birlikte çalışma yönteminin adı.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Managed Interop yönteminin imzası.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
