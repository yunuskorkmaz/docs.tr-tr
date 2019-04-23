---
title: ETW Olaylarını JIT İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7261e5ce06a4ac20b1e7c816ababf8c8ba129b29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150767"
---
# <a name="jit-tracing-etw-events"></a>ETW Olaylarını JIT İzleme
<a name="top"></a> Bu olaylar, başarı veya hata just-in-time (JIT) satır içi kullanım ve JIT kuyruk çağrıları ile ilgili bilgi toplayın.  
  
 JIT izleme olayları aşağıdaki iki kategoriye oluşur:  
  
-   [JIT satır içi kullanım olayları](#jit_inlining_events)  
  
-   [JIT Tail çağrısı olayları](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT satır içi kullanım olayları  
  
### <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Ayrıntılı (5)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Satır içi kullanım JIT başarısız oldu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Kazanma: UnicodeString|Namespace yönteminin derleniyor.|  
|MethodBeingCompiledName|Kazanma: UnicodeString|Derleniyor yöntemin adı.|  
|MethodBeingCompiledNameSignature|Kazanma: UnicodeString|Derleniyor metodu imzası.|  
|InlinerNamespace|Kazanma: UnicodeString|Ad alanı JIT derleyicisi yönteminin kodunu oluşturmak çalışıyor.|  
|InlinerName|Kazanma: UnicodeString|Derleyici kod üretmek için çalışıyor yöntemin adı. Bu aynı olmayabilir `MethodBeingCompiledName` derleyici, satır içi kod çalışılıyor, `MethodBeingCompiledName` çağrı oluşturmak yerine `InlinerName`.|  
|InlinerNameSignature|Kazanma: UnicodeString|İnliner imzası.|  
|InlineeNamespace|Kazanma: UnicodeString|Alınanın ad alanı.|  
|InlineeName|Kazanma: UnicodeString|Derleyici, satır içi çalışıyor yöntemi (bir çağrı oluşturma değil).|  
|InlineeNameSignature|Kazanma: UnicodeString|Alınanın imzası.|  
|FailAlways|Kazanma: Boolean|JIT Derleyici, satır içi kullanım için bir ipucu alınanın için her zaman başarısız olur.|  
|FailReason|Kazanma: UnicodeString|INLINE_NEVER anlamına gelir inlining'i olmuştu belirlenen inlining'i olacak hiçbir zaman başka bir nedenle; başarılı Aksi takdirde, serbest biçimli metin.|  
|ClrInstanceID|Kazanma: UnicodeString|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Ayrıntılı (5)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Satır içi kullanım yöntem başarılı oldu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Kazanma: UnicodeString|Ad alanı derleniyor yöntemi.|  
|MethodBeingCompiledName|Kazanma: UnicodeString|Derlenmiş olma yöntemi adı.|  
|MethodBeingCompiledNameSignature|Kazanma: UnicodeString|Derleniyor metodu imzası.|  
|InlinerNamespace|Kazanma: UnicodeString|Ad alanı JIT derleyicisi yönteminin kodunu oluşturmak çalışıyor.|  
|InlinerName|Kazanma: UnicodeString|Derleyici kod üretmek için çalışıyor yöntemin adı. Bu aynı olmayabilir `MethodBeingCompiledName` derleyici, satır içi kod çalışılıyor, `MethodBeingCompiledName` çağrı oluşturmak yerine `InlinerName`.|  
|InlinerNameSignature|Kazanma: UnicodeString|İnliner imzası.|  
|InlineeNamespace|Kazanma: UnicodeString|Alınanın ad alanı.|  
|InlineeName|Kazanma: UnicodeString|Derleyici, satır içi çalışıyor yöntemi (bir çağrı oluşturma değil).|  
|InlineeNameSignature|Kazanma: UnicodeString|Alınanın imzası.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>JIT Tail çağrısı olayları  
  
### <a name="methodjittailcallfailed-event"></a>MethodJITTailCallFailed olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Ayrıntılı (5)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Yöntem tail çağrısı başarısız oldu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Kazanma: UnicodeString|Namespace yönteminin derleniyor.|  
|MethodBeingCompiledName|Kazanma: UnicodeString|Derleniyor yöntemin adı.|  
|MethodBeingCompiledNameSignature|Kazanma: UnicodeString|Derleniyor metodu imzası.|  
|CallerNamespace|Kazanma: UnicodeString|Ad alanı JIT derleyicisi yönteminin kodunu oluşturmak çalışıyor.|  
|CallerName|Kazanma: UnicodeString|Derleyici kod üretmek için çalışıyor yöntemin adı.|  
|CallerNameSignature|Kazanma: UnicodeString|Çağıranın imzası.|  
|CalleeNamespace|Kazanma: UnicodeString|Çağrılan ad alanı.|  
|CalleeName|Kazanma: UnicodeString|Yöntem derleyici arama kuyruk çalışıyor (bir çağrı oluşturma değil).|  
|CalleeNameSignature|Kazanma: UnicodeString|Çağrılan imzası.|  
|TailPrefix|Kazanma: Boolean|Kuyruk çağrısı için ön ek|  
|FailReason|Kazanma: UnicodeString|Neden kuyruk çağrısı başarısız oldu.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="methodjittailcallsucceeded-event"></a>MethodJITTailCallSucceeded olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Ayrıntılı (5)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Metot tail çağrısı başarılı oldu.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Kazanma: UnicodeString|Namespace yönteminin derleniyor.|  
|MethodBeingCompiledName|Kazanma: UnicodeString|Derleniyor yöntemin adı.|  
|MethodBeingCompiledNameSignature|Kazanma: UnicodeString|Derleniyor metodu imzası.|  
|CallerNamespace|Kazanma: UnicodeString|Ad alanı JIT derleyicisi yönteminin kodunu oluşturmak çalışıyor.|  
|CallerName|Kazanma: UnicodeString|Derleyici kod üretmek için çalışıyor yöntemin adı.|  
|CallerNameSignature|Kazanma: UnicodeString|Çağıranın imzası.|  
|CalleeNamespace|Kazanma: UnicodeString|Çağrılan ad alanı.|  
|CalleeName|Kazanma: UnicodeString|Yöntem derleyici arama kuyruk çalışıyor (bir çağrı oluşturma değil).|  
|CalleeNameSignature|Kazanma: UnicodeString|Çağrılan imzası.|  
|TailPrefix|Kazanma: Boolean|Tail çağrısı için önek.|  
|TailCallType|Kazanma: UnicodeString|Kuyruk çağrısı türü.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
