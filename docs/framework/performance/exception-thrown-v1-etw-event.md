---
title: Özel Durum Thrown_V1 ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865b7b16d5807bd9161855f453128a63c84eab96
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400828"
---
# <a name="exception-thrownv1-etw-event"></a>Özel Durum Thrown_V1 ETW Olayı
Bu olay attığı özel durumları hakkında bilgileri yakalar.  
  
 Aşağıdaki tabloda, anahtar sözcüğü altında olay tetiklenir ve olay düzeyini gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Uyarı (2)|  
  
 Aşağıdaki tablo, olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Yönetilen bir özel durum oluşturulur.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Özel durum türü|Kazanma: UnicodeString|Özel durumun türünü; Örneğin, `System.NullReferenceException`.|  
|Özel durum iletisi|Kazanma: UnicodeString|Gerçek özel durum iletisi.|  
|EIPCodeThrow|Kazanma: işaretçi|Özel durum oluştuğu yönerge işaretçisi.|  
|ExceptionHR|Kazanma: UInt32|Özel durum [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|Kazanma: UInt16|0x01: HasInnerException (bkz [CLR ETW olaylarını](../../../docs/framework/performance/clr-etw-events.md) Visual Basic belgelerinde).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (işlem durumu bozuk olduğunu belirtir; bkz [işleme bozuk durum özel durumları](https://go.microsoft.com/fwlink/?LinkId=179681) MSDN'de).<br /><br /> 0x10: IsCLSCompliant (türeyen bir özel durum <xref:System.Exception> CLS uyumlu; Aksi takdirde, CLS uyumlu değil).|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
