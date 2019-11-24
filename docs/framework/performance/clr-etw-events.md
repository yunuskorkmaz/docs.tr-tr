---
title: CLR ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941af2568e72fe093860801bd2595b3037e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428170"
---
# <a name="clr-etw-events"></a>CLR ETW Olayları
The topics in this section describe event tracing for Windows (ETW) events. Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic. The CLR has two providers for the events:  
  
- The runtime provider, which raises events depending on which keywords (categories of events) are enabled. The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
- The rundown provider, which has special-purpose uses. The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.  
  
 For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Çalışma Zamanı Bilgileri Olayları](runtime-information-etw-events.md)  
 Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.  
  
 [Özel Durum Thrown_V1 Olayı](exception-thrown-v1-etw-event.md)  
 Captures information about exceptions that are thrown.  
  
 [Çekişme Olayları](contention-etw-events.md)  
 Captures information about contention for monitor locks or native locks that the runtime uses.  
  
 [İş Parçacığı Havuzu Olayları](thread-pool-etw-events.md)  
 Captures information about worker thread pools and I/O thread pools.  
  
 [Yükleyici Olayları](loader-etw-events.md)  
 Captures information about loading and unloading application domains, assemblies, and modules.  
  
 [Yöntem Olayları](method-etw-events.md)  
 Captures information about CLR methods for symbol resolution.  
  
 [Atık Toplama Olayları](garbage-collection-etw-events.md)  
 Captures information pertaining to garbage collection, to help in diagnostics and debugging.  
  
 [Olayları Tam Zamanında İzleme](jit-tracing-etw-events.md)  
 Captures information about just-in-time (JIT) inlining and tail calls.  
  
 [Birlikte Çalışma Olayları](interop-etw-events.md)  
 Captures information about Microsoft intermediate language (MSIL) stub generation and caching.  
  
 [ARM Olayları](application-domain-resource-monitoring-arm-etw-events.md)  
 Captures detailed diagnostic information about the state of an application domain.  
  
 [Güvenlik Olayları](security-etw-events.md)  
 Captures information about strong name and Authenticode verification.  
  
 [Yığın Olayı](stack-etw-event.md)  
 Captures information that is used with other events to generate stack traces after an event is raised.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Improve Debugging And Performance Tuning With ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [Windows Performance Blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [.NET Framework Günlük Kaydını Denetleme](controlling-logging.md)
- [CLR ETW Sağlayıcılar](clr-etw-providers.md)
- [CLR ETW Anahtar Sözcükleri ve Düzeyler](clr-etw-keywords-and-levels.md)
- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](etw-events-in-the-common-language-runtime.md)
