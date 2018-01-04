---
title: "ETW Olaylarını JIT İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf205ef1707cee81e741f71d3dce771e53caee93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="jit-tracing-etw-events"></a>ETW Olaylarını JIT İzleme
<a name="top"></a>Bu olaylar, başarı veya başarısızlık tam zamanında (JIT) satır içi kullanım ve JIT kuyruk çağrıları ilgili bilgi toplayın.  
  
 JIT izleme olayları aşağıdaki iki kategoriye oluşur:  
  
-   [JIT satır içi kullanım olayları](#jit_inlining_events)  
  
-   [JIT Tail çağrısı olayları](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT satır içi kullanım olayları  
  
### <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Satır içi kullanım JIT başarısız oldu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Namespace derleniyor yöntemi.|  
|MethodBeingCompiledName|Win: UnicodeString|Derleniyor yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derleniyor yöntemi imzası.|  
|InlinerNamespace|Win: UnicodeString|JIT Derleyici yöntemi ad alanı kodunu oluşturmak çalışıyor.|  
|InlinerName|Win: UnicodeString|Derleme kodunu oluşturmak için çalışıyor yöntemin adı. Bu aynı olmayabilir `MethodBeingCompiledName` derleyici, satır içi koduna çalışılıyor varsa `MethodBeingCompiledName` yapılan bir çağrı oluşturmak yerine `InlinerName`.|  
|InlinerNameSignature|Win: UnicodeString|İnliner imzası.|  
|InlineeNamespace|Win: UnicodeString|İnlinee ad alanı.|  
|InlineeName|Win: UnicodeString|Satır içi derleyici çalışıyor yöntemi (yapılan bir çağrı Oluştur değil).|  
|InlineeNameSignature|Win: UnicodeString|İnlinee imzası.|  
|FailAlways|Win: Boolean|Bu satır içi kullanım JIT Derleyici ipucu inlinee için her zaman başarısız olur.|  
|FailReason|Win: UnicodeString|INLINE_NEVER anlamına gelir önceki bir satır içi kullanım girişimi, satır içi kullanım belirlenen hiçbir zaman başka bir nedenle; başarılı Aksi takdirde, serbest biçimli metin.|  
|ClrInstanceID|Win: UnicodeString|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Satır içi kullanım yöntemi başarılı oldu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Ad alanı derleniyor yöntemi.|  
|MethodBeingCompiledName|Win: UnicodeString|Derlenmiş olan olma yöntemi adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derleniyor yöntemi imzası.|  
|InlinerNamespace|Win: UnicodeString|JIT Derleyici yöntemi ad alanı kodunu oluşturmak çalışıyor.|  
|InlinerName|Win: UnicodeString|Derleme kodunu oluşturmak için çalışıyor yöntemin adı. Bu aynı olmayabilir `MethodBeingCompiledName` derleyici, satır içi koduna çalışılıyor varsa `MethodBeingCompiledName` yapılan bir çağrı oluşturmak yerine `InlinerName`.|  
|InlinerNameSignature|Win: UnicodeString|İnliner imzası.|  
|InlineeNamespace|Win: UnicodeString|İnlinee ad alanı.|  
|InlineeName|Win: UnicodeString|Satır içi derleyici çalışıyor yöntemi (yapılan bir çağrı Oluştur değil).|  
|InlineeNameSignature|Win: UnicodeString|İnlinee imzası.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>JIT Tail çağrısı olayları  
  
### <a name="methodjittailcallfailed-event"></a>MethodJITTailCallFailed olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Yöntem tail çağrısı başarısız oldu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Namespace derleniyor yöntemi.|  
|MethodBeingCompiledName|Win: UnicodeString|Derleniyor yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derleniyor yöntemi imzası.|  
|CallerNamespace|Win: UnicodeString|JIT Derleyici yöntemi ad alanı kodunu oluşturmak çalışıyor.|  
|CallerName|Win: UnicodeString|Derleme kodunu oluşturmak için çalışıyor yöntemin adı.|  
|CallerNameSignature|Win: UnicodeString|Arayan imzası.|  
|CalleeNamespace|Win: UnicodeString|Aranan ad alanı.|  
|CalleeName|Win: UnicodeString|Yöntem derleyici çağrısı kuyruk çalışıyor (yapılan bir çağrı Oluştur değil).|  
|CalleeNameSignature|Win: UnicodeString|Aranan imzası.|  
|TailPrefix|Win: Boolean|Kuyruk çağrısı için önek|  
|FailReason|Win: UnicodeString|Neden kuyruk çağrısı başarısız oldu.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
### <a name="methodjittailcallsucceeded-event"></a>MethodJITTailCallSucceeded olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`(0x10)|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Yöntem tail çağrısı başarılı oldu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Namespace derleniyor yöntemi.|  
|MethodBeingCompiledName|Win: UnicodeString|Derleniyor yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derleniyor yöntemi imzası.|  
|CallerNamespace|Win: UnicodeString|JIT Derleyici yöntemi ad alanı kodunu oluşturmak çalışıyor.|  
|CallerName|Win: UnicodeString|Derleme kodunu oluşturmak için çalışıyor yöntemin adı.|  
|CallerNameSignature|Win: UnicodeString|Arayan imzası.|  
|CalleeNamespace|Win: UnicodeString|Aranan ad alanı.|  
|CalleeName|Win: UnicodeString|Yöntem derleyici çağrısı kuyruk çalışıyor (yapılan bir çağrı Oluştur değil).|  
|CalleeNameSignature|Win: UnicodeString|Aranan imzası.|  
|TailPrefix|Win: Boolean|Kuyruk çağrısı için önek.|  
|TailCallType|Win: UnicodeString|Kuyruk çağrısı türü.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
