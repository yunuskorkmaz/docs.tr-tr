---
title: Özel Durum Thrown_V1 ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f0e968053c87319bf90bf3de0f21d750ec899ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447635"
---
# <a name="exception-thrown_v1-etw-event"></a>Özel Durum Thrown_V1 ETW Olayı
Bu olay, oluşturulan özel durumlarla ilgili bilgileri yakalar.  
  
 Aşağıdaki tabloda, olayın oluşturulduğu anahtar sözcük ve olay düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Uyarı (2)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Yönetilen bir özel durum oluşturulur.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Özel Durum Türü|Win: UnicodeString|Özel durumun türü; Örneğin, `System.NullReferenceException`.|  
|Özel durum Iletisi|Win: UnicodeString|Gerçek özel durum iletisi.|  
|EIPCodeThrow|Win: Işaretçi|Özel durumun oluştuğu yönerge işaretçisi.|  
|ExceptionHR|Win: UInt32|Özel durum [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|  
|ExceptionFlags|Win: UInt16|0x01: HasInnerException (Visual Basic belgelerinde [CLR ETW olaylarını](clr-etw-events.md) görün).<br /><br /> 0x02: ısnestedexception.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: ıbozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> 0x10: ısclscompliant (<xref:System.Exception> türetilen bir özel durum CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
