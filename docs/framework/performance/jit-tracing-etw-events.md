---
title: ETW Olaylarını JIT İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145a53363c9d7aca622ee0b1ccb2700e5984397d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046420"
---
# <a name="jit-tracing-etw-events"></a>ETW Olaylarını JIT İzleme
<a name="top"></a>Bu olaylar, tam zamanında (JıT) giriş ve JıT kuyruğu çağrılarının başarısı veya başarısızlığı ile ilgili bilgiler toplar.  
  
 JıT izleme olayları aşağıdaki iki kategoriden oluşur:  
  
- [JıT olayları](#jit_inlining_events)  
  
- [JıT kuyruğu çağrı olayları](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JıT olayları  
  
### <a name="methodjitinliningfailed-event"></a>Methodjınliningfailed olayı  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|JıT girişi başarısız oldu.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Derlenmekte olan metodun ad alanı.|  
|MethodBeingCompiledName|Win: UnicodeString|Derlenmekte olan yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derlenmekte olan metodun imzası.|  
|Inlinernamespace|Win: UnicodeString|JıT derleyicisinin için kod oluşturmaya çalıştığı yöntemin ad alanı.|  
|InlinerName|Win: UnicodeString|Derleyicinin kod oluşturmaya çalışan yöntemin adı. Bu, derleyicinin ' a çağrı `MethodBeingCompiledName` `InlinerName`oluşturmak `MethodBeingCompiledName` yerine satır içi kod almaya çalıştığı ile aynı olmayabilir.|  
|Inlinernamesignature|Win: UnicodeString|İnoluşturucu için imza.|  
|Inlineenamespace|Win: UnicodeString|İnlinee ad alanı.|  
|Inlineename|Win: UnicodeString|Derleyicinin satır içine almaya çalıştığı Yöntem (bir çağrı oluşturmaz).|  
|Inlineenamesignature|Win: UnicodeString|Inlinee için imza.|  
|Failalyollar|Win: Boolean|JıT derleyicisine yönelik bir ipucu, inlinee için her zaman başarısız olur.|  
|FailReason|Win: UnicodeString|INLINE_NEVER, önceki bir ıntıl denemesinin başka bir nedenden dolayı hiçbir şekilde başarısız olacağını tespit eder; Aksi takdirde, serbest biçimli metin.|  
|ClrInstanceID|Win: UnicodeString|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
### <a name="methodjitinliningsucceeded-event"></a>Methodjınliningsucceeded olayı  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Yöntem geçersiz oldu.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Derlenmekte olan metodun ad alanı.|  
|MethodBeingCompiledName|Win: UnicodeString|Derlenen yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derlenmekte olan metodun imzası.|  
|Inlinernamespace|Win: UnicodeString|JıT derleyicisinin için kod oluşturmaya çalışan yöntemin ad alanı.|  
|InlinerName|Win: UnicodeString|Derleyicinin kod oluşturmaya çalışan yöntemin adı. Bu, derleyicinin ' a çağrı `MethodBeingCompiledName` `InlinerName`oluşturmak `MethodBeingCompiledName` yerine satır içi kod almaya çalıştığı ile aynı olmayabilir.|  
|Inlinernamesignature|Win: UnicodeString|İnoluşturucu için imza.|  
|Inlineenamespace|Win: UnicodeString|İnlinee ad alanı.|  
|Inlineename|Win: UnicodeString|Derleyicinin satır içine almaya çalıştığı Yöntem (bir çağrı oluşturmaz).|  
|Inlineenamesignature|Win: UnicodeString|Inlinee için imza.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
 [Başa dön](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>JıT kuyruğu çağrı olayları  
  
### <a name="methodjittailcallfailed-event"></a>Methodjbir Callcallfailed olayı  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Yöntem tail çağrısı başarısız oldu.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Derlenmekte olan metodun ad alanı.|  
|MethodBeingCompiledName|Win: UnicodeString|Derlenmekte olan yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derlenmekte olan metodun imzası.|  
|CallerNamespace|Win: UnicodeString|JıT derleyicisinin için kod oluşturmaya çalışan yöntemin ad alanı.|  
|CallerName|Win: UnicodeString|Derleyicinin kod oluşturmaya çalışan yöntemin adı.|  
|CallerNameSignature|Win: UnicodeString|Çağıran için imza.|  
|Caltaenamespace|Win: UnicodeString|Çağrılan ad alanı.|  
|Caltaename|Win: UnicodeString|Derleyicinin çağrı kuyruğunu deneme yöntemi (bir çağrı oluşturmaz).|  
|Caltaenamesignature|Win: UnicodeString|Aranan için imza.|  
|Uyarprefıx|Win: Boolean|Kuyruk çağrısının öneki|  
|FailReason|Win: UnicodeString|Kuyruk çağrısının başarısız olmasının nedeni.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
### <a name="methodjittailcallsucceeded-event"></a>Methodj, Callsucceeded olayı  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Düzey|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Yöntem tail çağrısı başarılı oldu.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Win: UnicodeString|Derlenmekte olan metodun ad alanı.|  
|MethodBeingCompiledName|Win: UnicodeString|Derlenmekte olan yöntemin adı.|  
|MethodBeingCompiledNameSignature|Win: UnicodeString|Derlenmekte olan metodun imzası.|  
|CallerNamespace|Win: UnicodeString|JıT derleyicisinin için kod oluşturmaya çalışan yöntemin ad alanı.|  
|CallerName|Win: UnicodeString|Derleyicinin kod oluşturmaya çalışan yöntemin adı.|  
|CallerNameSignature|Win: UnicodeString|Çağıran için imza.|  
|Caltaenamespace|Win: UnicodeString|Çağrılan ad alanı.|  
|Caltaename|Win: UnicodeString|Derleyicinin çağrı kuyruğunu deneme yöntemi (bir çağrı oluşturmaz).|  
|Caltaenamesignature|Win: UnicodeString|Aranan için imza.|  
|Uyarprefıx|Win: Boolean|Kuyruk çağrısının öneki.|  
|, Uyarcalltype|Win: UnicodeString|Kuyruk çağrısının türü.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
