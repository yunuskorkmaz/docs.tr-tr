---
description: 'Daha fazla bilgi edinin: AppDomainInfo'
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 1e527f2a25c48a3bf35d974e3ac192d937a8a86e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757975"
---
# <a name="appdomaininfo"></a>AppDomainInfo

Uygulama etki alanı bilgileri  
  
## <a name="syntax"></a>Syntax  
  
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

 AppDomainInfo sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainID  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 AppDomain kimliği.  
  
### <a name="isdefault"></a>IsDefault  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 AppDomain 'in varsayılan AppDomain olup olmadığını gösterir.  
  
### <a name="logmalformedmessages"></a>Günlüğe kaydetme Iletileri  

 Veri türü: Boole  
  
 Erişim türü: okuma/yazma  
  
 Hatalı biçimlendirilmiş iletilerin günlüğe kaydedilip kaydedilmeyeceğini belirten bir değer.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  

 Veri türü: Boole  
  
 Erişim türü: okuma/yazma  
  
 İletilerin hizmet düzeyinde izlenip izlenmeyeceğini belirten bir değer (şifreleme ve aktarımlarla ilgili dönüşümlerden önce).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  

 Veri türü: Boole  
  
 Erişim türü: okuma/yazma  
  
 İletilerin Aktarım düzeyinde izlenip izlenmediğini belirten bir değer.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  

 Veri türü: TraceListener dizisi  
  
 Erişim türü: salt okunurdur  
  
 System. WMI. MessageLogging izleme kaynağını dinleyen koleksiyon izleme dinleyicileri.  
  
### <a name="name"></a>Name  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 AppDomain 'in adı.  
  
### <a name="performancecounters"></a>PerformanceCounters  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 AppDomain içindeki etkin performans sayaçlarının kapsamı.  
  
### <a name="processid"></a>Işlem  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 İşlem kimliği.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin yapılandırmasının yolu.  
  
### <a name="tracelevel"></a>TraceLevel  

 Veri türü: dize  
  
 Erişim türü: okuma/yazma  
  
 System. WMI izleme kaynağının izleme düzeyi.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  

 Veri türü: TraceListener dizisi  
  
 Erişim türü: salt okunurdur  
  
 System. ServiceModel izleme kaynağından gelen bir dinleyici koleksiyonu.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
