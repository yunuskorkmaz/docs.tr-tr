---
title: Çözümleme İzleme Etkinliği Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 0f8b4c15f2afefbc62b98dca66dcf3ccc31b1dc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753042"
---
# <a name="analytic-trace-event-reference"></a>Çözümleme İzleme Etkinliği Başvurusu
Aşağıdaki tabloda, olay düzeyleri, tanımlayıcıların ve WCF analiz izleme ile ilişkili iletilerin tanımlar.  
  
## <a name="event-reference"></a>Etkinliği başvurusu  
  
|Olay Kimliği|Olay düzeyi|Olay iletisi|anahtar sözcükler|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Ayrıntılı|%1 bayt ayırma havuzu.|Altyapı|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Ayrıntılı|Kota %2'ile değiştirerek BufferPool boyutunun %1.|Altyapı|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Ayrıntılı|Çağrılan GÇ iş parçacığı Zamanlayıcısı geri çağırma.|Altyapı|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Ayrıntılı|Çağrılan GÇ iş parçacığı Zamanlayıcısı geri çağırma.|Altyapı|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Bilgiler|Dağıtıcı 'AfterReceiveReply' üzerinde '%1' türünde bir ClientMessageInspector çağrılır.|Sorun giderme, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Bilgiler|Dağıtıcı 'BeforeSendRequest' üzerinde '%1' türünde bir ClientMessageInspector çağrılır.|Sorun giderme, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Bilgiler|Dağıtıcı 'AfterCall' bir ClientParameterInspector çağrılır. türü '%1'.|Sorun giderme, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Bilgiler|Dağıtıcı 'BeforeCall' üzerinde '%1' türünde bir ClientParameterInspector çağrılır.|Sorun giderme, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Bilgiler|'%1' yöntemi bir OperationInvoker çağrılır.|Sorun giderme, ServiceModel EndToEndMonitoring,|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Bilgiler|Dağıtıcı '%3' türünde bir özel durum ile '%1' türünde bir ErrorHandler çağrılır.  ErrorHandled == '%2'.|Sorun giderme, ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Bilgiler|Dağıtıcı '%2' türünde bir özel durum ile '%1' türünde bir FaultProvider çağrılır.|Sorun giderme, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Bilgiler|Dağıtıcı 'AfterReceiveReply' üzerinde '%1' türünde bir MessageInspector çağrılır.|Sorun giderme, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Bilgiler|Dağıtıcı 'BeforeSendRequest' üzerinde '%1' türünde bir MessageInspector çağrılır.|Sorun giderme, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Uyarı|'%2', '%1' azaltma sınırına ulaşıldı.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Bilgiler|Dağıtıcı 'AfterCall' üzerinde '%1' türünde bir ParameterInspector çağrılır.|Sorun giderme, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Bilgiler|Dağıtıcı 'BeforeCall' üzerinde '%1' türünde bir ParameterInspector çağrılır.|Sorun giderme, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost başlatıldı: '%1'.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Bilgiler|'%1' yöntemine çağrı bir OperationInvoker tamamlandı.  Yöntem çağrısı süresi '%2' ms idi.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Bilgiler|Taşıma, '%1' den bir ileti alındı.|Sorun giderme, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Bilgiler|Taşıma, '%1' için bir ileti gönderdi.|Sorun giderme, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Bilgiler|İstemci '%2' sözleşmede tanımlanan '%1' işlemi yürütülüyor. '%3' ileti gönderilir.|Sorun giderme, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Bilgiler|İstemci yürütülürken '%2' sözleşmede tanımlanan '%1' işlemi tamamlandı. '%3' iletisi gönderildi.|Sorun giderme, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Hata|İleti işleme sırasında '%2' türünde yakalanamayan bir özel durum oluştu.  ToString tam özel durum: %1.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Bilgiler|Dağıtıcı taşıma için bir ileti gönderilir. Bağıntı Kimliği '%1' ==.|Sorun giderme, ServiceModel EndToEndMonitoring,|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Bilgiler|Dağıtıcı taşımadan bir ileti alındı. Bağıntı Kimliği '%1' ==.|Sorun giderme, ServiceModel EndToEndMonitoring,|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Uyarı|'%1' yöntemi tarafından OperationInvoker çağrıldığında işlenmeyen bir özel durum oluşturdu. Yöntem çağrısı süresi '%2' ms idi.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Uyarı|'%1' yöntemi tarafından OperationInvoker çağrıldığında bir FaultException oluşturdu. Yöntem çağrısı süresi '%2' ms idi.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Uyarı|'%2', '%1' kısıtlama sınırı % 70 ' dir.|EndToEndMonitoring, sorun giderme, ServiceModel ögesi|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|%1 boşta Hizmetleri toplam %2 dışında kapalı hizmetleri etkinleştirildi.|WebHost ögesi|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Hata|Ad: '%1', başvuru: '%2', yükü: %3.|Sorun giderme, ServiceModel UserEvents, ögesi, EndToEndMonitoring,|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Uyarı|Ad: '%1', başvuru: '%2', yükü: %3.|Sorun giderme, ServiceModel UserEvents, ögesi, EndToEndMonitoring,|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Bilgiler|Ad: '%1', başvuru: '%2', yükü: %3.|Sorun giderme, ServiceModel UserEvents, ögesi, EndToEndMonitoring,|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Bilgiler|Hranice aktivity|Sorun giderme|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Bilgiler|Hranice aktivity|Sorun giderme|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Bilgiler|Hranice aktivity|Sorun giderme|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Bilgiler|Hranice aktivity|Sorun giderme|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Bilgiler|%1|Sorun giderme, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Uyarı|%1|Sorun giderme, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Olay yayınlanan aktarır.|Sorun giderme, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Bilgiler|Derleme başlar.|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Bilgiler|Konec kompilace.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Bilgiler|ServiceHostFactory oluşturma başlar.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Bilgiler|ServiceHostFactory son oluşturma.|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Bilgiler|Begin CreateServiceHost.|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Bilgiler|Konec metody CreateServiceHost.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Bilgiler|HostedTransportConfigurationManager yapılandırma başlatma başlayın.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Bilgiler|HostedTransportConfigurationManager konec inicializace konfigurace.|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Bilgiler|HostedTransportConfigurationManager konec inicializace konfigurace.|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Bilgiler|ServiceHost açık tamamlandı.|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Bilgiler|İstek sanal yolu '%2' ile '%1' uygulama etki aldı.|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Bilgiler|WebHostRequest durdur.|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Ayrıntılı|İşlenen ServiceActivation öğesi göreli adres: '%1', normalleştirilmiş göreli adresi '%2'.||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Ayrıntılı|Gelen istek, '%1' adresi ServiceActivation öğeyle eşleşir.||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Ayrıntılı|Gelen istek adresi %1 olan Asp.Net yol içinde tanımlanan bir WCF Hizmeti ile eşleşir.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Ayrıntılı|ServiceType '%2' ve '%3' serviceHostFactoryType ile yeni bir Asp.Net yol '%1' eklenir.|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Ayrıntılı|IncrementBusyCount çağrılır. Kaynak: %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Ayrıntılı|DecrementBusyCount çağrılır. Kaynak: %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Ayrıntılı|ServiceChannelOpen başlatıldı.|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Bilgiler|ServiceChannelOpen tamamlandı.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Bilgiler|ServiceChannelCall başlatıldı.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Bilgiler|ServiceChannel zaman uyumsuz çağrılar başlatıldı.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Ayrıntılı|HTTP gönderme isteği başlangıcı.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Ayrıntılı|HTTP gönderme isteği durdur.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Ayrıntılı|HTTP aktarımı alınan ileti.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Bilgiler|İleti gönderilirken başlatıldı.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Ayrıntılı|İleti gönderme için kimlik doğrulaması'nı başlatın.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Ayrıntılı|İleti gönderme için yetkilendirme başlatın.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Bilgiler|Tamamlandı iletisi gönderiyor.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Bilgiler|Açık başlatma ServiceChannel.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Bilgiler|ServiceChannel Open Stop.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Bilgiler|Http gönderme akış iletisi başlatıldı.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Hata|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Hata|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Hata|%1 bağlantı havuzu anahtarı: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Bilgiler|%1 bağlantı havuzu anahtarı: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Hata|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Hata|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Hata|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Bilgiler|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Hata|%1|Kota|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Hata|%1|Kota|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Bilgiler|%1|Kota|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Bilgiler|%1|Kota|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Hata|%1|Kota|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Hata|%1|Kota|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Ayrıntılı|Belirteç kimlik doğrulayıcısı durumu önbelleği oranı anlaşma: %1 / %2|Kota|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Ayrıntılı|Güvenlik oturumu oranı: %1 / %2|Kota|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Ayrıntılı|Bekleyen bağlantılar oranı: %1 / %2|Kota|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Ayrıntılı|Eşzamanlı oturum oranı: %1 / %2|Kota|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Ayrıntılı|Eşzamanlı oturum oranı: %1 / %2|Kota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Ayrıntılı|Uç nokta oranı başına giden bağlantı: %1 / %2|Kota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Ayrıntılı|Uç nokta oranı başına giden bağlantı: %1 / %2|Kota|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Ayrıntılı|Bekleyen iletileri her kanal oranı: %1 / %2|Kota|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Ayrıntılı|Eş zamanlı örnekleri oranı: %1 / %2|Kota|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Bilgiler|Bekleyen sıfır sol kabul eder|Kota|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Uyarı|1%|Kota|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Uyarı|Yeniden deneme sayısı '%1' kimlikli MSMQ iletideki ulaşıldı alma|Kota|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Hata|'%1' kimlikli MSMQ iletideki aşıldı en fazla yeniden deneme döngüsü|Kota|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Ayrıntılı|Yeni '%1' oluşturuldu|Kota|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Ayrıntılı|Yeni '%1' oluşturuldu|Kota|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Hata|1%|Kota|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Uyarı|%1 tamamlayamadı.|Kanal|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Uyarı|Gönderilemeyen %1'için başarısız oldu.|Kanal|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Uyarı|Bağlamı alma hatalı.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Bilgiler|%1 %2 özel durumuyla bırakıldı.|Kanal|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Bilgiler|Önbelleğe alınmış kanal fabrikaları sayısı: '%1'.  En fazla '%2' kanal fabrikaları önbelleğe alınabilir.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Bilgiler|Önbellek '%1' sınırına ulaştığı için bir kanal üreteci önbellek dışına eski.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Bilgiler|Önbelleğinde bulunan eşleşen kanal fabrikası kullanılır.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Bilgiler|Kanal fabrikası önbellekten kullanarak değil, yani önbelleği örneği için devre dışı.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Bilgiler|Sorgu oluşturma kullanarak '%1', istek Uri'sinde yürütüldü: '%2'.|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Hata|'%1' işlemi hatalarla gönderildi.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Bilgiler|'%1' işlemi başarıyla gönderildi.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Bilgiler|'%1' bayttan içeren bir ileti Kodlayıcı tarafından okundu.|Kanal|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Bilgiler|'%1' bayttan içeren bir ileti Kodlayıcı tarafından yazılmıştır.|Kanal|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Hata|URI boş kanal durduruluyor oturum: '%1'.|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Ayrıntılı|Bağlantı kabul etmesi başlatıldı.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Ayrıntılı|Kabul edilen ListenerId:% 1 SocketId:% 2.|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Ayrıntılı|%1 için havuzu herhangi bir bağlantı ve %2 meşgul bağlantıları vardır.|Kanal|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Ayrıntılı|Dağıtıcı çalışmaya seri durumundan çıkarma istek iletisi.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Ayrıntılı|Tamamlanan dağıtıcı seri durumundan çıkarma istek iletisi.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Ayrıntılı|Yanıt iletisinin serileştirme göndericisi başlatıldı.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Ayrıntılı|Dağıtıcı yanıt iletisi serileştirilmesi tamamlandı.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Ayrıntılı|İstemci isteği serileştirme başlatıldı.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Ayrıntılı|İstemci istek iletisinin serileştirme tamamlandı.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Ayrıntılı|Yanıt iletisi seri durumdan çıkarılırken bir istemci başlatıldı.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Ayrıntılı|İstemci, yanıt iletisi seri durumdan çıkarılırken tamamlandı.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Ayrıntılı|Güvenlik görüşmeleri başlatıldı.|Güvenlik|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Ayrıntılı|Güvenlik görüşmeleri tamamlandı.|Güvenlik|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Ayrıntılı|SecurityTokenProvider açılış tamamlandı.|Güvenlik|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Ayrıntılı|Giden ileti güvenli.|Güvenlik|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Ayrıntılı|Gelen ileti doğrulandı.|Güvenlik ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Ayrıntılı|Hizmet örneği alma başlatıldı.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Ayrıntılı|Hizmet örneği alınır.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Ayrıntılı|1 - ileti ChannelHandlerId:% çalışmaya döngü alırsınız.|Kanal|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Ayrıntılı|1 - ileti ChannelHandlerId:% durduruldu döngü alırsınız.|Kanal|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Ayrıntılı|ChannelFactory oluşturulur.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Ayrıntılı|Kanal bağlantısı kabul ' %1 başlatıldı.|Kanal|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Ayrıntılı|Kanal bağlantısı kabul edildi.|Kanal|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Ayrıntılı|Bağlantının kurulması için %1 başlatıldı.|Kanal|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Ayrıntılı|Bağlantı kuruldu.|Kanal|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Ayrıntılı|'%1' için oturum giriş anladım.|Kanal|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Hata|Hata '%1' gönderme bağlantı okuyucu.|Kanal|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Ayrıntılı|Yuva kabul kapalı.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Kritik|Hizmet ana bilgisayarı hatalı.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Ayrıntılı|'%1' için açma dinleyicisi.|Kanal|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Ayrıntılı|Dinleyici açık tamamlandı.|Kanal|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Ayrıntılı|Sunucu en fazla havuza alınmış bağlantı kotasına ulaşıldı.|Kota|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Hata|Uzak Adres %2 için 1 SocketId:% zaman aşımına uğradı.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Uyarı|Uzak Adres %2 için 1 SocketId:% sıfırlama hatası bir bağlantı vardı.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Ayrıntılı|Hizmet güvenliği anlaşması tamamlandı.|Güvenlik|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Hata|Güvenlik anlaşması işleme başarısız oldu.|Güvenlik|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Ayrıntılı|Güvenlik doğrulaması başarılı oldu.|Güvenlik|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Hata|Güvenlik doğrulaması başarısız oldu.|Güvenlik|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Ayrıntılı|%1 için yinelenen yuva.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Ayrıntılı|Güvenlik kimliğe bürünme başarılı oldu.|Güvenlik|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Uyarı|Güvenlik kimliğe bürünme başarısız oldu.|Güvenlik|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Uyarı|HTTP kanalı istek sona erdirildi.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Uyarı|HTTP kanalı yanıt durduruldu.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Uyarı|HTTP kimlik doğrulaması başarısız oldu.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Ayrıntılı|'%1' URI'sini SharedListenerProxy kayıt başladı.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Ayrıntılı|SharedListenerProxy kayıt durdur.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Hata|SharedListenerProxy kaydı, '%1' durumu ile başarısız oldu.|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Hata|ConnectionPoolPreambleFailed.|Kanal|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Ayrıntılı|SslOnAcceptUpgradeStart|Güvenlik|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Ayrıntılı|SslOnAcceptUpgradeStop|Güvenlik|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Ayrıntılı|İleti kodlama BinaryMessageEncoder başlatıldı.|Kanal|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Ayrıntılı|İleti kodlama MtomMessageEncoder başlatıldı.|Kanal|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Ayrıntılı|İleti kodlama TextMessageEncoder başlatıldı.|Kanal|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Ayrıntılı|Bir iletinin şifrelemesini kaldırmada BinaryMessageEncoder başlatıldı.|Kanal|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Ayrıntılı|Bir iletinin şifrelemesini kaldırmada MtomMessageEncoder başlatıldı.|Kanal|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Ayrıntılı|Bir iletinin şifrelemesini kaldırmada TextMessageEncoder başlatıldı.|Kanal|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Bilgiler|Bir mesaj HTTP aktarımı başladı.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Ayrıntılı|'%3' okunan SocketId:% 1 okunur '%2' bayt.|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Ayrıntılı|'%3' okunan SocketId:% 1 okunur '%2' bayt.|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Ayrıntılı|'% 3', '%2' yazma bayt SocketId:% 1.|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Ayrıntılı|'% 3', '%2' yazma bayt SocketId:% 1.|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Ayrıntılı|Gönderilen SessionId:% 1 alındı.|Kanal|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Bilgiler|1 SessionId:% bağlanılıyor.|Kanal|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Bilgiler|1 SessionId:% hatalı.|Kanal|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Ayrıntılı|Güvenlik yükseltmesi başlatma WindowsStreamSecurity.|Güvenlik|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Ayrıntılı|Windows yükseltme kabul üzerinde güvenlik akış.|Güvenlik|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Uyarı|1 SocketId:% iptal ediliyor.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Ayrıntılı|HttpGetContext başlangıcı.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Ayrıntılı|İstemci gönderme giriş Başlat.|Kanal|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Ayrıntılı|İstemci gönderme giriş durdur.|Kanal|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Uyarı|HTTP iletisi alma başarısız.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Bilgiler|TransactionScope ile LocalIdentifier oluşturuluyor: '%1' ve DistributedIdentifier: '%2'.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Bilgiler|Bir akış ileti Kodlayıcı tarafından okundu.|Kanal|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Bilgiler|Bir akış ileti Kodlayıcı tarafından yazıldı.|Kanal|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Bilgiler|İleti Kodlayıcı tarafından zaman uyumsuz olarak yazılmıştır.|Kanal|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Bilgiler|Temel alınan akışa tamamlandı BufferId:% 1 yazma '%2' bayt.|Kanal|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Bilgiler|İleti Kodlayıcı tarafından zaman uyumsuz olarak yazılmıştır.|Kanal|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Ayrıntılı|Paylaşılan bellek '%1' öğesinde oluşturulan kanal.|Kanal|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Ayrıntılı|NamedPipe '%1' oluşturuldu.|Kanal|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Ayrıntılı|İmza doğrulama başlatıldı.|Güvenlik|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Ayrıntılı|İmza doğrulama başarılı oldu.|Güvenlik|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Ayrıntılı|Anahtar şifre çözme çalışmaya DC'de sona erdi.|Güvenlik|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Ayrıntılı|Sarmalanan anahtar şifre çözme başarılı oldu.|Güvenlik|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Ayrıntılı|Veri işleme çalışmaya şifrelenir.|Güvenlik|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Ayrıntılı|Şifrelenmiş veri işleme başarılı oldu.|Güvenlik|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Ayrıntılı|HTTP ileti işleyicisi, gelen isteğin işlenmesine başlandı.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Ayrıntılı|HTTP ileti işleyicisi, gelen isteği zaman uyumsuz işlenmesine başlandı.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Ayrıntılı|HTTP ileti işleyicisi, bir gelen talep işleme tamamlandı.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Uyarı|HTTP ileti işleyicisi hatalı.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Hata|WebSocket bağlantısı zaman aşımına uğradı.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Ayrıntılı|HTTP ileti işleyicisi, yanıt işlenmesine başlandı.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Ayrıntılı|HTTP ileti işleyicisi, yanıtı zaman uyumsuz işlenmesine başlandı.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Ayrıntılı|HTTP ileti işleyicisi yanıt işleme tamamlandı.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Ayrıntılı|'%1' WebSocket bağlantısı istek başlangıç gönderin.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Ayrıntılı|WebSocketId:% 1 bağlantı isteği gönderildi.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Ayrıntılı|WebSocket bağlantısı başlangıç kabul edin.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Ayrıntılı|WebSocketId:% 1 bağlantı kabul edildi.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Hata|'%1' durum koduyla WebSocket bağlantısı reddedildi|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Hata|WebSocket bağlantısı isteği başarısız oldu: '%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Hata|1 WebSocketId:% bağlantısı iptal edildi.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Ayrıntılı|'% 3', '%2' yazma bayt WebSocketId:% 1.|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Ayrıntılı|1 WebSocketId:% zaman uyumsuz yazma durdur.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Ayrıntılı|Okuma WebSocketId:% 1 başlangıcı.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Ayrıntılı|'% 3', '%2' bayt okuma WebSocketId:% 1.|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Ayrıntılı|Gönderme WebSocketId:% 1 ileti Kapat durumu '%3' ile '% 2' kapatın.|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Ayrıntılı|WebSocketId:% 1 göndermeden Kapat durumu '%3' ile '% 2' çıkış iletisi kapatın.|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Ayrıntılı|WebSocketId:% 1 bağlantı kapatıldı.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Ayrıntılı|'%2' durumundaki WebSocketId:% 1 bağlantı kapatma iletisi alındı.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Ayrıntılı|İstemci '%1' türünde WebSocket fabrikadan WebSocketVersion kullanma.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Ayrıntılı|WebSocket istemcisi ile '%1' türünde bir Fabrika oluşturuluyor.|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Bilgiler|XamlServicesLoad start|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Bilgiler|XamlServicesLoad Stop|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Bilgiler|CreateWorkflowServiceHost Başlat|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Bilgiler|CreateWorkflowServiceHost Durdur|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Bilgiler|Hizmeti etkinleştirme Başlat|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Bilgiler|Hizmeti etkinleştirme Durdur|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Ayrıntılı|Kullanılabilir bellek (bayt): %1|Kota|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Bilgiler|Yönlendirme hizmeti, '%1' istemci kapatılıyor.|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Uyarı|Yönlendirme Hizmeti İstemcisi '%1' hatalı.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Bilgiler|Yönlendirme hizmeti yollarından ileti tamamlıyor.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Hata|Yönlendirme Hizmeti uç nokta adresi '%1' olan bir ileti işlenirken başarısız oldu.|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Bilgiler|Yönlendirme Hizmeti uç noktası için bir istemci oluşturuyor: '%1'.|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Ayrıntılı|Yönlendirme hizmeti ile RouteOnHeadersOnly yapılandırılmıştır: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Bilgiler|Yönlendirme hizmeti isteği yanıt iletisi tamamlıyor.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Ayrıntılı|Yönlendirme hizmeti yönlendirilmiş iletinin kimliği: '%1' %2 uç nokta listeler.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Bilgiler|Yönlendirme hizmeti için yeni bir RoutingConfiguration uygulanmıştır.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Bilgiler|Yönlendirme hizmeti kimliği ile bir iletisi işliyor: '%1', eylem: '%2', gelen URL: '%3' işlemde alınan: %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Bilgiler|İleti kimliği ile yönlendirme hizmeti iletmesini durdurabilirsiniz: '%1' [işlemi %2] '% 3'.|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Bilgiler|Yönlendirme hizmeti, kimliğine sahip bir işlem işleniyor: '%1'.|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Hata|Yönlendirme hizmeti bileşeninin %1 bir çift yönlü bir geri çağırma özel durumla karşılaştı.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Bilgiler|Yönlendirme hizmeti iletinin kimliği: '%1' [%2 işlemi] yedekleme '%3' uç noktasına taşınır.|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Bilgiler|Yönlendirme hizmeti, iletileri işlemek için yeni bir işlem kimliğine sahip '%1' oluşturuldu.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Uyarı|Yönlendirme hizmeti, '%1' Giden istemci kapatılırken başarısız oldu.|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Bilgiler|Yönlendirme hizmeti, '%1' eylemi ile bir yanıt iletisi geri gönderme.|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Uyarı|Yönlendirme hizmeti, '%1' eylemi ile bir hata yanıt iletisi geri gönderme.|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Ayrıntılı|Yönlendirme hizmeti ReceiveContext.Complete Kimliğe sahip ileti için çağırma: '%1'.|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Uyarı|Yönlendirme hizmeti ReceiveContext.Abandon Kimliğe sahip ileti için çağırma: '%1'.|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Ayrıntılı|Yönlendirme hizmeti, '%1' kullanarak mevcut işlem iletileri gönderir.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Uyarı|Yönlendirme hizmeti, '%1' gönderilirken başarısız oldu.|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Bilgiler|Yönlendirme hizmeti MessageFilterTable eşleşme başlangıcı.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Bilgiler|Yönlendirme hizmeti MessageFilterTable eşleşme durdur.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Ayrıntılı|Yönlendirme Hizmeti durdurma çağıran kanalda: '%1'.|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Ayrıntılı|Yönlendirme hizmeti, bir özel durum işlense.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Bilgiler|Yönlendirme hizmeti başarıyla ileti kimliği ile aktarılan: ' %1 [işlemi %2] '% 3'.|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Ayrıntılı|'%1' alınan aktarım dinleyicisi oturumu|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Kritik|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Hata|Hizmeti Başlat kanal hatası|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Ayrıntılı|Oturum gönderme başlatıldı.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Uyarı|Oturumu Kuyruk öğeleri bekleyen '%2' ile tam olduğundan '%1' için oturum gönderme başarısız oldu.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Ayrıntılı|İleti kuyruğu başlangıç kaydedin.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Hata|İleti kuyruğu kayıt durumu ile iptal edildi: '%1' URI: '%2'.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Ayrıntılı|İleti kuyruğu kaydı başarılı URI: '%1'.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Hata|İleti kuyruğu kayıt URI: '%1' durumuyla başarısız oldu: '%2'.|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Bilgiler|İleti kuyruğu kaydı için '%1' URI tamamlandı.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Hata|İleti kuyruğu çoğaltma yuva başarısız oldu.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Ayrıntılı|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Ayrıntılı|Tcp aktarımı dinleyicisi URI üzerinde dinleme işlemi başlatılıyor: '%1'.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Ayrıntılı|Tcp aktarımı dinleyicisinin dinleme.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Hata|Hata kodu: % 1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Bilgiler|Tüm dinleyici kanal örnekleri tamamlandı kapatma.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Hata|Hata kodu: % 1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Hata|Hata kodu: % 1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Ayrıntılı|Bağlandı.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Ayrıntılı|Bağlantısı kesildi.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Ayrıntılı|Kanal taşıma dinleyicisi dinleme Uri 1 Başlat.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Ayrıntılı|Kanal taşıma dinleyicisinin dinleme durdur.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Bilgiler|Oturum gönderme başarılı oldu.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Hata|Oturum gönderme başarısız oldu.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Kritik|Bağlantı zaman aşımına uğradı.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Ayrıntılı|Yönlendirme tablosu aramasında başlatıldı.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Ayrıntılı|Yönlendirme tablosunda arama tamamlandı.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Ayrıntılı|Bekleyen oturum kuyruğu oranı: %1 / %2|Kota|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Uyarı|ETW olay boyutu aştığı ileti günlüğe yazılamadı|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Uyarı|DiscoveryClientChannel içinde oluşturulan DiscoveryClient kapatın ve bu nedenle iptal edildi başarısız oldu.|Bulma|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Bilgiler|DiscoveryClient kapatılırken bir ProtocolException engellendi. DiscoveryClient yanıta gönderilecek bir DiscoveryService hala çalışıyor olmasından kaynaklanabilir.|Bulma|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Bilgiler|DiscoveryClient bir DiscoveryProxy çok noktaya yayın gizleme ileti aldınız.|Bulma|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Bilgiler|MessageID ile bir %1 ileti = karşılık gelen %3 işlemi tamamlandıktan sonra olduğundan, '%2' tarafından DiscoveryClient bırakıldı.|Bulma|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Uyarı|MessageID ile bir %1 ileti = '%2', geçersiz içeriğe sahip olmadığından bırakıldı.|Bulma|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Uyarı|MessageID ile bir %1 ileti = '%2' ve relatesTo = karşılık gelen %4 işlem tamamlandı veya relatesTo değeri geçersiz olduğundan '%3' tarafından DiscoveryClient bırakıldı.|Bulma|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Uyarı|Bir bulma isteği iletisiyle MessageID = ReplyTo adresi geçersiz olduğundan '%1' bırakıldı.|Bulma|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Uyarı|Herhangi bir içerik yoktu bir %1 ileti bırakıldı.|Bulma|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Uyarı|Bir %1 ileti, ileti üst bilgisi gerekli MessageID özelliği içermediğinden atıldı.|Bulma|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Uyarı|MessageID ile bir %1 ileti = DiscoveryMessageSequence özelliğine sahip olmadığından, '%2' tarafından DiscoveryClient bırakıldı.|Bulma|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Uyarı|MessageID ile bir %1 ileti = gerekli RelatesTo özelliği ileti üst bilgisi içermediğinden '%2' tarafından DiscoveryClient bırakıldı.|Bulma|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Uyarı|Bir bulma isteği iletisiyle MessageID = '%1' ReplyTo adres sahip olmadığından bırakıldı.|Bulma|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Uyarı|MessageID ile bir %1 ileti = '%2', yinelenen olduğu için bırakıldı.|Bulma|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Bilgiler|EndpointAddress bitiş noktası bulunabilirliğini = '%1' ve ListenUri = '%2' devre dışı bırakıldı.|Bulma|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Bilgiler|EndpointAddress bitiş noktası bulunabilirliğini = '%1' ve ListenUri = '%2' etkin.|Bulma|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Ayrıntılı|Uç nokta bulmak için DiscoveryClientChannel bulma işlemi başlatıldı.|Bulma|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Uyarı|DiscoveryClientChannel EndpointAddress ile keşfedilen bir uç noktası ile kanal oluşturma başarısız oldu. '%1' = ve aracılığıyla = '%2'. DiscoveryClientChannel artık sonraki kullanılabilir bulunan uç noktası kullanmayı dener.|Bulma|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Uyarı|EndpointAddress ile keşfedilen bir uç noktasıyla kanalını açmayı DiscoveryClientChannel başarısız = '%1' ve '%2' aracılığıyla =. DiscoveryClientChannel artık sonraki kullanılabilir bulunan uç noktası kullanmayı dener.|Bulma|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Bilgiler|DiscoveryClientChannel başarıyla bir uç nokta bulundu ve kullanmaya kanalı açıldı. İstemci EndpointAddress kullanarak bir hizmete bağlı = '%1' ve '%2' aracılığıyla =.|Bulma|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Bilgiler|SynchronizationContext özgün değerine %1 DiscoveryClientChannel tarafından sıfırlandı.|Bulma|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Bilgiler|SynchronizationContext kümesi bulma işlemi başlatmadan önce DiscoveryClientChannel tarafından null.|Bulma|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Ayrıntılı|DataContract temsilciler başlangıç %1 serileştirir.|Serileştirme|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Ayrıntılı|DataContract ile temsilciler durdurma serileştirir.|Serileştirme|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Ayrıntılı|DataContract temsilciler başlangıç %1 seri durumdan çıkarır.|Serileştirme|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Ayrıntılı|DataContract ile temsilciler durdurma seri durumdan çıkarır.|Serileştirme|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Ayrıntılı|ImportKnownTypes başlatın.|Serileştirme|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Ayrıntılı|ImportKnownTypes durdurun.|Serileştirme|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Ayrıntılı|DataContract çözümleyici %1 başlangıç çözümleme.|Serileştirme|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Ayrıntılı|DataContract başlangıç %2 için %1 yazıcı oluşturur.|Serileştirme|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Ayrıntılı|DataContract yazan durdurma oluşturur.|Serileştirme|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Ayrıntılı|DataContract başlangıç %2 için %1 okuyucu oluşturur.|Serileştirme|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Ayrıntılı|DataContract üretimi durdur.|Serileştirme|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Ayrıntılı|JSON başlangıç %2 için %1 okuyucu oluşturur.|Serileştirme|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Ayrıntılı|JSON okuyucu üretimi durdur.|Serileştirme|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Ayrıntılı|JSON başlangıç %2 için %1 yazıcı oluşturur.|Serileştirme|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Ayrıntılı|JSON yazan durdurma oluşturur.|Serileştirme|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Ayrıntılı|'%1' Başlangıç için serileştirilebilir XML oluşturur.|Serileştirme|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Ayrıntılı|XML seri hale getirilebilir durdurma oluşturur.|Serileştirme|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Ayrıntılı|Bir iletinin şifrelemesini kaldırmada JsonMessageEncoder başlatıldı.|Kanal|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Ayrıntılı|İleti kodlama JsonMessageEncoder başlatıldı.|Kanal|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Ayrıntılı|SecurityToken (türü '%1' ve Kimliği '%2') doğrulama başlatıldı.|Güvenlik|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Ayrıntılı|SecurityToken (türü '%1' ve Kimliği '%2') doğrulama başarılı oldu.|Güvenlik|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Hata|SecurityToken (türü '%1' ve Kimliği '%2') doğrulama başarısız oldu. %3|Güvenlik|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Ayrıntılı|Veren adı: % 1 tokenId:% 2'den alma başarılı.|Güvenlik|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Hata|Verenin adını tokenId:% 1 alınması başarısız oldu.|Güvenlik|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Ayrıntılı|Federasyon ileti işleme başladı.|Güvenlik|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Ayrıntılı|Federasyon ileti işleme başarılı oldu.|Güvenlik|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Ayrıntılı|Federasyon iletisi sunulan form gönderisi oluşturma başladı.|Güvenlik|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Ayrıntılı|Form post Federasyon iletisi oluşturma başarılı oldu.|Güvenlik|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Ayrıntılı|Oturum belirteci oturum tanımlama bilgisinden okuma başlatıldı.|Güvenlik|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Ayrıntılı|Okuma Thread.CurrentPrincipal z tokenu relace oturum tanımlama bilgisinin başarılı oldu.|Güvenlik|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Ayrıntılı|Oturum belirteci asıl ayarından başlatıldı.|Güvenlik|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Ayrıntılı|Oturum belirteci asıl ayarından başarılı oldu.|Güvenlik|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Bilgiler|AppDomain kaldırılıyor. %1, işlemadı: %2, işlem kimliği %3. AppDomain.FriendlyName.|Altyapı|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Bilgiler|Bir özel durum işleme.|Altyapı|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Hata|Beklenmeyen bir hata oluştu. Bu hatayı işlemek uygulamaları çalışmamalıdır. Tanılama amacıyla bu İngilizce ileti hatayla ilişkilendirildi: %1.|Altyapı|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Uyarı|Bir özel durum. %1. kaynak.|Altyapı|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Kritik|İşlenmeyen özel durum.|Altyapı|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Kritik|EventLog öğesine yazıldı.|Altyapı|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Hata|EventLog öğesine yazıldı.|Altyapı|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Bilgiler|EventLog öğesine yazıldı.|Altyapı|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Ayrıntılı|EventLog öğesine yazıldı.|Altyapı|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Uyarı|EventLog öğesine yazıldı.|Altyapı|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Uyarı|Bir özel durum işleme.|Altyapı|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Bilgiler|'%1' URL'si konakları XAML belgenin kök öğe '%2' yazın. HTTP işleyicisi türü '%3', bu URL'ye yapılan tüm isteklere hizmet vermek için çekilir.|WebHost|
