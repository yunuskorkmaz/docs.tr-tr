---
title: Çözümleme İzleme Etkinliği Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: ae792a0b55b0559b13c2394bd27d85f224d1aea0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243968"
---
# <a name="analytic-trace-event-reference"></a>Çözümleme İzleme Etkinliği Başvurusu
Aşağıdaki tablo, WCF analitik Izleme ile ilişkili olay düzeylerini, tanımlayıcıları ve iletileri tanımlar.  
  
## <a name="event-reference"></a>Olay başvurusu  
  
|Olay Kimliği|Olay düzeyi|Olay Iletisi|anahtar sözcükler|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Ayrıntılı|Havuz% 1 bayt ayırıyor.|Altyapı|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Ayrıntılı|BufferPool% 1 boyutunda, kota% 2 ile değiştiriliyor.|Altyapı|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Ayrıntılı|GÇ Iş parçacığı Zamanlayıcı geri çağırması çağrıldı.|Altyapı|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Ayrıntılı|GÇ Iş parçacığı Zamanlayıcı geri çağırması çağrıldı.|Altyapı|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Clientmessageınspector üzerinde ' AfterReceiveReply ' çağırdı.|Sorun giderme, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Clientmessageınspector üzerinde ' BeforeSendRequest ' çağırdı.|Sorun giderme, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Bilgiler|Dağıtıcı bir Clientparameterınspector üzerinde ' AfterCall ' çağırdı. '% 1 ' türünde.|Sorun giderme, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Clientparameterınspector üzerinde ' Befohatırla ' çağırdı.|Sorun giderme, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Bilgiler|Bir OperationInvoker '% 1 ' metodunu çağırdı.|EndToEndMonitoring, sorun giderme, ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Bilgiler|Dağıtıcı, '% 3 ' türünde bir özel durum ile '% 1 ' türünde bir ErrorHandler çağırdı.  Errorişlenmiş = = '% 2 '.|Sorun giderme, ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Bilgiler|Dağıtıcı, '% 2 ' türünde bir özel durum ile '% 1 ' türünde bir FaultProvider çağırdı.|Sorun giderme, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Messageınspector üzerinde ' AfterReceiveReply ' çağırdı.|Sorun giderme, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Messageınspector üzerinde ' BeforeSendRequest ' çağırdı.|Sorun giderme, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Uyarı|'% 2 ' için '% 1 ' kısıtlama sınırına ulaşıldı.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Parameterınspector üzerinde ' AfterCall ' çağırdı.|Sorun giderme, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Bilgiler|Dağıtıcı, '% 1 ' türünde bir Parameterınspector üzerinde ' Befohatırla ' çağırdı.|Sorun giderme, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|Günlüğe kaydetme her zaman|ServiceHost başlatıldı: '% 1 '.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Bilgiler|Bir OperationInvoker '% 1 ' metoduna çağrıyı tamamladı.  Yöntem çağrısı süresi '% 2 ' MS idi.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Bilgiler|Taşıma, '% 1 ' öğesinden bir ileti aldı.|Sorun giderme, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Bilgiler|Taşıma, '% 1 ' öğesine bir ileti gönderdi.|Sorun giderme, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Bilgiler|Istemci, '% 2 ' sözleşmesinde tanımlanan '% 1 ' işlemini yürütüyor. İleti, '% 3 ' öğesine gönderilecek.|Sorun giderme, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Bilgiler|Istemci, '% 2 ' sözleşmesinde tanımlanan '% 1 ' işlemini yürütmeyi tamamladı. İleti, '% 3 ' öğesine gönderildi.|Sorun giderme, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Hata|İleti işleme sırasında '% 2 ' türünde işlenmeyen bir özel durum oluştu.  Tam özel durum ToString:% 1.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Bilgiler|Dağıtıcı, aktarıma bir ileti gönderdi. Bağıntı KIMLIĞI = = '% 1 '.|EndToEndMonitoring, sorun giderme, ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Bilgiler|Dağıtıcı aktarımdan bir ileti aldı. Bağıntı KIMLIĞI = = '% 1 '.|EndToEndMonitoring, sorun giderme, ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Uyarı|'% 1 ' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu. Yöntem çağrısı süresi '% 2 ' MS idi.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Uyarı|'% 1 ' yöntemi, OperationInvoker tarafından çağrıldığında bir FaultException belirtti. Yöntem çağrısı süresi '% 2 ' MS idi.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Uyarı|'% 2 ' öğesinin '% 1 ' kısıtlama sınırı% 70.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|Günlüğe kaydetme her zaman|Toplam% 2 etkinleştirilmiş hizmetten boşta kalan% 1 hizmet kapatıldı.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Hata|Ad: '% 1 ', başvuru: '% 2 ', yük:% 3.|Kullanıcıetkinlikleri, HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Uyarı|Ad: '% 1 ', başvuru: '% 2 ', yük:% 3.|Kullanıcıetkinlikleri, HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Bilgiler|Ad: '% 1 ', başvuru: '% 2 ', yük:% 3.|Kullanıcıetkinlikleri, HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Bilgiler|Etkinlik sınırı.|Sorun giderme|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Bilgiler|Etkinlik sınırı.|Sorun giderme|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Bilgiler|Etkinlik sınırı.|Sorun giderme|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Bilgiler|Etkinlik sınırı.|Sorun giderme|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Bilgiler|%1|Sorun giderme, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Uyarı|%1|Sorun giderme, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|Günlüğe kaydetme her zaman|Aktarım olayı yayınlandı.|Sorun giderme, Kullanıcıetkinlikleri, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Bilgiler|Derlemeyi başlatın.|Leyemedi|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Bilgiler|Derlemeyi bitir.|Leyemedi|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Bilgiler|ServiceHostFactory oluşturmaya başladı.|Leyemedi|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Bilgiler|ServiceHostFactory son oluşturma.|Leyemedi|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Bilgiler|CreateServiceHost 'u başlatın.|Leyemedi|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Bilgiler|CreateServiceHost 'u sonlandır.|Leyemedi|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Bilgiler|HostedTransportConfigurationManager yapılandırma başlatmayı Başlat.|Leyemedi|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Bilgiler|HostedTransportConfigurationManager yapılandırmayı başlatma.|Leyemedi|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Bilgiler|HostedTransportConfigurationManager yapılandırmayı başlatma.|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Bilgiler|ServiceHost açma tamamlandı.|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Bilgiler|'% 1 ' AppDomain 'e ait '% 2 ' sanal yoluna sahip istek alındı.|Leyemedi|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Bilgiler|WebHostRequest durdu.|Leyemedi|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Ayrıntılı|İşlenen ServiceActivation öğesi göreli adresi: '% 1 ', normalleştirilmiş göreli adres '% 2 '.||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Ayrıntılı|Gelen istek, adresi '% 1 ' olan bir ServiceActivation öğesiyle eşleşiyor.||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Ayrıntılı|Gelen istek,% 1 adresli Asp.Net rotasında tanımlanan bir WCF hizmeti ile eşleşiyor.|Yönlendirme hizmetleri|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Ayrıntılı|ServiceType '% 2 ' ve serviceHostFactoryType '% 3 ' olan '% 1 ' yeni bir Asp.Net rotası eklendi.|Yönlendirme hizmetleri|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Ayrıntılı|Incrementbusyıcount çağrıldı. Kaynak:% 1|Leyemedi|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Ayrıntılı|Çağrılan Mentbuson sayısını azaltır. Kaynak:% 1|Leyemedi|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Ayrıntılı|ServiceChannelOpen başladı.|Leyemedi|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Bilgiler|ServiceChannelOpen tamamlandı.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Bilgiler|ServiceChannelCall başladı.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Bilgiler|ServiceChannel zaman uyumsuz çağrıları başladı.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Ayrıntılı|Http gönderme Isteği başladı.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Ayrıntılı|Http gönderme Isteği durdu.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Ayrıntılı|Http aktarımından ileti alındı.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Bilgiler|İleti dağıtma başladı.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Ayrıntılı|İleti dağıtma için kimlik doğrulamasını Başlat.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Ayrıntılı|İleti gönderme için Yetkilendirmeyi başlatın.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Bilgiler|İleti gönderme tamamlandı.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Bilgiler|ServiceChannel açma başladı.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Bilgiler|ServiceChannel açma durdu.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Bilgiler|Http gönderme akışı iletisi başlatıldı.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Hata|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Hata|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Hata|% 1 bağlantı havuzu anahtarı:% 2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Bilgiler|% 1 bağlantı havuzu anahtarı:% 2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Hata|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Hata|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Hata|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Bilgiler|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Hata|%1|Kotasının|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Hata|%1|Kotasının|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Bilgiler|%1|Kotasının|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Bilgiler|%1|Kotasının|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Hata|%1|Kotasının|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Hata|%1|Kotasının|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Ayrıntılı|Anlaşma belirteci Doğrulayıcı durumu önbellek oranı:% 1/% 2|Kotasının|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Ayrıntılı|Güvenlik oturumu oranı:% 1/% 2|Kotasının|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Ayrıntılı|Bekleyen bağlantı oranı:% 1/% 2|Kotasının|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Ayrıntılı|Eşzamanlı oturumların oranı:% 1/% 2|Kotasının|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Ayrıntılı|Eşzamanlı oturumların oranı:% 1/% 2|Kotasının|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Ayrıntılı|Uç nokta başına giden bağlantı oranı:% 1/% 2|Kotasının|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Ayrıntılı|Kanal başına bekleyen ileti oranı:% 1/% 2|Kotasının|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Ayrıntılı|Eşzamanlı örneklerin oranı:% 1/% 2|Kotasının|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Bilgiler|Bekleyen sıfır kabul|Kotasının|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Uyarı|1%|Kotasının|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Uyarı|Kimliği '% 1 ' olan MSMQ iletisinde alma yeniden deneme sayısına ulaşıldı|Kotasının|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Hata|Kimliği '% 1 ' olan MSMQ iletisinde en fazla yeniden deneme döngüsü aşıldı|Kotasının|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Ayrıntılı|Yeni '% 1 ' oluşturuldu|Kotasının|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Ayrıntılı|Yeni '% 1 ' oluşturuldu|Kotasının|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Hata|1%|Kotasının|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Uyarı|% 1 işlemi tamamlanamıyor.|Kanalla|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Uyarı|% 1 bırakılamadı.|Kanalla|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Uyarı|Alma bağlamı hatalı.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Bilgiler|% 1,% 2 özel durumuyla bırakıldı.|Kanalla|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Bilgiler|Önbelleğe alınan kanal fabrikası sayısı: '% 1 '.  En fazla '% 2 ' kanal fabrikası önbelleğe alınabilir.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Bilgiler|Önbellek, '% 1 ' sınırına ulaştığından önbellekten eski bir kanal fabrikası kullanıldı.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Bilgiler|Önbellekte bulunan eşleşen kanal fabrikası kullanıldı.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Bilgiler|Önbellekten kanal fabrikası kullanmıyor, yani örnek için önbelleğe alma devre dışı.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Bilgiler|'% 1 ' kullanılarak sorgu oluşturma Istek Uri 'Si üzerinde yürütüldü: '% 2 '.|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Hata|'% 1 ' işlemi hatalarla dağıtıldı.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Bilgiler|'% 1 ' işlemi başarıyla dağıtıldı.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Bilgiler|Kodlayıcı tarafından boyutu '% 1 ' bayt olan bir ileti okundu.|Kanalla|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Bilgiler|Kodlayıcı tarafından boyutu '% 1 ' bayt olan bir ileti yazıldı.|Kanalla|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Hata|'% 1 ' Uri 'sine yönelik boştaki kanal için oturum iptal ediliyor.|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Ayrıntılı|Bağlantı kabulü başladı.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Ayrıntılı|Listenerıd:% 1 kabul edilen Socketıd:% 2.|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Ayrıntılı|% 1 havuzu için kullanılabilir bağlantı yok ve% 2 meşgul bağlantı yok.|Kanalla|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Ayrıntılı|Dağıtıcı istek iletisini seri durumdan çıkarmayı başlattı.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Ayrıntılı|Dağıtıcı istek iletisini seri durumdan çıkarmayı tamamladı.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Ayrıntılı|Dağıtıcı yanıt iletisini Serileştirmeyi başlattı.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Ayrıntılı|Dağıtıcı yanıt iletisini Serileştirmeyi tamamladı.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Ayrıntılı|İstemci isteği serileştirme başladı.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Ayrıntılı|İstemci istek iletisini Serileştirmeyi tamamladı.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Ayrıntılı|İstemci yanıt iletisini seri durumdan çıkarmayı başlattı.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Ayrıntılı|İstemci yanıt iletisini seri durumdan çıkarmayı tamamladı.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Ayrıntılı|Güvenlik anlaşması başladı.|Güvenlik|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Ayrıntılı|Güvenlik anlaşması tamamlandı.|Güvenlik|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Ayrıntılı|SecurityTokenProvider açma tamamlandı.|Güvenlik|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Ayrıntılı|Giden ileti güvenli hale getirildi.|Güvenlik|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Ayrıntılı|Gelen ileti doğrulandı.|Güvenlik ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Ayrıntılı|Hizmet örneği alımı başlatıldı.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Ayrıntılı|Hizmet örneği alındı.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Ayrıntılı|Channelhandlerıd:% 1-Ileti alma döngüsü başladı.|Kanalla|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Ayrıntılı|Channelhandlerıd:% 1-Ileti alma döngüsü durdu.|Kanalla|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Ayrıntılı|ChannelFactory oluşturuldu.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Ayrıntılı|Kanal bağlantısı kabulü% 1 tarihinde başladı.|Kanalla|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Ayrıntılı|Kanal bağlantısı kabul edildi.|Kanalla|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Ayrıntılı|% 1 için bağlantı kurma işlemi başladı.|Kanalla|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Ayrıntılı|Bağlantı oluşturuldu.|Kanalla|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Ayrıntılı|'% 1 ' için oturum girişi anlaşıldı.|Kanalla|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Hata|Bağlantı okuyucusu '% 1 ' hatasını gönderiyor.|Kanalla|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Ayrıntılı|Yuva kabulü kapandı.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Kritik|Hizmet konağı hatalı.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Ayrıntılı|'% 1 ' için dinleyici açılıyor.|Kanalla|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Ayrıntılı|Dinleyiciyi açma tamamlandı.|Kanalla|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Ayrıntılı|Sunucu en fazla havuza alınmış bağlantı kotasına ulaşıldı.|Kotasının|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Hata|% 2 uzak adresine yönelik Socketıd:% 1 zaman aşımına uğradı.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Uyarı|% 2 uzak adresine yönelik Socketıd:% 1, bir bağlantı sıfırlama hatasına sahipti.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Ayrıntılı|Hizmet güvenliği anlaşması tamamlandı.|Güvenlik|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Hata|Güvenlik anlaşması işleme başarısız oldu.|Güvenlik|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Ayrıntılı|Güvenlik doğrulaması başarılı.|Güvenlik|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Hata|Güvenlik doğrulaması başarısız oldu.|Güvenlik|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Ayrıntılı|% 1 için yuva yineleniyor.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Ayrıntılı|Güvenlik kimliğine bürünme başarılı.|Güvenlik|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Uyarı|Güvenlik kimliğine bürünme başarısız oldu.|Güvenlik|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Uyarı|Http kanalı isteği iptal edildi.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Uyarı|Http kanalı yanıtı iptal edildi.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Uyarı|Http kimlik doğrulaması başarısız oldu.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Ayrıntılı|'% 1 ' Uri 'si için SharedListenerProxy kaydı başladı.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Ayrıntılı|SharedListenerProxy kaydı durdu.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Hata|SharedListenerProxy kaydı, '% 1 ' durumuyla başarısız oldu.|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Hata|Connectionpoolön kimlik Mblet başarısız.|Kanalla|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Ayrıntılı|SslOnAcceptUpgradeStart|Güvenlik|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Ayrıntılı|SslOnAcceptUpgradeStop|Güvenlik|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Ayrıntılı|BinaryMessageEncoder iletiyi kodlamaya başladı.|Kanalla|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Ayrıntılı|MtomMessageEncoder iletiyi kodlamaya başladı.|Kanalla|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Ayrıntılı|TextMessageEncoder iletiyi kodlamaya başladı.|Kanalla|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Ayrıntılı|BinaryMessageEncoder iletinin kodunu çözmeye başladı.|Kanalla|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Ayrıntılı|MtomMessageEncoder iletinin kodunu çözmeye başladı.|Kanalla|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Ayrıntılı|TextMessageEncoder iletinin kodunu çözmeye başladı.|Kanalla|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Bilgiler|Http aktarımı bir ileti almaya başladı.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Ayrıntılı|Socketıd:% 1, '% 3 ' öğesinden okunan '% 2 ' bayt okudu.|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Ayrıntılı|Socketıd:% 1, '% 3 ' öğesinden okunan '% 2 ' bayt okudu.|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Ayrıntılı|Socketıd:% 1, '% 3 ' öğesine '% 2 ' bayt yazıyor.|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Ayrıntılı|Socketıd:% 1, '% 3 ' öğesine '% 2 ' bayt yazıyor.|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Ayrıntılı|SessionID:% 1 alındı bildirimi gönderildi.|Kanalla|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Bilgiler|SessionID:% 1 yeniden bağlanıyor.|Kanalla|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Bilgiler|SessionID:% 1 hata verdi.|Kanalla|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Ayrıntılı|WindowsStreamSecurity güvenlik yükseltmesini başlatıyor.|Güvenlik|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Ayrıntılı|Windows akış güvenliği yükseltmeyi kabul ediyor.|Güvenlik|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Uyarı|Socketıd:% 1 durduruluyor.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Ayrıntılı|HttpGetContext başladı.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Ayrıntılı|İstemci gönderme girişi başladı.|Kanalla|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Ayrıntılı|İstemci gönderme girişi durdu.|Kanalla|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Uyarı|Http Iletisi alma başarısız oldu.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Bilgiler|'% 1 ' ve DistributedIdentifier: '% 2 ' LocalIdentifier ile TransactionScope oluşturuluyor.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Bilgiler|Kodlayıcı tarafından akışlı bir ileti okundu.|Kanalla|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Bilgiler|Kodlayıcı tarafından akışlı bir ileti yazıldı.|Kanalla|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Bilgiler|Kodlayıcı tarafından zaman uyumsuz olarak bir ileti yazıldı.|Kanalla|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Bilgiler|Bufferıd:% 1 temel alınan akışa '% 2 ' bayt yazmayı tamamladı.|Kanalla|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Bilgiler|Kodlayıcı tarafından zaman uyumsuz olarak bir ileti yazıldı.|Kanalla|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Ayrıntılı|Kanal paylaşılan belleği '% 1 ' konumunda oluşturuldu.|Kanalla|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Ayrıntılı|NamedPipe '% 1 ' oluşturuldu.|Kanalla|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Ayrıntılı|İmza doğrulama başladı.|Güvenlik|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Ayrıntılı|İmza doğrulama başarılı oldu.|Güvenlik|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Ayrıntılı|Sarmalanan anahtar şifre çözme başladı.|Güvenlik|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Ayrıntılı|Sarmalanan anahtar şifre çözme başarılı oldu.|Güvenlik|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Ayrıntılı|Şifrelenmiş veri işleme başladı.|Güvenlik|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Ayrıntılı|Şifrelenmiş veri işleme başarılı oldu.|Güvenlik|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Ayrıntılı|Http ileti işleyicisi gelen isteği işlemeye başladı.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Ayrıntılı|Http ileti işleyicisi gelen isteği zaman uyumsuz olarak işlemeye başladı.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Ayrıntılı|Http ileti işleyicisi bir gelen isteği işlemeyi tamamladı.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Uyarı|Http ileti işleyicisi hatalı.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Hata|WebSocket bağlantısı zaman aşımına uğradı.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Ayrıntılı|Http ileti işleyicisi yanıtı işlemeye başladı.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Ayrıntılı|Http ileti işleyicisi yanıtı zaman uyumsuz olarak işlemeye başladı.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Ayrıntılı|Http ileti işleyicisi yanıtı işlemeyi tamamladı.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Ayrıntılı|'% 1 ' için WebSocket bağlantı isteği gönderme başladı.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Ayrıntılı|Websocketıd:% 1 bağlantı isteği gönderildi.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Ayrıntılı|WebSocket bağlantısı kabul etme başladı.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Ayrıntılı|Websocketıd:% 1 bağlantı kabul edildi.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Hata|WebSocket bağlantısı '% 1 ' durum koduyla reddedildi|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Hata|WebSocket bağlantı isteği başarısız oldu: '% 1 '|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Hata|Websocketıd:% 1 bağlantı iptal edildi.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Ayrıntılı|Websocketıd:% 1, '% 3 ' öğesine '% 2 ' bayt yazıyor.|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Ayrıntılı|Websocketıd:% 1 zaman uyumsuz yazma durdu.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Ayrıntılı|Websocketıd:% 1 okuma başladı.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Ayrıntılı|Websocketıd:% 1, '% 3 ' öğesinden '% 2 ' bayt okudu.|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Ayrıntılı|Websocketıd:% 1, '% 2 ' öğesine '% 3 ' kapatma durumuyla kapatma iletisi gönderiyor.|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Ayrıntılı|Websocketıd:% 1, '% 2 ' öğesine '% 3 ' kapatma durumuyla kapatma çıkış iletisi gönderiyor.|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Ayrıntılı|Websocketıd:% 1 bağlantı kapatıldı.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Ayrıntılı|Websocketıd:% 1, '% 2 ' durumuyla bağlantı kapatma iletisi alındı.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Ayrıntılı|'% 1 ' türündeki istemci WebSocket 'inden WebSocketVersion kullanılıyor.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Ayrıntılı|'% 1 ' fabrika türü ile istemci WebSocket 'i oluşturuluyor.|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Bilgiler|XamlServicesLoad Başlat|Leyemedi|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Bilgiler|XamlServicesLoad durdur|Leyemedi|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Bilgiler|CreateWorkflowServiceHost Başlat|Leyemedi|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Bilgiler|CreateWorkflowServiceHost durdur|Leyemedi|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Bilgiler|Hizmet etkinleştirme başlangıcı|Leyemedi|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Bilgiler|Hizmet etkinleştirme durdu|Leyemedi|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Ayrıntılı|Kullanılabilir bellek (bayt):% 1|Kotasının|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Bilgiler|Yönlendirme hizmeti '% 1 ' istemcisini kapatıyor.|Yönlendirme hizmetleri|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Uyarı|'% 1 ' yönlendirme hizmeti istemcisi hata verdi.|Yönlendirme hizmetleri|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Bilgiler|Tek yönlü bir yönlendirme hizmeti iletisi tamamlanıyor.|Yönlendirme hizmetleri|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Hata|Yönlendirme hizmeti, '% 1 ' adresine sahip uç noktada bir iletiyi işlerken başarısız oldu.|Yönlendirme hizmetleri|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Bilgiler|Yönlendirme hizmeti bitiş noktası için istemci oluşturuyor: '% 1 '.|Yönlendirme hizmetleri|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Ayrıntılı|Yönlendirme hizmeti RouteOnHeadersOnly:% 1, SoapProcessingEnabled:% 2, EnsureOrderedDispatch:% 3 ile yapılandırıldı.|Yönlendirme hizmetleri|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Bilgiler|Yönlendirme hizmeti isteği yanıt iletisi tamamlanıyor.|Yönlendirme hizmetleri|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Ayrıntılı|Yönlendirme hizmeti KIMLIĞI '% 1 ' olan iletiyi% 2 bitiş noktası listesine yönlendirdi.|Yönlendirme hizmetleri|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Bilgiler|Yönlendirme hizmeti 'ne yeni bir RoutingConfiguration uygulandı.|Yönlendirme hizmetleri|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Bilgiler|Yönlendirme hizmeti KIMLIK: '% 1 ', eylem: '% 2 ', gelen URL: '% 3 ', Işlem:% 4 ile alınmış bir iletiyi işliyor.|Yönlendirme hizmetleri|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Bilgiler|Yönlendirme hizmeti KIMLIĞI '% 1 ' olan iletiyi [işlem% 2] '% 3 ' öğesine aktarıyor.|Yönlendirme hizmetleri|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Bilgiler|Yönlendirme hizmeti kimliği '% 1 ' olan bir işlem yürütüyor.|Yönlendirme hizmetleri|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Hata|% 1 yönlendirme hizmeti bileşeni bir çift yönlü geri çağırma özel durumuyla karşılaştı.|Yönlendirme hizmetleri|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Bilgiler|KIMLIĞI '% 1 ' olan yönlendirme hizmeti iletisi [işlem% 2], '% 3 ' yedekleme uç noktasına taşındı.|Yönlendirme hizmetleri|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Bilgiler|Yönlendirme hizmeti iletileri işlemek için kimliği '% 1 ' olan yeni bir Işlem oluşturdu.|Yönlendirme hizmetleri|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Uyarı|Yönlendirme hizmeti, '% 1 ' giden istemcisini kapatırken başarısız oldu.|Yönlendirme hizmetleri|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Bilgiler|Yönlendirme hizmeti '% 1 ' eylemi ile bir yanıt iletisi geri gönderiyor.|Yönlendirme hizmetleri|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Uyarı|Yönlendirme hizmeti, '% 1 ' eylemi ile bir hata yanıt iletisi geri gönderiyor.|Yönlendirme hizmetleri|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Ayrıntılı|Yönlendirme hizmeti KIMLIĞI '% 1 ' olan Ileti için ReceiveContext. tamamlamayı çağırıyor.|Yönlendirme hizmetleri|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Uyarı|Yönlendirme hizmeti KIMLIĞI '% 1 ' olan Ileti için ReceiveContext. Abandon 'ı çağırıyor.|Yönlendirme hizmetleri|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Ayrıntılı|Yönlendirme hizmeti, var olan '% 1 ' işlemini kullanarak ileti gönderecek.|Yönlendirme hizmetleri|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Uyarı|Yönlendirme hizmeti '% 1 ' öğesine gönderilirken başarısız oldu.|Yönlendirme hizmetleri|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Bilgiler|Yönlendirme hizmeti MessageFilterTable eşleştirme başlangıcı.|Yönlendirme hizmetleri|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Bilgiler|Yönlendirme hizmeti MessageFilterTable eşleştirme durdu.|Yönlendirme hizmetleri|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Ayrıntılı|Yönlendirme hizmeti kanalda iptali çağırıyor: '% 1 '.|Yönlendirme hizmetleri|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Ayrıntılı|Yönlendirme hizmeti bir özel durumu işledi.|Yönlendirme hizmetleri|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Bilgiler|Yönlendirme hizmeti KIMLIĞI '% 1 [işlem% 2] olan Iletiyi '% 3 ' öğesine başarıyla Iletti.|Yönlendirme hizmetleri|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Ayrıntılı|Taşıma dinleyicisi oturumu '% 1 ' aracılığıyla alındı|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Kritik|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Hata|Hizmet başlatma kanal hatası.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Ayrıntılı|Oturum gönderme başladı.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Uyarı|Bekleyen oturum kuyruğu '% 2 ' bekleyen öğelerle dolu olduğundan, '% 1 ' için oturum gönderme işlemi başarısız oldu.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Ayrıntılı|İleti sırası kaydı başladı.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Hata|İleti kuyruğu kaydı, '% 2 ' Uri 'si için '% 1 ' durumuyla durdu.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Ayrıntılı|'% 1 ' Uri 'si için ileti sırası kaydı başarıyla silindi.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Hata|Uri: '% 1 ' için ileti sırası kaydı '% 2 ' durumuyla başarısız oldu.|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Bilgiler|'% 1 ' Uri 'si için ileti sırası kaydı tamamlandı.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Hata|İleti sırası yuvayı çoğaltamadı.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Ayrıntılı|Messagequeuedupereptedsockettamamlanmıştır|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Ayrıntılı|'% 1 ' Uri 'sinde TCP aktarma dinleyicisi dinlemeye başlıyor.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Ayrıntılı|TCP aktarma dinleyicisi dinliyor.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Hata|Hata kodu:% 1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Bilgiler|Tüm dinleyici kanalı örneklerinin kapatılması tamamlandı.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Hata|Hata kodu:% 1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Hata|Hata kodu:% 1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Ayrıntılı|Bağlandı.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Ayrıntılı|WAS bağlantısı kesildi.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Ayrıntılı|Uri:% 1 üzerinde kanal aktarma dinleyicisi dinlemeye başladı.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Ayrıntılı|Kanal aktarma dinleyicisi dinleme durdu.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Bilgiler|Oturum gönderme başarılı oldu.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Hata|Oturum gönderilemedi.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Kritik|WAS bağlantısı zaman aşımına uğradı.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Ayrıntılı|Yönlendirme tablosu araması başladı.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Ayrıntılı|Yönlendirme tablosu araması tamamlandı.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Ayrıntılı|Bekleyen oturum sırası oranı:% 1/% 2|Kotasının|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Uyarı|İleti, ETW olay boyutunu aştığından günlüğe kaydedilemedi|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Uyarı|DiscoveryClientChannel içinde oluşturulan DiscoveryClient kapatılamadı ve bu nedenle iptal edildi.|Bulma|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Bilgiler|DiscoveryClient kapatılırken ProtocolException gizlendi. Bunun nedeni, bir DiscoveryService 'in DiscoveryClient 'a yanıt gönderilmeye çalışıyor olması olabilir.|Bulma|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Bilgiler|DiscoveryClient bir DiscoveryProxy 'den çok noktaya yayın gizleme iletisi aldı.|Bulma|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Bilgiler|MessageID = '% 2 ' olan bir% 1 iletisi, karşılık gelen% 3 işlemi tamamlandığından DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Uyarı|MessageID = '% 2 ' olan bir% 1 iletisi, geçersiz içeriğe sahip olduğundan bırakıldı.|Bulma|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Uyarı|MessageID = '% 2 ' ve relatesTo = '% 3 ' olan bir% 1 iletisi, karşılık gelen% 4 işlemi tamamlandığı ya da relatesTo değeri geçersiz olduğu için DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Uyarı|MessageID = '% 1 ' olan bir bulma isteği iletisi, geçersiz bir ReplyTo adresine sahip olduğundan bırakıldı.|Bulma|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Uyarı|Bir% 1 iletisi, herhangi bir içeriğe sahip olmadığından bırakıldı.|Bulma|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Uyarı|İleti üst bilgisi gerekli MessageID özelliğini içermediği için bir% 1 iletisi bırakıldı.|Bulma|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Uyarı|MessageID = '% 2 ' olan bir% 1 iletisi, DiscoveryMessageSequence özelliğine sahip olmadığı için DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Uyarı|MessageID = '% 2 ' olan bir% 1 iletisi, ileti üst bilgisi gerekli RelatesTo özelliğini içermediğinden DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Uyarı|MessageID = '% 1 ' olan bir bulma isteği iletisi, ReplyTo adresi olmadığından bırakıldı.|Bulma|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Uyarı|MessageID = '% 2 ' olan bir% 1 iletisi, yinelenen bir öğe olduğu için bırakıldı.|Bulma|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Bilgiler|EndpointAddress = '% 1 ' ve ListenUri = '% 2 ' olan bitiş noktasının bulunabilirliği devre dışı bırakıldı.|Bulma|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Bilgiler|EndpointAddress = '% 1 ' ve ListenUri = '% 2 ' olan bitiş noktasının bulunabilirliği etkinleştirildi.|Bulma|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Ayrıntılı|DiscoveryClientChannel 'da uç noktaları bulmak için bir bulma işlemi başlatıldı.|Bulma|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Uyarı|DiscoveryClientChannel, EndpointAddress = '% 1 ' ve = '% 2 ' aracılığıyla bulunan bir uç nokta ile kanalı oluşturamadı. DiscoveryClientChannel şimdi bulunan bir sonraki kullanılabilir uç noktayı kullanmaya çalışacak.|Bulma|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Uyarı|DiscoveryClientChannel, EndpointAddress = '% 1 ' ve '% 2 ' aracılığıyla bulunan bir uç nokta ile kanalı açamadı. DiscoveryClientChannel şimdi bulunan bir sonraki kullanılabilir uç noktayı kullanmaya çalışacak.|Bulma|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Bilgiler|DiscoveryClientChannel başarıyla bir uç nokta buldu ve kanalı kullanarak açtı. İstemci EndpointAddress = '% 1 ' ve aracılığıyla = '% 2 ' kullanılarak bir hizmete bağlı.|Bulma|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Bilgiler|SynchronizationContext, DiscoveryClientChannel tarafından özgün% 1 değerine sıfırlandı.|Bulma|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Bilgiler|SynchronizationContext, bulma işlemini başlatmadan önce DiscoveryClientChannel tarafından null olarak ayarlandı.|Bulma|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Ayrıntılı|Yedekleri olan% 1 DataContract seri hale getirme başladı.|Serileştirme|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Ayrıntılı|Yedekleri olan DataContract seri hale getirme durdu.|Serileştirme|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Ayrıntılı|Yedekleri olan% 1 DataContract seri durumdan çıkarma başladı.|Serileştirme|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Ayrıntılı|Yedekleri olan DataContract seri durumdan çıkarma durdu.|Serileştirme|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Ayrıntılı|Importknowntypes başladı.|Serileştirme|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Ayrıntılı|Importknowntypes durdu.|Serileştirme|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Ayrıntılı|% 1 için DataContract çözümleyici çözümleme başladı.|Serileştirme|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Ayrıntılı|% 2 için DataContract üretme% 1 yazıcısı başladı.|Serileştirme|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Ayrıntılı|DataContract üretme yazıcı durdu.|Serileştirme|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Ayrıntılı|% 2 için DataContract üretme% 1 okuyucusu başladı.|Serileştirme|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Ayrıntılı|DataContract üretme durdu.|Serileştirme|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Ayrıntılı|% 2 için JSON üretme% 1 okuyucusu başladı.|Serileştirme|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Ayrıntılı|JSON okuyucu üretme durdu.|Serileştirme|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Ayrıntılı|% 2 için JSON üretme% 1 yazıcısı başladı.|Serileştirme|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Ayrıntılı|JSON üretme yazıcı durdu.|Serileştirme|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Ayrıntılı|'% 1 ' için seri hale getirilebilir XML üretme başladı.|Serileştirme|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Ayrıntılı|Seri hale getirilebilir XML üretme durdu.|Serileştirme|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Ayrıntılı|JsonMessageEncoder iletinin kodunu çözmeye başladı.|Kanalla|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Ayrıntılı|JsonMessageEncoder iletiyi kodlamaya başladı.|Kanalla|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Ayrıntılı|SecurityToken ('% 1 ' türü ve '% 2 ' kimliği) doğrulaması başlatıldı.|Güvenlik|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Ayrıntılı|SecurityToken ('% 1 ' türü ve '% 2 ' kimliği) doğrulaması başarılı oldu.|Güvenlik|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Hata|SecurityToken ('% 1 ' türü ve '% 2 ' kimliği) doğrulaması başarısız oldu. %3|Güvenlik|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Ayrıntılı|% 1 veren adının% 2 belirteç kimliğinden alınması başarılı oldu.|Güvenlik|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Hata|% 1 tokenId 'den veren adının alınması başarısız oldu.|Güvenlik|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Ayrıntılı|Federasyon iletisi işleme başladı.|Güvenlik|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Ayrıntılı|Federasyon iletisi işleme başarılı oldu.|Güvenlik|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Ayrıntılı|Form Gönderi başlatıldıktan sonra Federasyon iletisi oluşturuluyor.|Güvenlik|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Ayrıntılı|Form gönderme işleminden Federasyon iletisi oluşturma başarılı oldu.|Güvenlik|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Ayrıntılı|Oturum tanımlama bilgisinden oturum belirteci okuma işlemi başlatıldı.|Güvenlik|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Ayrıntılı|Oturum tanımlama bilgisinden oturum belirteci okuma başarılı oldu.|Güvenlik|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Ayrıntılı|Oturum belirtecinden sorumlu ayarı başlatıldı.|Güvenlik|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Ayrıntılı|Oturum belirtecinden sorumlu ayarı başarılı oldu.|Güvenlik|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Bilgiler|AppDomain boşaltılıyor. AppDomain. FriendlyName% 1, ProcessName% 2, ProcessId% 3.|Altyapı|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Bilgiler|Özel durum işleme.|Altyapı|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Hata|Beklenmeyen bir hata oluştu. Uygulamalar bu hatayı işlemeye çalışmamalıdır. Bu Ingilizce ileti, tanılama amacıyla başarısız oldu:% 1.|Altyapı|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Uyarı|Özel durum oluşturuluyor. % 1 kaynağı.|Altyapı|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Kritik|İşlenmeyen özel durum.|Altyapı|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Kritik|EventLog öğesine yazıldı.|Altyapı|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Hata|EventLog öğesine yazıldı.|Altyapı|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Bilgiler|EventLog öğesine yazıldı.|Altyapı|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Ayrıntılı|EventLog öğesine yazıldı.|Altyapı|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Uyarı|EventLog öğesine yazıldı.|Altyapı|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Uyarı|Özel durum işleme.|Altyapı|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Bilgiler|'% 1 ' URL 'si, '% 2 ' kök öğe türü ile XAML belgesi barındırır. HTTP işleyici türü '% 3 ', bu URL 'ye yapılan tüm istekleri sunacak şekilde çekildi.|Leyemedi|
