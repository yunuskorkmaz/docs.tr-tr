---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 7189448a930298837089cf3ac2743cb7e073ae02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486987"
---
# <a name="appdomaininfo"></a>AppDomainInfo
Uygulama etki alanı bilgileri  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 AppDomainInfo sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Appdomain kimliği.  
  
### <a name="isdefault"></a>IsDefault  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Appdomain varsayılan appdomain olup olmadığını gösterir.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Veri türü: boolean  
  
 Erişim türüne: okuma/yazma  
  
 Hatalı biçimlendirilmiş iletileri günlüğe olup olmadığını belirten bir değer.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Veri türü: boolean  
  
 Erişim türüne: okuma/yazma  
  
 İletiler (şifreleme ve taşımayla ilgili Dönüşümlerde önce) hizmet düzeyinde izlenip izlenmediğini belirten bir değer.  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Veri türü: boolean  
  
 Erişim türüne: okuma/yazma  
  
 İletileri aktarım düzeyinde izlenip izlenmediğini belirten bir değer.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Veri türü: TraceListener dizisi  
  
 Erişim türüne: salt okunur  
  
 System.Wmi.MessageLogging izleme kaynağını dinleyen izleme dinleyicileri koleksiyonu.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Uygulama etki alanı adı.  
  
### <a name="performancecounters"></a>performans sayaçları  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Appdomain'deki etkin performans sayaçlarının kapsamı.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İşlem kimliği.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Hizmet yapılandırma yolu.  
  
### <a name="tracelevel"></a>TraceLevel  
 Veri türü: dize  
  
 Erişim türüne: okuma/yazma  
  
 System.Wmi izleme kaynağına izleme düzeyi.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Veri türü: TraceListener dizisi  
  
 Erişim türüne: salt okunur  
  
 System.ServiceModel izleme kaynağından dinleyicileri koleksiyonu.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|
