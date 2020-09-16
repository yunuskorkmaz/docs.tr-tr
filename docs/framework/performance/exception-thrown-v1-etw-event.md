---
title: Özel Durum Thrown_V1 ETW Olayı
description: ExceptionThrown_V1 ETW olayı hakkında ayrıntılı bilgileri görüntüleyin. Oluşturulan özel durumlar için alan adları, veri türleri ve açıklamalar gibi olay verileri verilir.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f4ae277b5dfb09d2676755fec2208b63906ead84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554677"
---
# <a name="exception-thrown_v1-etw-event"></a>Özel Durum Thrown_V1 ETW Olayı
Bu olay, oluşturulan özel durumlarla ilgili bilgileri yakalar.  
  
 Aşağıdaki tabloda, olayın oluşturulduğu anahtar sözcük ve olay düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` 0x8000|Uyarı (2)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Yönetilen bir özel durum oluşturulur.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Özel durum türü|Win: UnicodeString|Özel durumun türü; Örneğin, `System.NullReferenceException` .|  
|Özel durum Iletisi|Win: UnicodeString|Gerçek özel durum iletisi.|  
|EIPCodeThrow|Win: Işaretçi|Özel durumun oluştuğu yönerge işaretçisi.|  
|ExceptionHR|Win: UInt32|Özel durum [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|  
|ExceptionFlags|Win: UInt16|0x01: HasInnerException (Visual Basic belgelerinde [CLR ETW olaylarını](clr-etw-events.md) görün).<br /><br /> 0x02: ısnestedexception.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: ıbozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> 0x10: ısclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
