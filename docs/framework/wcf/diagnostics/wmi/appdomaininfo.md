---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170230"
---
# <a name="appdomaininfo"></a>AppDomainInfo
Uygulama etki alanı bilgileri  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
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
 AppDomainInfo sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Uygulama etki alanı kimliği.  
  
### <a name="isdefault"></a>Dil paketinde IsDefault  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Appdomain varsayılan uygulama etki alanı olup olmadığını belirtir.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Veri türü: Boole  
  
 Erişim türü: okuma/yazma  
  
 Hatalı biçimlendirilmiş iletilerin kaydedilip kaydedilmeyeceğini belirten bir değeri.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Veri türü: Boole  
  
 Erişim türü: okuma/yazma  
  
 İletilerin hizmet düzeyinde (önce şifreleme ve taşıma ilişkili dönüşümler) izlenilmeyeceğini belirleyen bir değer.  
  
### <a name="logmessagesattransportlevel"></a>Transfer  
 Veri türü: Boole  
  
 Erişim türü: okuma/yazma  
  
 İletileri taşıma düzeyinde izlenip izlenilmeyeceğini belirleyen bir değer.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Veri türü: TraceListener dizi  
  
 Erişim türü: salt okunur  
  
 Dinleme System.Wmi.MessageLogging izleme kaynağına izleme dinleyicileri koleksiyonu.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Uygulama etki alanı adı.  
  
### <a name="performancecounters"></a>PerformanceCounters  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Appdomain içinde etkin performans sayaçlarının kapsamı.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İşlem kimliği.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hizmeti yapılandırma yolu.  
  
### <a name="tracelevel"></a>TraceLevel  
 Veri türü: dize  
  
 Erişim türü: okuma/yazma  
  
 System.Wmi izleme kaynağına izleme düzeyi.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Veri türü: TraceListener dizi  
  
 Erişim türü: salt okunur  
  
 System.ServiceModel kaynağına ait izleme dinleyicileri koleksiyonudur.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|
