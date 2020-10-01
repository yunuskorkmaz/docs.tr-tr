---
title: Çözümleme İzleme Etkinliği Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 4aa8e7a7d22edde02272dc4c3850b5695347b2bb
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609518"
---
# <a name="analytic-trace-event-reference"></a>Çözümleme İzleme Etkinliği Başvurusu
Aşağıdaki tablo, WCF analitik Izleme ile ilişkili olay düzeylerini, tanımlayıcıları ve iletileri tanımlar.  
  
## <a name="event-reference"></a>Olay başvurusu  
  
|Olay Kimliği|Olay düzeyi|Olay Iletisi|Anahtar sözcükler|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](131-bufferpoolallocation.md)|Ayrıntılı|Havuz %1 bayt ayırıyor.|Altyapı|  
|[132 - BufferPoolChangeQuota](132-bufferpoolchangequota.md)|Ayrıntılı|BufferPool %1 boyutunda, kota %2 ile değiştiriliyor.|Altyapı|  
|[133 - ActionItemScheduled](133-actionitemscheduled.md)|Ayrıntılı|GÇ Iş parçacığı Zamanlayıcı geri çağırması çağrıldı.|Altyapı|  
|[134 - ActionItemCallbackInvoked](134-actionitemcallbackinvoked.md)|Ayrıntılı|GÇ Iş parçacığı Zamanlayıcı geri çağırması çağrıldı.|Altyapı|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](201-clientmessageinspectorafterreceiveinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' AfterReceiveReply ' çağırdı.|Sorun giderme, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](202-clientmessageinspectorbeforesendinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' BeforeSendRequest ' çağırdı.|Sorun giderme, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](203-clientparameterinspectoraftercallinvoked.md)|Bilgi|Dağıtıcı bir Clientparameterınspector üzerinde ' AfterCall ' çağırdı. ' %1 ' türünde.|Sorun giderme, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](204-clientparameterinspectorbeforecallinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Clientparameterınspector üzerinde ' Befohatırla ' çağırdı.|Sorun giderme, ServiceModel|  
|[205 - OperationInvoked](205-operationinvoked.md)|Bilgi|Bir OperationInvoker ' %1 ' metodunu çağırdı.|EndToEndMonitoring, sorun giderme, ServiceModel|  
|[206 - ErrorHandlerInvoked](206-errorhandlerinvoked.md)|Bilgi|Dağıtıcı, ' %3 ' türünde bir özel durum ile ' %1 ' türünde bir ErrorHandler çağırdı.  Errorişlenmiş = = ' %2 '.|Sorun giderme, ServiceModel|  
|[207 - FaultProviderInvoked](207-faultproviderinvoked.md)|Bilgi|Dağıtıcı, ' %2 ' türünde bir özel durum ile ' %1 ' türünde bir FaultProvider çağırdı.|Sorun giderme, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](208-messageinspectorafterreceiveinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Messageınspector üzerinde ' AfterReceiveReply ' çağırdı.|Sorun giderme, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](209-messageinspectorbeforesendinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Messageınspector üzerinde ' BeforeSendRequest ' çağırdı.|Sorun giderme, ServiceModel|  
|[210 - MessageThrottleExceeded](210-messagethrottleexceeded.md)|Uyarı|' %2 ' için ' %1 ' kısıtlama sınırına ulaşıldı.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](211-parameterinspectoraftercallinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Parameterınspector üzerinde ' AfterCall ' çağırdı.|Sorun giderme, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](212-parameterinspectorbeforecallinvoked.md)|Bilgi|Dağıtıcı, ' %1 ' türünde bir Parameterınspector üzerinde ' Befohatırla ' çağırdı.|Sorun giderme, ServiceModel|  
|[213 - ServiceHostStarted](213-servicehoststarted.md)|Günlüğe kaydetme her zaman|ServiceHost başlatıldı: ' %1 '.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[214 - OperationCompleted](214-operationcompleted.md)|Bilgi|Bir OperationInvoker ' %1 ' metoduna çağrıyı tamamladı.  Yöntem çağrısı süresi ' %2 ' MS idi.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[215 - MessageReceivedByTransport](215-messagereceivedbytransport.md)|Bilgi|Taşıma, ' %1 ' öğesinden bir ileti aldı.|Sorun giderme, ServiceModel|  
|[216 - MessageSentByTransport](216-messagesentbytransport.md)|Bilgi|Taşıma, ' %1 ' öğesine bir ileti gönderdi.|Sorun giderme, ServiceModel|  
|[217 - ClientOperationPrepared](217-clientoperationprepared.md)|Bilgi|Istemci, ' %2 ' sözleşmesinde tanımlanan ' %1 ' işlemini yürütüyor. İleti, ' %3 ' öğesine gönderilecek.|Sorun giderme, ServiceModel|  
|[218 - ClientOperationCompleted](218-clientoperationcompleted.md)|Bilgi|Istemci, ' %2 ' sözleşmesinde tanımlanan ' %1 ' işlemini yürütmeyi tamamladı. İleti, ' %3 ' öğesine gönderildi.|Sorun giderme, ServiceModel|  
|[219 - ServiceException](219-serviceexception.md)|Hata|İleti işleme sırasında ' %2 ' türünde işlenmeyen bir özel durum oluştu.  Tam özel durum ToString: %1.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[220 - MessageSentToTransport](220-messagesenttotransport.md)|Bilgi|Dağıtıcı, aktarıma bir ileti gönderdi. Bağıntı KIMLIĞI = = ' %1 '.|EndToEndMonitoring, sorun giderme, ServiceModel|  
|[221 - MessageReceivedFromTransport](221-messagereceivedfromtransport.md)|Bilgi|Dağıtıcı aktarımdan bir ileti aldı. Bağıntı KIMLIĞI = = ' %1 '.|EndToEndMonitoring, sorun giderme, ServiceModel|  
|[222 - OperationFailed](222-operationfailed.md)|Uyarı|' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu. Yöntem çağrısı süresi ' %2 ' MS idi.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[223 - OperationFaulted](223-operationfaulted.md)|Uyarı|' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında bir FaultException belirtti. Yöntem çağrısı süresi ' %2 ' MS idi.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](224-messagethrottleatseventypercent.md)|Uyarı|' %2 ' öğesinin ' %1 ' kısıtlama sınırı %70.|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[226 - IdleServicesClosed](226-idleservicesclosed.md)|Günlüğe kaydetme her zaman|Toplam %2 etkinleştirilmiş hizmetten boşta kalan %1 hizmet kapatıldı.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](301-userdefinederroroccurred.md)|Hata|Ad: ' %1 ', başvuru: ' %2 ', yük: %3.|Kullanıcıetkinlikleri, HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[302 - UserDefinedWarningOccurred](302-userdefinedwarningoccurred.md)|Uyarı|Ad: ' %1 ', başvuru: ' %2 ', yük: %3.|Kullanıcıetkinlikleri, HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](303-userdefinedinformationeventoccured.md)|Bilgi|Ad: ' %1 ', başvuru: ' %2 ', yük: %3.|Kullanıcıetkinlikleri, HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|[401- StopSignPostEvent](401-stopsignpostevent.md)|Bilgi|Etkinlik sınırı.|Sorun giderme|  
|[402 - StartSignpostEvent](402-startsignpostevent.md)|Bilgi|Etkinlik sınırı.|Sorun giderme|  
|[403 - SuspendSignpostEvent](403-suspendsignpostevent.md)|Bilgi|Etkinlik sınırı.|Sorun giderme|  
|[404 - ResumeSignpostEvent](404-resumesignpostevent.md)|Bilgi|Etkinlik sınırı.|Sorun giderme|  
|[451 - MessageLogInfo](451-messageloginfo.md)|Bilgi|%1|Sorun giderme, WCFMessageLogging|  
|[452 - MessageLogWarning](452-messagelogwarning.md)|Uyarı|%1|Sorun giderme, WCFMessageLogging|  
|[499 - TransferEmitted](499-transferemitted.md)|Günlüğe kaydetme her zaman|Aktarım olayı yayınlandı.|Sorun giderme, Kullanıcıetkinlikleri, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](501-compilationstart.md)|Bilgi|Derlemeyi başlatın.|Leyemedi|  
|[502 - CompilationStop](502-compilationstop.md)|Bilgi|Derlemeyi bitir.|Leyemedi|  
|[503 - ServiceHostFactoryCreationStart](503-servicehostfactorycreationstart.md)|Bilgi|ServiceHostFactory oluşturmaya başladı.|Leyemedi|  
|[504 - ServiceHostFactoryCreationStop](504-servicehostfactorycreationstop.md)|Bilgi|ServiceHostFactory son oluşturma.|Leyemedi|  
|[505 - CreateServiceHostStart](505-createservicehoststart.md)|Bilgi|CreateServiceHost 'u başlatın.|Leyemedi|  
|[506 - CreateServiceHostStop](506-createservicehoststop.md)|Bilgi|CreateServiceHost 'u sonlandır.|Leyemedi|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](507-hostedtransportconfigurationmanagerconfiginitstart.md)|Bilgi|HostedTransportConfigurationManager yapılandırma başlatmayı Başlat.|Leyemedi|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](508-hostedtransportconfigurationmanagerconfiginitstop.md)|Bilgi|HostedTransportConfigurationManager yapılandırmayı başlatma.|Leyemedi|  
|[509 - ServiceHostOpenStart](509-servicehostopenstart.md)|Bilgi|HostedTransportConfigurationManager yapılandırmayı başlatma.|ServiceHost|  
|[510 - ServiceHostOpenStop](510-servicehostopenstop.md)|Bilgi|ServiceHost açma tamamlandı.|ServiceHost|  
|[513 - WebHostRequestStart](513-webhostrequeststart.md)|Bilgi|' %1 ' AppDomain 'e ait ' %2 ' sanal yoluna sahip istek alındı.|Leyemedi|  
|[514 - WebHostRequestStop](514-webhostrequeststop.md)|Bilgi|WebHostRequest durdu.|Leyemedi|  
|[601 - CBAEntryRead](601-cbaentryread.md)|Ayrıntılı|İşlenen ServiceActivation öğesi göreli adresi: ' %1 ', normalleştirilmiş göreli adres ' %2 '.||  
|[602 - CBAMatchFound](602-cbamatchfound.md)|Ayrıntılı|Gelen istek, adresi ' %1 ' olan bir ServiceActivation öğesiyle eşleşiyor.||  
|[603 - AspNetRoutingService](603-aspnetroutingservice.md)|Ayrıntılı|Gelen istek, %1 adresli ASP.NET rotasında tanımlanan bir WCF hizmeti ile eşleşiyor.|Yönlendirme hizmetleri|  
|[604 - AspNetRoute](604-aspnetroute.md)|Ayrıntılı|ServiceType ' %2 ' ve serviceHostFactoryType ' %3 ' olan ' %1 ' yeni bir ASP.NET rotası eklendi.|Yönlendirme hizmetleri|  
|[605 - IncrementBusyCount](605-incrementbusycount.md)|Ayrıntılı|Incrementbusyıcount çağrıldı. Kaynak: %1|Leyemedi|  
|[606 - DecrementBusyCount](606-decrementbusycount.md)|Ayrıntılı|Çağrılan Mentbuson sayısını azaltır. Kaynak: %1|Leyemedi|  
|[701 - ServiceChannelOpenStart](701-servicechannelopenstart.md)|Ayrıntılı|ServiceChannelOpen başladı.|Leyemedi|  
|[702 - ServiceChannelOpenStop](702-servicechannelopenstop.md)|Bilgi|ServiceChannelOpen tamamlandı.|ServiceModel|  
|[703 - ServiceChannelCallStart](703-servicechannelcallstart.md)|Bilgi|ServiceChannelCall başladı.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](704-servicechannelbegincallstart.md)|Bilgi|ServiceChannel zaman uyumsuz çağrıları başladı.|ServiceModel|  
|[706 - HttpSendMessageStart](706-httpsendmessagestart.md)|Ayrıntılı|Http gönderme Isteği başladı.|HTTP|  
|[707 - HttpSendStop](707-httpsendstop.md)|Ayrıntılı|Http gönderme Isteği durdu.|HTTP|  
|[708 - HttpMessageReceiveStart](708-httpmessagereceivestart.md)|Ayrıntılı|Http aktarımından ileti alındı.|HTTP|  
|[709 - DispatchMessageStart](709-dispatchmessagestart.md)|Bilgi|İleti dağıtma başladı.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](710-httpcontextbeforeprocessauthentication.md)|Ayrıntılı|İleti dağıtma için kimlik doğrulamasını Başlat.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](711-dispatchmessagebeforeauthorization.md)|Ayrıntılı|İleti gönderme için Yetkilendirmeyi başlatın.|ServiceModel|  
|[712 - DispatchMessageStop](712-dispatchmessagestop.md)|Bilgi|İleti gönderme tamamlandı.|ServiceModel|  
|[715 - ClientChannelOpenStart](715-clientchannelopenstart.md)|Bilgi|ServiceChannel açma başladı.|ServiceModel|  
|[716 - ClientChannelOpenStop](716-clientchannelopenstop.md)|Bilgi|ServiceChannel açma durdu.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](717-httpsendstreamedmessagestart.md)|Bilgi|Http gönderme akışı iletisi başlatıldı.|HTTP|  
|[1400 - ChannelInitializationTimeout](1400-channelinitializationtimeout.md)|Hata|%1|ServiceModel|  
|[1401 - CloseTimeout](1401-closetimeout.md)|Hata|%1|ServiceModel|  
|[1402 - IdleTimeout](1402-idletimeout.md)|Hata|%1 bağlantı havuzu anahtarı: %2|ServiceModel|  
|[1403 - LeaseTimeout](1403-leasetimeout.md)|Bilgi|%1 bağlantı havuzu anahtarı: %2|ServiceModel|  
|[1405 - OpenTimeout](1405-opentimeout.md)|Hata|%1|ServiceModel|  
|[1406 - ReceiveTimeout](1406-receivetimeout.md)|Hata|%1|ServiceModel|  
|[1407 - SendTimeout](1407-sendtimeout.md)|Hata|%1|ServiceModel|  
|[1409 - InactivityTimeout](1409-inactivitytimeout.md)|Bilgi|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](1416-maxreceivedmessagesizeexceeded.md)|Hata|%1|Kota|  
|[1417 - MaxSentMessageSizeExceeded](1417-maxsentmessagesizeexceeded.md)|Hata|%1|Kota|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](1418-maxoutboundconnectionsperendpointexceeded.md)|Bilgi|%1|Kota|  
|[1419 - MaxPendingConnectionsExceeded](1419-maxpendingconnectionsexceeded.md)|Bilgi|%1|Kota|  
|[1420 - ReaderQuotaExceeded](1420-readerquotaexceeded.md)|Hata|%1|Kota|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Hata|%1|Kota|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](1423-negotiatetokenauthenticatorstatecacheratio.md)|Ayrıntılı|Anlaşma belirteci Doğrulayıcı durumu önbellek oranı: %1/%2|Kota|  
|[1424 - SecuritySessionRatio](1424-securitysessionratio.md)|Ayrıntılı|Güvenlik oturumu oranı: %1/%2|Kota|  
|[1430 - PendingConnectionsRatio](1430-pendingconnectionsratio.md)|Ayrıntılı|Bekleyen bağlantı oranı: %1/%2|Kota|  
|[1431 - ConcurrentCallsRatio](1431-concurrentcallsratio.md)|Ayrıntılı|Eşzamanlı oturumların oranı: %1/%2|Kota|  
|[1432 - ConcurrentSessionsRatio](1432-concurrentsessionsratio.md)|Ayrıntılı|Eşzamanlı oturumların oranı: %1/%2|Kota|  
|[1433 - OutboundConnectionsPerEndpointRatio](1433-outboundconnectionsperendpointratio.md)|Ayrıntılı|Uç nokta başına giden bağlantı oranı: %1/%2|Kota|  
|[1436 - PendingMessagesPerChannelRatio](1436-pendingmessagesperchannelratio.md)|Ayrıntılı|Kanal başına bekleyen ileti oranı: %1/%2|Kota|  
|[1438 - ConcurrentInstancesRatio](1438-concurrentinstancesratio.md)|Ayrıntılı|Eşzamanlı örneklerin oranı: %1/%2|Kota|  
|[1439 - PendingAcceptsAtZero](1439-pendingacceptsatzero.md)|Bilgi|Bekleyen sıfır kabul|Kota|  
|[1441 - MaxSessionSizeReached](1441-maxsessionsizereached.md)|Uyarı|%1|Kota|  
|[1442 - ReceiveRetryCountReached](1442-receiveretrycountreached.md)|Uyarı|Kimliği ' %1 ' olan MSMQ iletisinde alma yeniden deneme sayısına ulaşıldı|Kota|  
|[1443 - MaxRetryCyclesExceededMsmq](1443-maxretrycyclesexceededmsmq.md)|Hata|Kimliği ' %1 ' olan MSMQ iletisinde en fazla yeniden deneme döngüsü aşıldı|Kota|  
|[1445 - ReadPoolMiss](1445-readpoolmiss.md)|Ayrıntılı|Yeni ' %1 ' oluşturuldu|Kota|  
|[1446 - WritePoolMiss](1446-writepoolmiss.md)|Ayrıntılı|Yeni ' %1 ' oluşturuldu|Kota|  
|[1451 - MaxRetryCyclesExceeded](1451-maxretrycyclesexceeded.md)|Hata|%1|Kota|  
|[3300 - ReceiveContextCompleteFailed](3300-receivecontextcompletefailed.md)|Uyarı|%1 işlemi tamamlanamıyor.|Kanal|  
|[3301 - ReceiveContextAbandonFailed](3301-receivecontextabandonfailed.md)|Uyarı|%1 bırakılamadı.|Kanal|  
|[3303 - ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Uyarı|Alma bağlamı hatalı.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Bilgi|%1, %2 özel durumuyla bırakıldı.|Kanal|  
|[3305 - ClientBaseCachedChannelFactoryCount](3305-clientbasecachedchannelfactorycount.md)|Bilgi|Önbelleğe alınan kanal fabrikası sayısı: ' %1 '.  En fazla ' %2 ' kanal fabrikası önbelleğe alınabilir.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](3306-clientbasechannelfactoryagedoutofcache.md)|Bilgi|Önbellek, ' %1 ' sınırına ulaştığından önbellekten eski bir kanal fabrikası kullanıldı.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](3307-clientbasechannelfactorycachehit.md)|Bilgi|Önbellekte bulunan eşleşen kanal fabrikası kullanıldı.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](3308-clientbaseusinglocalchannelfactory.md)|Bilgi|Önbellekten kanal fabrikası kullanmıyor, yani örnek için önbelleğe alma devre dışı.|ServiceModel|  
|[3309 - QueryCompositionExecuted](3309-querycompositionexecuted.md)|Bilgi|' %1 ' kullanılarak sorgu oluşturma Istek Uri 'Si üzerinde yürütüldü: ' %2 '.|ServiceModel|  
|[3310 - DispatchFailed](3310-dispatchfailed.md)|Hata|' %1 ' işlemi hatalarla dağıtıldı.|ServiceModel|  
|[3311 - DispatchSuccessful](3311-dispatchsuccessful.md)|Bilgi|' %1 ' işlemi başarıyla dağıtıldı.|ServiceModel|  
|[3312 - MessageReadByEncoder](3312-messagereadbyencoder.md)|Bilgi|Kodlayıcı tarafından boyutu ' %1 ' bayt olan bir ileti okundu.|Kanal|  
|[3312 - MessageReadByEncoder](3312-messagereadbyencoder.md)|Bilgi|Kodlayıcı tarafından boyutu ' %1 ' bayt olan bir ileti yazıldı.|Kanal|  
|[3314 - SessionIdleTimeout](3314-sessionidletimeout.md)|Hata|' %1 ' Uri 'sine yönelik boştaki kanal için oturum iptal ediliyor.|ServiceModel|  
|[3319 - SocketAcceptEnqueued](3319-socketacceptenqueued.md)|Ayrıntılı|Bağlantı kabulü başladı.|TCP|  
|[3320 - SocketAccepted](3320-socketaccepted.md)|Ayrıntılı|Listenerıd: %1 kabul edilen Socketıd: %2.|TCP|  
|[3321 - ConnectionPoolMiss](3321-connectionpoolmiss.md)|Ayrıntılı|%1 havuzu için kullanılabilir bağlantı yok ve %2 meşgul bağlantı yok.|Kanal|  
|[3322 - DispatchFormatterDeserializeRequestStart](3322-dispatchformatterdeserializerequeststart.md)|Ayrıntılı|Dağıtıcı istek iletisini seri durumdan çıkarmayı başlattı.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](3323-dispatchformatterdeserializerequeststop.md)|Ayrıntılı|Dağıtıcı istek iletisini seri durumdan çıkarmayı tamamladı.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](3324-dispatchformatterserializereplystart.md)|Ayrıntılı|Dağıtıcı yanıt iletisini Serileştirmeyi başlattı.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](3325-dispatchformatterserializereplystop.md)|Ayrıntılı|Dağıtıcı yanıt iletisini Serileştirmeyi tamamladı.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](3326-clientformatterserializerequeststart.md)|Ayrıntılı|İstemci isteği serileştirme başladı.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](3327-clientformatterserializerequeststop.md)|Ayrıntılı|İstemci istek iletisini Serileştirmeyi tamamladı.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](3328-clientformatterdeserializereplystart.md)|Ayrıntılı|İstemci yanıt iletisini seri durumdan çıkarmayı başlattı.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](3329-clientformatterdeserializereplystop.md)|Ayrıntılı|İstemci yanıt iletisini seri durumdan çıkarmayı tamamladı.|ServiceModel|  
|[3330 - SecurityNegotiationStart](3330-securitynegotiationstart.md)|Ayrıntılı|Güvenlik anlaşması başladı.|Güvenlik|  
|[3331 - SecurityNegotiationStop](3331-securitynegotiationstop.md)|Ayrıntılı|Güvenlik anlaşması tamamlandı.|Güvenlik|  
|[3332 - SecurityTokenProviderOpened](3332-securitytokenprovideropened.md)|Ayrıntılı|SecurityTokenProvider açma tamamlandı.|Güvenlik|  
|[3333 - OutgoingMessageSecured](3333-outgoingmessagesecured.md)|Ayrıntılı|Giden ileti güvenli hale getirildi.|Güvenlik|  
|[3334 - IncomingMessageVerified](3334-incomingmessageverified.md)|Ayrıntılı|Gelen ileti doğrulandı.|Güvenlik ServiceModel|  
|[3335 - GetServiceInstanceStart](3335-getserviceinstancestart.md)|Ayrıntılı|Hizmet örneği alımı başlatıldı.|ServiceModel|  
|[3336 - GetServiceInstanceStop](3336-getserviceinstancestop.md)|Ayrıntılı|Hizmet örneği alındı.|ServiceModel|  
|[3337 - ChannelReceiveStart](3337-channelreceivestart.md)|Ayrıntılı|Channelhandlerıd: %1-Ileti alma döngüsü başladı.|Kanal|  
|[3338 - ChannelReceiveStop](3338-channelreceivestop.md)|Ayrıntılı|Channelhandlerıd: %1-Ileti alma döngüsü durdu.|Kanal|  
|[3339 - ChannelFactoryCreated](3339-channelfactorycreated.md)|Ayrıntılı|ChannelFactory oluşturuldu.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](3340-pipeconnectionacceptstart.md)|Ayrıntılı|Kanal bağlantısı kabulü %1 tarihinde başladı.|Kanal|  
|[3341 - PipeConnectionAcceptStop](3341-pipeconnectionacceptstop.md)|Ayrıntılı|Kanal bağlantısı kabul edildi.|Kanal|  
|[3342 - EstablishConnectionStart](3342-establishconnectionstart.md)|Ayrıntılı|%1 için bağlantı kurma işlemi başladı.|Kanal|  
|[3343 - EstablishConnectionStop](3343-establishconnectionstop.md)|Ayrıntılı|Bağlantı oluşturuldu.|Kanal|  
|[3345 - SessionPreambleUnderstood](3345-sessionpreambleunderstood.md)|Ayrıntılı|' %1 ' için oturum girişi anlaşıldı.|Kanal|  
|[3346 - ConnectionReaderSendFault](3346-connectionreadersendfault.md)|Hata|Bağlantı okuyucusu ' %1 ' hatasını gönderiyor.|Kanal|  
|[3347 - SocketAcceptClosed](3347-socketacceptclosed.md)|Ayrıntılı|Yuva kabulü kapandı.|TCP|  
|[3348 - ServiceHostFaulted](3348-servicehostfaulted.md)|Kritik|Hizmet konağı hatalı.|TCP|  
|[3349 - ListenerOpenStart](3349-listeneropenstart.md)|Ayrıntılı|' %1 ' için dinleyici açılıyor.|Kanal|  
|[3350 - ListenerOpenStop](3350-listeneropenstop.md)|Ayrıntılı|Dinleyiciyi açma tamamlandı.|Kanal|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](3351-servermaxpooledconnectionsquotareached.md)|Ayrıntılı|Sunucu en fazla havuza alınmış bağlantı kotasına ulaşıldı.|Kota|  
|[3352 - TcpConnectionTimedOut](3352-tcpconnectiontimedout.md)|Hata|%2 uzak adresine yönelik Socketıd: %1 zaman aşımına uğradı.|TCP|  
|[3353 - TcpConnectionResetError](3353-tcpconnectionreseterror.md)|Uyarı|%2 uzak adresine yönelik Socketıd: %1, bir bağlantı sıfırlama hatasına sahipti.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](3354-servicesecuritynegotiationcompleted.md)|Ayrıntılı|Hizmet güvenliği anlaşması tamamlandı.|Güvenlik|  
|[3355 - SecurityNegotiationProcessingFailure](3355-securitynegotiationprocessingfailure.md)|Hata|Güvenlik anlaşması işleme başarısız oldu.|Güvenlik|  
|[3356 - SecurityIdentityVerificationSuccess](3356-securityidentityverificationsuccess.md)|Ayrıntılı|Güvenlik doğrulaması başarılı.|Güvenlik|  
|[3357 - SecurityIdentityVerificationFailure](3357-securityidentityverificationfailure.md)|Hata|Güvenlik doğrulaması başarısız oldu.|Güvenlik|  
|[3358 - PortSharingDuplicatedSocket](3358-portsharingduplicatedsocket.md)|Ayrıntılı|%1 için yuva yineleniyor.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](3359-securityimpersonationsuccess.md)|Ayrıntılı|Güvenlik kimliğine bürünme başarılı.|Güvenlik|  
|[3360 - SecurityImpersonationFailure](3360-securityimpersonationfailure.md)|Uyarı|Güvenlik kimliğine bürünme başarısız oldu.|Güvenlik|  
|[3361 - HttpChannelRequestAborted](3361-httpchannelrequestaborted.md)|Uyarı|Http kanalı isteği iptal edildi.|HTTP|  
|[3362 - HttpChannelResponseAborted](3362-httpchannelresponseaborted.md)|Uyarı|Http kanalı yanıtı iptal edildi.|HTTP|  
|[3363 - HttpAuthFailed](3363-httpauthfailed.md)|Uyarı|Http kimlik doğrulaması başarısız oldu.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](3364-sharedlistenerproxyregisterstart.md)|Ayrıntılı|' %1 ' Uri 'si için SharedListenerProxy kaydı başladı.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](3365-sharedlistenerproxyregisterstop.md)|Ayrıntılı|SharedListenerProxy kaydı durdu.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](3366-sharedlistenerproxyregisterfailed.md)|Hata|SharedListenerProxy kaydı, ' %1 ' durumuyla başarısız oldu.|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](3367-connectionpoolpreamblefailed.md)|Hata|Connectionpoolön kimlik Mblet başarısız.|Kanal|  
|[3368 - SslOnInitiateUpgrade](3368-ssloninitiateupgrade.md)|Ayrıntılı|SslOnAcceptUpgradeStart|Güvenlik|  
|[3369 - SslOnAcceptUpgrade](3369-sslonacceptupgrade.md)|Ayrıntılı|SslOnAcceptUpgradeStop|Güvenlik|  
|[3370 - BinaryMessageEncodingStart](3370-binarymessageencodingstart.md)|Ayrıntılı|BinaryMessageEncoder iletiyi kodlamaya başladı.|Kanal|  
|[3371 - MtomMessageEncodingStart](3371-mtommessageencodingstart.md)|Ayrıntılı|MtomMessageEncoder iletiyi kodlamaya başladı.|Kanal|  
|[3372 - TextMessageEncodingStart](3372-textmessageencodingstart.md)|Ayrıntılı|TextMessageEncoder iletiyi kodlamaya başladı.|Kanal|  
|[3373 - BinaryMessageDecodingStart](3373-binarymessagedecodingstart.md)|Ayrıntılı|BinaryMessageEncoder iletinin kodunu çözmeye başladı.|Kanal|  
|[3374 - MtomMessageDecodingStart](3374-mtommessagedecodingstart.md)|Ayrıntılı|MtomMessageEncoder iletinin kodunu çözmeye başladı.|Kanal|  
|[3375 - TextMessageDecodingStart](3375-textmessagedecodingstart.md)|Ayrıntılı|TextMessageEncoder iletinin kodunu çözmeye başladı.|Kanal|  
|[3376 - HttpResponseReceiveStart](3376-httpresponsereceivestart.md)|Bilgi|Http aktarımı bir ileti almaya başladı.|HTTP|  
|[3377 - SocketReadStop](3377-socketreadstop.md)|Ayrıntılı|Socketıd: %1, ' %3 ' öğesinden okunan ' %2 ' bayt okudu.|TCP|  
|[3378 - SocketAsyncReadStop](3378-socketasyncreadstop.md)|Ayrıntılı|Socketıd: %1, ' %3 ' öğesinden okunan ' %2 ' bayt okudu.|TCP|  
|[3379 - SocketWriteStart](3379-socketwritestart.md)|Ayrıntılı|Socketıd: %1, ' %3 ' öğesine ' %2 ' bayt yazıyor.|TCP|  
|[3380 - SocketAsyncWriteStart](3380-socketasyncwritestart.md)|Ayrıntılı|Socketıd: %1, ' %3 ' öğesine ' %2 ' bayt yazıyor.|TCP|  
|[3381 - SequenceAcknowledgementSent](3381-sequenceacknowledgementsent.md)|Ayrıntılı|SessionID: %1 alındı bildirimi gönderildi.|Kanal|  
|[3382 - ClientReliableSessionReconnect](3382-clientreliablesessionreconnect.md)|Bilgi|SessionID: %1 yeniden bağlanıyor.|Kanal|  
|[3383 - ReliableSessionChannelFaulted](3383-reliablesessionchannelfaulted.md)|Bilgi|SessionID: %1 hata verdi.|Kanal|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](3384-windowsstreamsecurityoninitiateupgrade.md)|Ayrıntılı|WindowsStreamSecurity güvenlik yükseltmesini başlatıyor.|Güvenlik|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](3385-windowsstreamsecurityonacceptupgrade.md)|Ayrıntılı|Windows akış güvenliği yükseltmeyi kabul ediyor.|Güvenlik|  
|[3386 - SocketConnectionAbort](3386-socketconnectionabort.md)|Uyarı|Socketıd: %1 durduruluyor.|TCP|  
|[3388 - HttpGetContextStart](3388-httpgetcontextstart.md)|Ayrıntılı|HttpGetContext başladı.|HTTP|  
|[3389 - ClientSendPreambleStart](3389-clientsendpreamblestart.md)|Ayrıntılı|İstemci gönderme girişi başladı.|Kanal|  
|[3390 - ClientSendPreambleStop](3390-clientsendpreamblestop.md)|Ayrıntılı|İstemci gönderme girişi durdu.|Kanal|  
|[3391 - HttpMessageReceiveFailed](3391-httpmessagereceivefailed.md)|Uyarı|Http Iletisi alma başarısız oldu.|HTTP|  
|[3392 - TransactionScopeCreate](3392-transactionscopecreate.md)|Bilgi|' %1 ' ve DistributedIdentifier: ' %2 ' LocalIdentifier ile TransactionScope oluşturuluyor.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](3393-streamedmessagereadbyencoder.md)|Bilgi|Kodlayıcı tarafından akışlı bir ileti okundu.|Kanal|  
|[3394 - StreamedMessageWrittenByEncoder](3394-streamedmessagewrittenbyencoder.md)|Bilgi|Kodlayıcı tarafından akışlı bir ileti yazıldı.|Kanal|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](3395-messagewrittenasynchronouslybyencoder.md)|Bilgi|Kodlayıcı tarafından zaman uyumsuz olarak bir ileti yazıldı.|Kanal|  
|[3396 - BufferedAsyncWriteStart](3396-bufferedasyncwritestart.md)|Bilgi|Bufferıd: %1 temel alınan akışa ' %2 ' bayt yazmayı tamamladı.|Kanal|  
|[3397 - BufferedAsyncWriteStop](3397-bufferedasyncwritestop.md)|Bilgi|Kodlayıcı tarafından zaman uyumsuz olarak bir ileti yazıldı.|Kanal|  
|[3398 - PipeSharedMemoryCreated](3398-pipesharedmemorycreated.md)|Ayrıntılı|Kanal paylaşılan belleği ' %1 ' konumunda oluşturuldu.|Kanal|  
|[3399 - NamedPipeCreated](3399-namedpipecreated.md)|Ayrıntılı|NamedPipe ' %1 ' oluşturuldu.|Kanal|  
|[3401 - SignatureVerificationStart](3401-signatureverificationstart.md)|Ayrıntılı|İmza doğrulama başladı.|Güvenlik|  
|[3402 - SignatureVerificationSuccess](3402-signatureverificationsuccess.md)|Ayrıntılı|İmza doğrulama başarılı oldu.|Güvenlik|  
|[3403 - WrappedKeyDecryptionStart](3403-wrappedkeydecryptionstart.md)|Ayrıntılı|Sarmalanan anahtar şifre çözme başladı.|Güvenlik|  
|[3404 - WrappedKeyDecryptionSuccess](3404-wrappedkeydecryptionsuccess.md)|Ayrıntılı|Sarmalanan anahtar şifre çözme başarılı oldu.|Güvenlik|  
|[3405 - EncryptedDataProcessingStart](3405-encrypteddataprocessingstart.md)|Ayrıntılı|Şifrelenmiş veri işleme başladı.|Güvenlik|  
|[3406 - EncryptedDataProcessingSuccess](3406-encrypteddataprocessingsuccess.md)|Ayrıntılı|Şifrelenmiş veri işleme başarılı oldu.|Güvenlik|  
|[3407 - HttpPipelineProcessInboundRequestStart](3407-httppipelineprocessinboundrequeststart.md)|Ayrıntılı|Http ileti işleyicisi gelen isteği işlemeye başladı.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](3408-httppipelinebeginprocessinboundrequeststart.md)|Ayrıntılı|Http ileti işleyicisi gelen isteği zaman uyumsuz olarak işlemeye başladı.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](3409-httppipelineprocessinboundrequeststop.md)|Ayrıntılı|Http ileti işleyicisi bir gelen isteği işlemeyi tamamladı.|HTTP|  
|[3410 - HttpPipelineFaulted](3410-httppipelinefaulted.md)|Uyarı|Http ileti işleyicisi hatalı.|HTTP|  
|[3411 - HttpPipelineTimeoutException](3411-httppipelinetimeoutexception.md)|Hata|WebSocket bağlantısı zaman aşımına uğradı.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](3412-httppipelineprocessresponsestart.md)|Ayrıntılı|Http ileti işleyicisi yanıtı işlemeye başladı.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](3413-httppipelinebeginprocessresponsestart.md)|Ayrıntılı|Http ileti işleyicisi yanıtı zaman uyumsuz olarak işlemeye başladı.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](3414-httppipelineprocessresponsestop.md)|Ayrıntılı|Http ileti işleyicisi yanıtı işlemeyi tamamladı.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](3415-websocketconnectionrequestsendstart.md)|Ayrıntılı|' %1 ' için WebSocket bağlantı isteği gönderme başladı.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](3416-websocketconnectionrequestsendstop.md)|Ayrıntılı|Websocketıd: %1 bağlantı isteği gönderildi.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](3417-websocketconnectionacceptstart.md)|Ayrıntılı|WebSocket bağlantısı kabul etme başladı.|HTTP|  
|[3418 - WebSocketConnectionAccepted](3418-websocketconnectionaccepted.md)|Ayrıntılı|Websocketıd: %1 bağlantı kabul edildi.|HTTP|  
|[3419 - WebSocketConnectionDeclined](3419-websocketconnectiondeclined.md)|Hata|WebSocket bağlantısı ' %1 ' durum koduyla reddedildi|HTTP|  
|[3420 - WebSocketConnectionFailed](3420-websocketconnectionfailed.md)|Hata|WebSocket bağlantı isteği başarısız oldu: ' %1 '|HTTP|  
|[3421 - WebSocketConnectionAborted](3421-websocketconnectionaborted.md)|Hata|Websocketıd: %1 bağlantı iptal edildi.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](3422-websocketasyncwritestart.md)|Ayrıntılı|Websocketıd: %1, ' %3 ' öğesine ' %2 ' bayt yazıyor.|HTTP|  
|[3423 - WebSocketAsyncWriteStop](3423-websocketasyncwritestop.md)|Ayrıntılı|Websocketıd: %1 zaman uyumsuz yazma durdu.|HTTP|  
|[3424 - WebSocketAsyncReadStart](3424-websocketasyncreadstart.md)|Ayrıntılı|Websocketıd: %1 okuma başladı.|HTTP|  
|[3425 - WebSocketAsyncReadStop](3425-websocketasyncreadstop.md)|Ayrıntılı|Websocketıd: %1, ' %3 ' öğesinden ' %2 ' bayt okudu.|HTTP|  
|[3426 - WebSocketCloseSent](3426-websocketclosesent.md)|Ayrıntılı|Websocketıd: %1, ' %2 ' öğesine ' %3 ' kapatma durumuyla kapatma iletisi gönderiyor.|HTTP|  
|[3427 - WebSocketCloseOutputSent](3427-websocketcloseoutputsent.md)|Ayrıntılı|Websocketıd: %1, ' %2 ' öğesine ' %3 ' kapatma durumuyla kapatma çıkış iletisi gönderiyor.|HTTP|  
|[3428 - WebSocketConnectionClosed](3428-websocketconnectionclosed.md)|Ayrıntılı|Websocketıd: %1 bağlantı kapatıldı.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](3429-websocketclosestatusreceived.md)|Ayrıntılı|Websocketıd: %1, ' %2 ' durumuyla bağlantı kapatma iletisi alındı.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](3430-websocketuseversionfromclientwebsocketfactory.md)|Ayrıntılı|' %1 ' türündeki istemci WebSocket 'inden WebSocketVersion kullanılıyor.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](3431-websocketcreateclientwebsocketwithfactory.md)|Ayrıntılı|' %1 ' fabrika türü ile istemci WebSocket 'i oluşturuluyor.|HTTP|  
|[3553 - XamlServicesLoadStart](3553-xamlservicesloadstart.md)|Bilgi|XamlServicesLoad Başlat|Leyemedi|  
|[3554 - XamlServicesLoadStop](3554-xamlservicesloadstop.md)|Bilgi|XamlServicesLoad durdur|Leyemedi|  
|[3555 - CreateWorkflowServiceHostStart](3555-createworkflowservicehoststart.md)|Bilgi|CreateWorkflowServiceHost Başlat|Leyemedi|  
|[3556 - CreateWorkflowServiceHostStop](3556-createworkflowservicehoststop.md)|Bilgi|CreateWorkflowServiceHost durdur|Leyemedi|  
|[3558 - ServiceActivationStart](3558-serviceactivationstart.md)|Bilgi|Hizmet etkinleştirme başlangıcı|Leyemedi|  
|[3559 - ServiceActivationStop](3559-serviceactivationstop.md)|Bilgi|Hizmet etkinleştirme durdu|Leyemedi|  
|[3560 - ServiceActivationAvailableMemory](3560-serviceactivationavailablememory.md)|Ayrıntılı|Kullanılabilir bellek (bayt): %1|Kota|  
|[3800 - RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Bilgi|Yönlendirme hizmeti ' %1 ' istemcisini kapatıyor.|Yönlendirme hizmetleri|  
|[3800 - RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Uyarı|' %1 ' yönlendirme hizmeti istemcisi hata verdi.|Yönlendirme hizmetleri|  
|[3802 - RoutingServiceCompletingOneWay](3802-routingservicecompletingoneway.md)|Bilgi|Tek yönlü bir yönlendirme hizmeti iletisi tamamlanıyor.|Yönlendirme hizmetleri|  
|[3803 - RoutingServiceProcessingFailure](3803-routingserviceprocessingfailure.md)|Hata|Yönlendirme hizmeti, ' %1 ' adresine sahip uç noktada bir iletiyi işlerken başarısız oldu.|Yönlendirme hizmetleri|  
|[3804 - RoutingServiceCreatingClientForEndpoint](3804-routingservicecreatingclientforendpoint.md)|Bilgi|Yönlendirme hizmeti bitiş noktası için istemci oluşturuyor: ' %1 '.|Yönlendirme hizmetleri|  
|[3805 - RoutingServiceDisplayConfig](3805-routingservicedisplayconfig.md)|Ayrıntılı|Yönlendirme hizmeti RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3 ile yapılandırıldı.|Yönlendirme hizmetleri|  
|[3807 - RoutingServiceCompletingTwoWay](3807-routingservicecompletingtwoway.md)|Bilgi|Yönlendirme hizmeti isteği yanıt iletisi tamamlanıyor.|Yönlendirme hizmetleri|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](3809-routingservicemessageroutedtoendpoints.md)|Ayrıntılı|Yönlendirme hizmeti KIMLIĞI ' %1 ' olan iletiyi %2 bitiş noktası listesine yönlendirdi.|Yönlendirme hizmetleri|  
|[3810 - RoutingServiceConfigurationApplied](3810-routingserviceconfigurationapplied.md)|Bilgi|Yönlendirme hizmeti 'ne yeni bir RoutingConfiguration uygulandı.|Yönlendirme hizmetleri|  
|[3815 - RoutingServiceProcessingMessage](3815-routingserviceprocessingmessage.md)|Bilgi|Yönlendirme hizmeti KIMLIK: ' %1 ', eylem: ' %2 ', gelen URL: ' %3 ', Işlem: %4 ile alınmış bir iletiyi işliyor.|Yönlendirme hizmetleri|  
|[3816 - RoutingServiceTransmittingMessage](3816-routingservicetransmittingmessage.md)|Bilgi|Yönlendirme hizmeti KIMLIĞI ' %1 ' olan iletiyi [işlem %2] ' %3 ' öğesine aktarıyor.|Yönlendirme hizmetleri|  
|[3817 - RoutingServiceCommittingTransaction](3817-routingservicecommittingtransaction.md)|Bilgi|Yönlendirme hizmeti kimliği ' %1 ' olan bir işlem yürütüyor.|Yönlendirme hizmetleri|  
|[3818 - RoutingServiceDuplexCallbackException](3818-routingserviceduplexcallbackexception.md)|Hata|%1 yönlendirme hizmeti bileşeni bir çift yönlü geri çağırma özel durumuyla karşılaştı.|Yönlendirme hizmetleri|  
|[3819 - RoutingServiceMovedToBackup](3819-routingservicemovedtobackup.md)|Bilgi|KIMLIĞI ' %1 ' olan yönlendirme hizmeti iletisi [işlem %2], ' %3 ' yedekleme uç noktasına taşındı.|Yönlendirme hizmetleri|  
|[3820 - RoutingServiceCreatingTransaction](3820-routingservicecreatingtransaction.md)|Bilgi|Yönlendirme hizmeti iletileri işlemek için kimliği ' %1 ' olan yeni bir Işlem oluşturdu.|Yönlendirme hizmetleri|  
|[3821 - RoutingServiceCloseFailed](3821-routingserviceclosefailed.md)|Uyarı|Yönlendirme hizmeti, ' %1 ' giden istemcisini kapatırken başarısız oldu.|Yönlendirme hizmetleri|  
|[3822 - RoutingServiceSendingResponse](3822-routingservicesendingresponse.md)|Bilgi|Yönlendirme hizmeti ' %1 ' eylemi ile bir yanıt iletisi geri gönderiyor.|Yönlendirme hizmetleri|  
|[3823 - RoutingServiceSendingFaultResponse](3823-routingservicesendingfaultresponse.md)|Uyarı|Yönlendirme hizmeti, ' %1 ' eylemi ile bir hata yanıt iletisi geri gönderiyor.|Yönlendirme hizmetleri|  
|[3824 - RoutingServiceCompletingReceiveContext](3824-routingservicecompletingreceivecontext.md)|Ayrıntılı|Yönlendirme hizmeti KIMLIĞI ' %1 ' olan Ileti için ReceiveContext. tamamlamayı çağırıyor.|Yönlendirme hizmetleri|  
|[3825 - RoutingServiceAbandoningReceiveContext](3825-routingserviceabandoningreceivecontext.md)|Uyarı|Yönlendirme hizmeti KIMLIĞI ' %1 ' olan Ileti için ReceiveContext. Abandon 'ı çağırıyor.|Yönlendirme hizmetleri|  
|[3826 - RoutingServiceUsingExistingTransaction](3826-routingserviceusingexistingtransaction.md)|Ayrıntılı|Yönlendirme hizmeti, var olan ' %1 ' işlemini kullanarak ileti gönderecek.|Yönlendirme hizmetleri|  
|[3827 - RoutingServiceTransmitFailed](3827-routingservicetransmitfailed.md)|Uyarı|Yönlendirme hizmeti ' %1 ' öğesine gönderilirken başarısız oldu.|Yönlendirme hizmetleri|  
|[3828 - RoutingServiceFilterTableMatchStart](3828-routingservicefiltertablematchstart.md)|Bilgi|Yönlendirme hizmeti MessageFilterTable eşleştirme başlangıcı.|Yönlendirme hizmetleri|  
|[3829 - RoutingServiceFilterTableMatchStop](3829-routingservicefiltertablematchstop.md)|Bilgi|Yönlendirme hizmeti MessageFilterTable eşleştirme durdu.|Yönlendirme hizmetleri|  
|[3830 - RoutingServiceAbortingChannel](3830-routingserviceabortingchannel.md)|Ayrıntılı|Yönlendirme hizmeti kanalda iptali çağırıyor: ' %1 '.|Yönlendirme hizmetleri|  
|[3831 - RoutingServiceHandledException](3831-routingservicehandledexception.md)|Ayrıntılı|Yönlendirme hizmeti bir özel durumu işledi.|Yönlendirme hizmetleri|  
|[3832 - RoutingServiceTransmitSucceeded](3832-routingservicetransmitsucceeded.md)|Bilgi|Yönlendirme hizmeti KIMLIĞI ' %1 [işlem %2] olan Iletiyi ' %3 ' öğesine başarıyla Iletti.|Yönlendirme hizmetleri|  
|[4001 - TransportListenerSessionsReceived](4001-transportlistenersessionsreceived.md)|Ayrıntılı|Taşıma dinleyicisi oturumu ' %1 ' aracılığıyla alındı|ActivationServices|  
|[4002 - FailFastException](4002-failfastexception.md)|Kritik|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](4003-servicestartpipeerror.md)|Hata|Hizmet başlatma kanal hatası.|ActivationServices|  
|[4008 - DispatchSessionStart](4008-dispatchsessionstart.md)|Ayrıntılı|Oturum gönderme başladı.|ActivationServices|  
|[4008 - DispatchSessionStart](4008-dispatchsessionstart.md)|Uyarı|Bekleyen oturum kuyruğu ' %2 ' bekleyen öğelerle dolu olduğundan, ' %1 ' için oturum gönderme işlemi başarısız oldu.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](4011-messagequeueregisterstart.md)|Ayrıntılı|İleti sırası kaydı başladı.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](4012-messagequeueregisterabort.md)|Hata|İleti kuyruğu kaydı, ' %2 ' Uri 'si için ' %1 ' durumuyla durdu.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](4013-messagequeueunregistersucceeded.md)|Ayrıntılı|' %1 ' Uri 'si için ileti sırası kaydı başarıyla silindi.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](4014-messagequeueregisterfailed.md)|Hata|Uri: ' %1 ' için ileti sırası kaydı ' %2 ' durumuyla başarısız oldu.|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](4015-messagequeueregistercompleted.md)|Bilgi|' %1 ' Uri 'si için ileti sırası kaydı tamamlandı.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](4016-messagequeueduplicatedsocketerror.md)|Hata|İleti sırası yuvayı çoğaltamadı.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](4019-messagequeueduplicatedsocketcomplete.md)|Ayrıntılı|Messagequeuedupereptedsockettamamlanmıştır|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](4020-tcptransportlistenerlisteningstart.md)|Ayrıntılı|' %1 ' Uri 'sinde TCP aktarma dinleyicisi dinlemeye başlıyor.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](4021-tcptransportlistenerlisteningstop.md)|Ayrıntılı|TCP aktarma dinleyicisi dinliyor.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](4022-webhostunregisterprotocolfailed.md)|Hata|Hata kodu: %1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](4023-wasclosealllistenerchannelinstancescompleted.md)|Bilgi|Tüm dinleyici kanalı örneklerinin kapatılması tamamlandı.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](4024-wasclosealllistenerchannelinstancesfailed.md)|Hata|Hata kodu: %1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](4025-openlistenerchannelinstancefailed.md)|Hata|Hata kodu: %1|ActivationServices|  
|[4026 - WasConnected](4026-wasconnected.md)|Ayrıntılı|Bağlandı.|ActivationServices|  
|[4027 - WasDisconnected](4027-wasdisconnected.md)|Ayrıntılı|WAS bağlantısı kesildi.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](4028-pipetransportlistenerlisteningstart.md)|Ayrıntılı|Uri: %1 üzerinde kanal aktarma dinleyicisi dinlemeye başladı.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](4029-pipetransportlistenerlisteningstop.md)|Ayrıntılı|Kanal aktarma dinleyicisi dinleme durdu.|ActivationServices|  
|[4030 - DispatchSessionSuccess](4030-dispatchsessionsuccess.md)|Bilgi|Oturum gönderme başarılı oldu.|ActivationServices|  
|[4031 - DispatchSessionFailed](4031-dispatchsessionfailed.md)|Hata|Oturum gönderilemedi.|ActivationServices|  
|[4032 - WasConnectionTimedout](4032-wasconnectiontimedout.md)|Kritik|WAS bağlantısı zaman aşımına uğradı.|ActivationServices|  
|[4033 - RoutingTableLookupStart](4033-routingtablelookupstart.md)|Ayrıntılı|Yönlendirme tablosu araması başladı.|ActivationServices|  
|[4034 - RoutingTableLookupStop](4034-routingtablelookupstop.md)|Ayrıntılı|Yönlendirme tablosu araması tamamlandı.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](4035-pendingsessionqueueratio.md)|Ayrıntılı|Bekleyen oturum sırası oranı: %1/%2|Kota|  
|[4600 - MessageLogEventSizeExceeded](4600-messagelogeventsizeexceeded.md)|Uyarı|İleti, ETW olay boyutunu aştığından günlüğe kaydedilemedi|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](4801-discoveryclientinclientchannelfailedtoclose.md)|Uyarı|DiscoveryClientChannel içinde oluşturulan DiscoveryClient kapatılamadı ve bu nedenle iptal edildi.|Bulma|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](4802-discoveryclientprotocolexceptionsuppressed.md)|Bilgi|DiscoveryClient kapatılırken ProtocolException gizlendi. Bunun nedeni, bir DiscoveryService 'in DiscoveryClient 'a yanıt gönderilmeye çalışıyor olması olabilir.|Bulma|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](4803-discoveryclientreceivedmulticastsuppression.md)|Bilgi|DiscoveryClient bir DiscoveryProxy 'den çok noktaya yayın gizleme iletisi aldı.|Bulma|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](4804-discoverymessagereceivedafteroperationcompleted.md)|Bilgi|MessageID = ' %2 ' olan bir %1 iletisi, karşılık gelen %3 işlemi tamamlandığından DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4805 - DiscoveryMessageWithInvalidContent](4805-discoverymessagewithinvalidcontent.md)|Uyarı|MessageID = ' %2 ' olan bir %1 iletisi, geçersiz içeriğe sahip olduğundan bırakıldı.|Bulma|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Uyarı|MessageID = ' %2 ' ve relatesTo = ' %3 ' olan bir %1 iletisi, karşılık gelen %4 işlemi tamamlandığı ya da relatesTo değeri geçersiz olduğu için DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](4807-discoverymessagewithinvalidreplyto.md)|Uyarı|MessageID = ' %1 ' olan bir bulma isteği iletisi, geçersiz bir ReplyTo adresine sahip olduğundan bırakıldı.|Bulma|  
|[4808 - DiscoveryMessageWithNoContent](4808-discoverymessagewithnocontent.md)|Uyarı|Bir %1 iletisi, herhangi bir içeriğe sahip olmadığından bırakıldı.|Bulma|  
|[4809 - DiscoveryMessageWithNullMessageId](4809-discoverymessagewithnullmessageid.md)|Uyarı|İleti üst bilgisi gerekli MessageID özelliğini içermediği için bir %1 iletisi bırakıldı.|Bulma|  
|[4810 - DiscoveryMessageWithNullMessageSequence](4810-discoverymessagewithnullmessagesequence.md)|Uyarı|MessageID = ' %2 ' olan bir %1 iletisi, DiscoveryMessageSequence özelliğine sahip olmadığı için DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4811 - DiscoveryMessageWithNullRelatesTo](4811-discoverymessagewithnullrelatesto.md)|Uyarı|MessageID = ' %2 ' olan bir %1 iletisi, ileti üst bilgisi gerekli RelatesTo özelliğini içermediğinden DiscoveryClient tarafından bırakıldı.|Bulma|  
|[4812 - DiscoveryMessageWithNullReplyTo](4812-discoverymessagewithnullreplyto.md)|Uyarı|MessageID = ' %1 ' olan bir bulma isteği iletisi, ReplyTo adresi olmadığından bırakıldı.|Bulma|  
|[4813 - DuplicateDiscoveryMessage](4813-duplicatediscoverymessage.md)|Uyarı|MessageID = ' %2 ' olan bir %1 iletisi, yinelenen bir öğe olduğu için bırakıldı.|Bulma|  
|[4814 - EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Bilgi|EndpointAddress = ' %1 ' ve ListenUri = ' %2 ' olan bitiş noktasının bulunabilirliği devre dışı bırakıldı.|Bulma|  
|[4814 - EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Bilgi|EndpointAddress = ' %1 ' ve ListenUri = ' %2 ' olan bitiş noktasının bulunabilirliği etkinleştirildi.|Bulma|  
|[4816 - FindInitiatedInDiscoveryClientChannel](4816-findinitiatedindiscoveryclientchannel.md)|Ayrıntılı|DiscoveryClientChannel 'da uç noktaları bulmak için bir bulma işlemi başlatıldı.|Bulma|  
|[4817 - InnerChannelCreationFailed](4817-innerchannelcreationfailed.md)|Uyarı|DiscoveryClientChannel, EndpointAddress = ' %1 ' ve = ' %2 ' aracılığıyla bulunan bir uç nokta ile kanalı oluşturamadı. DiscoveryClientChannel şimdi bulunan bir sonraki kullanılabilir uç noktayı kullanmaya çalışacak.|Bulma|  
|[4818 - InnerChannelOpenFailed](4818-innerchannelopenfailed.md)|Uyarı|DiscoveryClientChannel, EndpointAddress = ' %1 ' ve ' %2 ' aracılığıyla bulunan bir uç nokta ile kanalı açamadı. DiscoveryClientChannel şimdi bulunan bir sonraki kullanılabilir uç noktayı kullanmaya çalışacak.|Bulma|  
|[4819 - InnerChannelOpenSucceeded](4819-innerchannelopensucceeded.md)|Bilgi|DiscoveryClientChannel başarıyla bir uç nokta buldu ve kanalı kullanarak açtı. İstemci EndpointAddress = ' %1 ' ve aracılığıyla = ' %2 ' kullanılarak bir hizmete bağlı.|Bulma|  
|[4820 - SynchronizationContextReset](4820-synchronizationcontextreset.md)|Bilgi|SynchronizationContext, DiscoveryClientChannel tarafından özgün %1 değerine sıfırlandı.|Bulma|  
|[4821 - SynchronizationContextSetToNull](4821-synchronizationcontextsettonull.md)|Bilgi|SynchronizationContext, bulma işlemini başlatmadan önce DiscoveryClientChannel tarafından null olarak ayarlandı.|Bulma|  
|[5001 - DCSerializeWithSurrogateStart](5001-dcserializewithsurrogatestart.md)|Ayrıntılı|Yedekleri olan %1 DataContract seri hale getirme başladı.|Serileştirme|  
|[5002 - DCSerializeWithSurrogateStop](5002-dcserializewithsurrogatestop.md)|Ayrıntılı|Yedekleri olan DataContract seri hale getirme durdu.|Serileştirme|  
|[5003 - DCDeserializeWithSurrogateStart](5003-dcdeserializewithsurrogatestart.md)|Ayrıntılı|Yedekleri olan %1 DataContract seri durumdan çıkarma başladı.|Serileştirme|  
|[5004 - DCDeserializeWithSurrogateStop](5004-dcdeserializewithsurrogatestop.md)|Ayrıntılı|Yedekleri olan DataContract seri durumdan çıkarma durdu.|Serileştirme|  
|[5005 - ImportKnownTypesStart](5005-importknowntypesstart.md)|Ayrıntılı|Importknowntypes başladı.|Serileştirme|  
|[5006 - ImportKnownTypesStop](5006-importknowntypesstop.md)|Ayrıntılı|Importknowntypes durdu.|Serileştirme|  
|[5007 - DCResolverResolve](5007-dcresolverresolve.md)|Ayrıntılı|%1 için DataContract çözümleyici çözümleme başladı.|Serileştirme|  
|[5008 - DCGenWriterStart](5008-dcgenwriterstart.md)|Ayrıntılı|%2 için DataContract üretme %1 yazıcısı başladı.|Serileştirme|  
|[5009 - DCGenWriterStop](5009-dcgenwriterstop.md)|Ayrıntılı|DataContract üretme yazıcı durdu.|Serileştirme|  
|[5010 - DCGenReaderStart](5010-dcgenreaderstart.md)|Ayrıntılı|%2 için DataContract üretme %1 okuyucusu başladı.|Serileştirme|  
|[5011 - DCGenReaderStop](5011-dcgenreaderstop.md)|Ayrıntılı|DataContract üretme durdu.|Serileştirme|  
|[5012 - DCJsonGenReaderStart](5012-dcjsongenreaderstart.md)|Ayrıntılı|%2 için JSON üretme %1 okuyucusu başladı.|Serileştirme|  
|[5013 - DCJsonGenReaderStop](5013-dcjsongenreaderstop.md)|Ayrıntılı|JSON okuyucu üretme durdu.|Serileştirme|  
|[5014 - DCJsonGenWriterStart](5014-dcjsongenwriterstart.md)|Ayrıntılı|%2 için JSON üretme %1 yazıcısı başladı.|Serileştirme|  
|[5015 - DCJsonGenWriterStop](5015-dcjsongenwriterstop.md)|Ayrıntılı|JSON üretme yazıcı durdu.|Serileştirme|  
|[5016 - GenXmlSerializableStart](5016-genxmlserializablestart.md)|Ayrıntılı|' %1 ' için seri hale getirilebilir XML üretme başladı.|Serileştirme|  
|[5017 - GenXmlSerializableStop](5017-genxmlserializablestop.md)|Ayrıntılı|Seri hale getirilebilir XML üretme durdu.|Serileştirme|  
|[5203 - JsonMessageDecodingStart](5203-jsonmessagedecodingstart.md)|Ayrıntılı|JsonMessageEncoder iletinin kodunu çözmeye başladı.|Kanal|  
|[5204 - JsonMessageEncodingStart](5204-jsonmessageencodingstart.md)|Ayrıntılı|JsonMessageEncoder iletiyi kodlamaya başladı.|Kanal|  
|[5402 - TokenValidationStarted](5402-tokenvalidationstarted.md)|Ayrıntılı|SecurityToken (' %1 ' türü ve ' %2 ' kimliği) doğrulaması başlatıldı.|Güvenlik|  
|[5403 - TokenValidationSuccess](5403-tokenvalidationsuccess.md)|Ayrıntılı|SecurityToken (' %1 ' türü ve ' %2 ' kimliği) doğrulaması başarılı oldu.|Güvenlik|  
|[5404 - TokenValidationFailure](5404-tokenvalidationfailure.md)|Hata|SecurityToken (' %1 ' türü ve ' %2 ' kimliği) doğrulaması başarısız oldu. %3|Güvenlik|  
|[5405 - GetIssuerNameSuccess](5405-getissuernamesuccess.md)|Ayrıntılı|%1 veren adının %2 belirteç kimliğinden alınması başarılı oldu.|Güvenlik|  
|[5406 - GetIssuerNameFailure](5406-getissuernamefailure.md)|Hata|%1 tokenId 'den veren adının alınması başarısız oldu.|Güvenlik|  
|[5600 - FederationMessageProcessingStarted](5600-federationmessageprocessingstarted.md)|Ayrıntılı|Federasyon iletisi işleme başladı.|Güvenlik|  
|[5601 - FederationMessageProcessingSuccess](5601-federationmessageprocessingsuccess.md)|Ayrıntılı|Federasyon iletisi işleme başarılı oldu.|Güvenlik|  
|[5602 - FederationMessageCreationStarted](5602-federationmessagecreationstarted.md)|Ayrıntılı|Form Gönderi başlatıldıktan sonra Federasyon iletisi oluşturuluyor.|Güvenlik|  
|[5603 - FederationMessageCreationSuccess](5603-federationmessagecreationsuccess.md)|Ayrıntılı|Form gönderme işleminden Federasyon iletisi oluşturma başarılı oldu.|Güvenlik|  
|[5604 - SessionCookieReadingStarted](5604-sessioncookiereadingstarted.md)|Ayrıntılı|Oturum tanımlama bilgisinden oturum belirteci okuma işlemi başlatıldı.|Güvenlik|  
|[5605 - SessionCookieReadingSuccess](5605-sessioncookiereadingsuccess.md)|Ayrıntılı|Oturum tanımlama bilgisinden oturum belirteci okuma başarılı oldu.|Güvenlik|  
|[5606 - PrincipalSettingFromSessionTokenStarted](5606-principalsettingfromsessiontokenstarted.md)|Ayrıntılı|Oturum belirtecinden sorumlu ayarı başlatıldı.|Güvenlik|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](5607-principalsettingfromsessiontokensuccess.md)|Ayrıntılı|Oturum belirtecinden sorumlu ayarı başarılı oldu.|Güvenlik|  
|[57393 - AppDomainUnload](57393-appdomainunload.md)|Bilgi|AppDomain boşaltılıyor. AppDomain. FriendlyName %1, ProcessName %2, ProcessId %3.|Altyapı|  
|[57394 - HandledException](57394-handledexception.md)|Bilgi|Özel durum işleme.|Altyapı|  
|[57395 - ShipAssertExceptionMessage](57395-shipassertexceptionmessage.md)|Hata|Beklenmeyen bir hata oluştu. Uygulamalar bu hatayı işlemeye çalışmamalıdır. Bu Ingilizce ileti, tanılama amacıyla başarısız oldu: %1.|Altyapı|  
|[57396 - ThrowingException](57396-throwingexception.md)|Uyarı|Özel durum oluşturuluyor. %1 kaynağı.|Altyapı|  
|[57397 - UnhandledException](57397-unhandledexception.md)|Kritik|İşlenmeyen özel durum.|Altyapı|  
|[57399 - TraceCodeEventLogCritical](57399-tracecodeeventlogcritical.md)|Kritik|EventLog öğesine yazıldı.|Altyapı|  
|[57400 - TraceCodeEventLogError](57400-tracecodeeventlogerror.md)|Hata|EventLog öğesine yazıldı.|Altyapı|  
|[57401 - TraceCodeEventLogInfo](57401-tracecodeeventloginfo.md)|Bilgi|EventLog öğesine yazıldı.|Altyapı|  
|[57402 - TraceCodeEventLogVerbose](57402-tracecodeeventlogverbose.md)|Ayrıntılı|EventLog öğesine yazıldı.|Altyapı|  
|[57403 - TraceCodeEventLogWarning](57403-tracecodeeventlogwarning.md)|Uyarı|EventLog öğesine yazıldı.|Altyapı|  
|[57404 - HandledExceptionWarning](57404-handledexceptionwarning.md)|Uyarı|Özel durum işleme.|Altyapı|  
|[62326 - HttpHandlerPickedForUrl](62326-httphandlerpickedforurl.md)|Bilgi|' %1 ' URL 'si, ' %2 ' kök öğe türü ile XAML belgesi barındırır. HTTP işleyici türü ' %3 ', bu URL 'ye yapılan tüm istekleri sunacak şekilde çekildi.|Leyemedi|
