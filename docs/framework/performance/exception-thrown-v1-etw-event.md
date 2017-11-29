---
title: "Özel Durum Thrown_V1 ETW Olayı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dcf3390821c4210ced4c43dab5a94c93802d5f9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-thrownv1-etw-event"></a>Özel Durum Thrown_V1 ETW Olayı
Bu olay, oluşturulan özel durumlar hakkında bilgi yakalar.  
  
 Aşağıdaki tabloda, altında olay tetiklenir anahtar sözcüğü ve olay düzeyini gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`ExceptionKeyword`(0x8000)|Uyarı (2)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Yönetilen bir özel durum oluşur.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Özel durum türü|Win: UnicodeString|Özel durum türünü; Örneğin, `System.NullReferenceException`.|  
|Özel durum iletisi|Win: UnicodeString|Gerçek özel durum iletisi.|  
|EIPCodeThrow|Win: işaretçi|Yönerge işaretçisi burada özel durum oluştu.|  
|ExceptionHR|Win: UInt32|Özel durum [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|Win: UInt16|0x01: HasInnerException (bkz [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md) Visual Basic belgelerinde).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (işlem durumu bozuk olduğunu gösteriyor; bkz [işleme bozuk durumu özel durumları](http://go.microsoft.com/fwlink/?LinkId=179681) MSDN'de).<br /><br /> 0x10: IsCLSCompliant (türeyen bir özel durum <xref:System.Exception> CLS uyumlu; Aksi takdirde, CLS uyumlu değil).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
