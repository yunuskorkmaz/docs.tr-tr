---
title: İzleme olayları başvurusu
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: 5b3bba83b3c6c7ab27c9470213b7675f7e107c7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712220"
---
# <a name="tracking-events-reference"></a>İzleme olayları başvurusu
Bir iş akışı yürütme sırasında [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] yaşam sürelerinin başlarında çeşitli aşamaları boyunca hareket ettikçe olayları izleme başlatır. Konak, bu olaylara abone olma ve iş akışının ilerleme durumu yaşam süresi boyunca güncel tutun. Oluşturulan izleme olayları, bu bölümde ele alınmıştır.  
  
## <a name="event-reference"></a>Etkinliği başvurusu  
  
|Olay Kimliği|Olay düzeyi|Olay iletisi|Anahtar Sözcükler|  
|--------------|-----------------|-------------------|--------------|  
|[100 - WorkflowInstanceRecord](100-workflowinstancerecord.md)|Bilgiler|TrackRecord WorkflowInstanceRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, ek açıklamalar = %6, ProfileName %7 =|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[101 - WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Hata|TrackRecord WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklamalar = % 10, ProfileName = % 11|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[102 - WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|Uyarı|TrackRecord WorkflowInstanceAbortedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName %7 =|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[103 - ActivityStateRecord](103-activitystaterecord.md)|Bilgiler|TrackRecord ActivityStateRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, durum = %4, ad = %5, etkinlik kimliği = %6, ActivityInstanceId = %7, ActivityTypeName = %8, bağımsız değişkenleri = %9, değişkenleri = % 10, ek açıklamalar = % 11, ProfileName = % 12|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[104 - ActivityScheduledRecord](104-activityscheduledrecord.md)|Bilgiler|TrackRecord ActivityScheduledRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, ad = %4, etkinlik kimliği = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName % 11, ek açıklamalar = 12, % ProfileName = % 13 =|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[105 - FaultPropagationRecord](105-faultpropagationrecord.md)|Uyarı|TrackRecord FaultPropagationRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8 FaultHandlerActivityId %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, hata = % 12, IsFaultSource = % 13, ek açıklamalar = % 14, ProfileName = = % 15|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[106 - CancelRequestRecord](106-cancelrequestrecord.md)|Bilgiler|TrackRecord CancelRequestedRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, ad = %4, etkinlik kimliği = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName % 11, ek açıklamalar = 12, % ProfileName = % 13 =|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[107 -- BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|Bilgiler|TrackRecord BookmarkResumptionRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ad = %4, SubInstanceID = %5, OwnerActivityName = %6, OwnerActivityId = %7, OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9, ek açıklamalar = % 10, ProfileName = % 11|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[108 - CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|Bilgiler|TrackRecord CustomTrackingRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityName = %5, etkinlik kimliği = %6, ActivityInstanceId = %7, ActivityTypeName = %8, veri = %9, ek açıklamalar = % 10, ProfileName = % 11|Sorun giderme, ögesi, WFTracking UserEvents, EndToEndMonitoring,|  
|[110 - CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|Uyarı|TrackRecord CustomTrackingRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityName = %5, etkinlik kimliği = %6, ActivityInstanceId = %7, ActivityTypeName = %8, veri = %9, ek açıklamalar = % 10, ProfileName = % 11|Sorun giderme, ögesi, WFTracking UserEvents, EndToEndMonitoring,|  
|[111 - CustomTrackingRecordError](111-customtrackingrecorderror.md)|Hata|TrackRecord CustomTrackingRecord, InstanceId = = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityName = %5, etkinlik kimliği = %6, ActivityInstanceId = %7, ActivityTypeName = %8, veri = %9, ek açıklamalar = % 10, ProfileName = % 11|Sorun giderme, ögesi, WFTracking UserEvents, EndToEndMonitoring,|  
|[112 - WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|Bilgiler|TrackRecord WorkflowInstanceSuspendedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName %7 =|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[113 - WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Hata|TrackRecord WorkflowInstanceTerminatedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName %7 =|Sorun giderme, ögesi, WFTracking EndToEndMonitoring,|  
|[114 - WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|Bilgiler|TrackRecord WorkflowInstanceRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, ek açıklamalar = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|Ögesi, WFTracking|  
|[115 - WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|Uyarı|TrackRecord WorkflowInstanceAbortedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|Ögesi, WFTracking|  
|[116 - WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|Bilgiler|TrackRecord WorkflowInstanceSuspendedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|Ögesi, WFTracking|  
|[117 - WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Hata|TrackRecord WorkflowInstanceTerminatedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, neden = %5, ek açıklamalar = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|Ögesi, WFTracking|  
|[118 - WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Hata|TrackRecord WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklamalar = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12|Ögesi, WFTrackingHealthMonitoring, WFTracking|  
|[119 - WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|Bilgiler|TrackRecord WorkflowInstanceUpdatedRecord, örnek kimliği = %1, RecordNumber = = %2, EventTime = %3, ActivityDefinitionId = %4, durum = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, ek açıklamalar = %8, ProfileName = %9|Ögesi, WFTracking|  
|[225 - TraceCorrelationKeys](225-tracecorrelationkeys.md)|Bilgiler|Bağıntı anahtar '%1' değerleri '%2' üst kapsamda '%3' kullanılarak hesaplanır.|WFServices sorunlarını giderme|  
|[440 - StartSignpostEvent1](440-startsignpostevent.md)|Bilgiler|Hranice aktivity|WFServices sorunlarını giderme|  
|[441- StopSignpostEvent1](441-stopsignpostevent.md)|Bilgiler|Hranice aktivity|WFServices sorunlarını giderme|  
|[1001 - WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|Bilgiler|WorkflowInstance ID: '%1' kapalı durumda tamamlandı.|WFRuntime|  
|[1002 - WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|Bilgiler|WorkflowApplication ID: '%1' sonlandırıldı. Faulted durumunda bir özel durum ile tamamlandı.|WFRuntime|  
|[1003 - WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|Bilgiler|WorkflowInstance ID: '%1' iptal edildi durumunda tamamlandı.|WFRuntime|  
|[1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|Bilgiler|WorkflowInstance ID: '%1', bir özel durum ile iptal edildi.|WFRuntime|  
|[1005 - WorkflowApplicationIdled](1005-workflowapplicationidled.md)|Bilgiler|WorkflowApplication ID: '%1' boşta geçti.|WFRuntime|  
|[1006 - WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Hata|WorkflowInstance ID: '%1' işlenmeyen bir özel durumla karşılaştı.  Özel durum '%2', DisplayName etkinliğinden kaynaklanan: '%3'.  Aşağıdaki işlem yapılmayacak: %4.|WFRuntime|  
|[1007 - WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|Bilgiler|WorkflowApplication ID: '%1' Trvalý.|WFRuntime|  
|[1008 - WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|Bilgiler|WorkflowInstance ID: '%1'. yüklenmemiş.|WFRuntime|  
|[1009 - ActivityScheduled](1009-activityscheduled.md)|Bilgiler|Üst etkinlik '%1', DisplayName: '%2', InstanceId: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1010 - ActivityCompleted](1010-activitycompleted.md)|Bilgiler|Üst etkinlik '%1', DisplayName: '%2', InstanceId: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1011 - ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem zamanlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1012 - StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.|WFRuntime|  
|[1013 - CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem tamamlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1014 - ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|Ayrıntılı|Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', InstanceId: '%3'.  '%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.|WFRuntime|  
|[1015 - StartCompletionWorkItem](1015-startcompletionworkitem.md)|Ayrıntılı|Üst etkinlik '%1', DisplayName için bir CompletionWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'. '%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.|WFRuntime|  
|[1016 - CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|Ayrıntılı|Bir CompletionWorkItem üst etkinliği '%1', DisplayName tamamlandı: '%2', InstanceId: '%3'. '%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.|WFRuntime|  
|[1017 - ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir CancelActivityWorkItem zamanlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1018 - StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir CancelActivityWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.|WFRuntime|  
|[1019 - CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir CancelActivityWorkItem tamamlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1020 - CreateBookmark](1020-createbookmark.md)|Ayrıntılı|'%1', DisplayName etkinliği için yer imi oluşturuldu: '%2', InstanceId: '%3'.  YerİşaretiAdı: %4, BookmarkScope: %5.|WFRuntime|  
|[1021 - ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir BookmarkWorkItem zamanlandı: '%2', InstanceId: '%3'.  YerİşaretiAdı: %4, BookmarkScope: %5.|WFRuntime|  
|[1022 - StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir BookmarkWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.  YerİşaretiAdı: %4, BookmarkScope: %5.|WFRuntime|  
|[1023 - CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir BookmarkWorkItem tamamlandı: '%2', InstanceId: '%3'. YerİşaretiAdı: %4, BookmarkScope: %5.|WFRuntime|  
|[1024 - CreateBookmarkScope](1024-createbookmarkscope.md)|Ayrıntılı|Bir BookmarkScope oluşturuldu: %1.|WFRuntime|  
|[1025 - BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|Ayrıntılı|TemporaryId vardı BookmarkScope: '%1' kimlikli başlatıldı: '%2'.|WFRuntime|  
|[1026 - ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir TransactionContextWorkItem zamanlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1027 - StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir TransactionContextWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.|WFRuntime|  
|[1028 - CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir TransactionContextWorkItem tamamlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1029 - ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir FaultWorkItem zamanlandı: '%2', InstanceId: '%3'.  Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.|WFRuntime|  
|[1030 - StartFaultWorkItem](1030-startfaultworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir FaultWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.  Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.|WFRuntime|  
|[1031 - CompleteFaultWorkItem](1031-completefaultworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', InstanceId: '%3'. Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.|WFRuntime|  
|[1032 - ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|Ayrıntılı|Bir çalışma zamanı iş öğesi '%1', DisplayName etkinliği için zamanlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1033 - StartRuntimeWorkItem](1033-startruntimeworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesinin yürütme başlatılıyor: '%2', InstanceId: '%3'.|WFRuntime|  
|[1034 - CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|Ayrıntılı|'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesi tamamlandı: '%2', InstanceId: '%3'.|WFRuntime|  
|[1035 - RuntimeTransactionSet](1035-runtimetransactionset.md)|Ayrıntılı|Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlanmış: '%2', InstanceId: '%3'.  '%4', DisplayName etkinlik için yalıtılmış yürütme: '%5', InstanceId: '%6'.|WFRuntime|  
|[1036 - RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|Ayrıntılı|Etkinliği '%1', DisplayName: '%2', InstanceId: '%3', çalışma zamanı TRANSACTION zamanlanmış.|WFRuntime|  
|[1037 - RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|Ayrıntılı|Çalışma zamanı işlem durumu '%1' ile tamamlandı.|WFRuntime|  
|[1038 - EnterNoPersistBlock](1038-enternopersistblock.md)|Ayrıntılı|Herhangi bir kalıcı engelleme giriliyor.|WFRuntime|  
|[1039 - ExitNoPersistBlock](1039-exitnopersistblock.md)|Ayrıntılı|Herhangi bir kalıcı engelleme çıkılıyor.|WFRuntime|  
|[1040 - InArgumentBound](1040-inargumentbound.md)|Ayrıntılı|Bağımsız değişkeninde '%1' etkinliği '%2', DisplayName: '%3', InstanceId: '%4', değer ile ilişkili: %5.|WFActivities|  
|[1041 - WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|Bilgiler|WorkflowApplication ID: '%1', boş ve kalıcı.  Aşağıdaki işlem yapılmayacak: %2.|WFRuntime|  
|[1101 - WorkflowActivityStart](1101-workflowactivitystart.md)|Bilgiler|WorkflowInstance ID: '%1' Aktivita E2E|WFRuntime|  
|[1102 - WorkflowActivityStop](1102-workflowactivitystop.md)|Bilgiler|WorkflowInstance ID: '%1' Aktivita E2E|WFRuntime|  
|[1103 - WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|Bilgiler|WorkflowInstance ID: '%1' Aktivita E2E|WFRuntime|  
|[1104 - WorkflowActivityResume](1104-workflowactivityresume.md)|Bilgiler|WorkflowInstance ID: '%1' Aktivita E2E|WFRuntime|  
|[1124 - InvokeMethodIsStatic](1124-invokemethodisstatic.md)|Bilgiler|InvokeMethod '%1' - yöntemi statik bir değer.|WFRuntime|  
|[1125 - InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|Bilgiler|'%1' - InvokeMethod yöntemi statik değil.|WFRuntime|  
|[1126 - InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|Bilgiler|Etkinlik tarafından '%1' adlı bir yöntemde özel durum oluşturuldu. %2|WFRuntime|  
|[1131 - InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|Bilgiler|InvokeMethod '%1' - '%2' ve '%3', zaman uyumsuz desen yöntemi kullanır.|WFRuntime|  
|[1132 - InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|Bilgiler|'%1' - InvokeMethod yöntemi zaman uyumsuz desen kullanmaz.|WFRuntime|  
|[1140 - FlowchartStart](1140-flowchartstart.md)|Bilgiler|'%1' - Başlangıç akış zamanlandı.|WFActivities|  
|[1141 - FlowchartEmpty](1141-flowchartempty.md)|Uyarı|'%1' - Akış Çizelgesi etkinlik tarafından '%1' adlı bir yöntemde özel durum oluştu hiçbir Nodes.An ile yürütüldü. %2|WFActivities|  
|[1143 - FlowchartNextNull](1143-flowchartnextnull.md)|Bilgiler|Akış ' %1'/FlowStep - sonraki düğüme NULL'dur. Akış Çizelgesi yürütme sona erecek.|WFActivities|  
|[1146 - FlowchartSwitchCase](1146-flowchartswitchcase.md)|Bilgiler|Akış ' %1'/FlowSwitch - durum '%2' seçilmiştir.|WFActivities|  
|[1147 - FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|Bilgiler|Akış ' %1'/FlowSwitch - varsayılan durumda seçilmiştir.|WFActivities|  
|[1148 - FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|Bilgiler|Akış ' %1'/FlowSwitch - bir servis talebi etkinliği ne varsayılan ifade sonucu eşleşen servis talebi bulun. Akış Çizelgesi yürütme sona erecek.|WFActivities|  
|[1150 - CompensationState](1150-compensationstate.md)|Bilgiler|CompensableActivity '%1', '%2' durumda değil.|WFActivities|  
|[1223 - SwitchCaseNotFound](1223-switchcasenotfound.md)|Bilgiler|'%1' Switch etkinliği ifade sonucu eşleşen servis talebi bir etkinlik bulunamadı.|WFActivities|  
|[1449 - WfMessageReceived](1449-wfmessagereceived.md)|Bilgiler|İş akışı tarafından alınan ileti|WFServices|  
|[1450 - WfMessageSent](1450-wfmessagesent.md)|Bilgiler|İş akışından gönderilen ileti|WFServices|  
|[2021 - ExecuteWorkItemStart](2021-executeworkitemstart.md)|Ayrıntılı|İş öğesi başlangıcı yürütün|WFRuntime|  
|[2022 - ExecuteWorkItemStop](2022-executeworkitemstop.md)|Ayrıntılı|İş öğesi stop yürütün|WFRuntime|  
|[2023 - SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|Ayrıntılı|SendMessageChannelCache isabetsizliği|WFRuntime|  
|[2024 - InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|Ayrıntılı|'%1' faaliyete InternalCacheMetadata başlatıldı.|WFRuntime|  
|[2025 - InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|Ayrıntılı|'%1' faaliyete InternalCacheMetadata durduruldu.|WFRuntime|  
|[2026 - CompileVbExpressionStart](2026-compilevbexpressionstart.md)|Ayrıntılı|VB ifade '%1'|WFRuntime|  
|[2027 - CacheRootMetadataStart](2027-cacherootmetadatastart.md)|Ayrıntılı|'%1' faaliyete CacheRootMetadata başlatıldı|WFRuntime|  
|[2028 - CacheRootMetadataStop](2028-cacherootmetadatastop.md)|Ayrıntılı|CacheRootMetadata etkinliği %1 durduruldu.|WFRuntime|  
|[2029 - CompileVbExpressionStop](2029-compilevbexpressionstop.md)|Ayrıntılı|VB ifade derleme tamamlandı.|WFRuntime|  
|[2576 - TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|Bilgiler|TryCatch etkinlik '%1', '%2' türünde bir özel durum zachytila výjimku.|WFActivities|  
|[2577 - TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|Uyarı|TryCatch etkinlik '%1' bir alt etkinlik iptal etme sırasında bir özel durum oluşturdu.|WFActivities|  
|[2578 - TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|Uyarı|Catch veya Finally TryCatch etkinlik '%1' ile ilişkili olan etkinliği bir özel durum oluşturdu.|WFActivities|  
|[3501 - InferredContractDescription](3501-inferredcontractdescription.md)|Bilgiler|ContractDescription Adı = '%1' ve Namespace = '%2', WorkflowService çıkarılan.|WFServices|  
|[3502 - InferredOperationDescription](3502-inferredoperationdescription.md)|Bilgiler|Adlı OperationDescription '%1' = '%2' WorkflowService sözleşmede ortaya çıkan. IsOneWay = %3.|WFServices|  
|[3503 - DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|Uyarı|Yinelenen CorrelationQuery bulunduğu yerle bulundu = '%1'. Bu yinelenen bir sorgu bağıntı hesaplarken kullanılmayacak.|WFServices|  
|[3507 - ServiceEndpointAdded](3507-serviceendpointadded.md)|Bilgiler|Hizmet uç noktası adresi '%1', '%2' bağlama ve Sözleşme '%3' için eklendi.|WFServices|  
|[3508 - TrackingProfileNotFound](3508-trackingprofilenotfound.md)|Ayrıntılı|TrackingProfile ActivityDefinitionId bulunamadı ' %2' için '%1'. TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.|WFServices|  
|[3550 - BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|Bilgiler|'%1' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu belirli bir işlemi hazır olduğunda başka bir deneme yapılır.|WFServices|  
|[3551 - BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|Bilgiler|Hizmet örneği '%1' üzerinde '%2' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu belirli bir işlemi hazır olduğunda başka bir deneme yapılır.|WFServices|  
|[3552 - MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|Uyarı|'%1' 'MaxPendingMessagesPerChannel' sınırını azaltma ulaşıldı. Bu sınırı artırmak için BufferedReceiveServiceBehavior MaxPendingMessagesPerChannel özelliği ayarlayın.|Kota WFServices|  
|[3557 - TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|Bilgiler|CommittableTransaction kimliğiyle şirket EndCommit çağrısı = '%1', şu iletiyle bir TransactionException oluşturdu: '%2'.|WFServices|  
|[4201 - EndSqlCommandExecute](4201-endsqlcommandexecute.md)|Ayrıntılı|SQL komut yürütme bitiş: %1|WFInstanceStore|  
|[4202 - StartSqlCommandExecute](4202-startsqlcommandexecute.md)|Ayrıntılı|SQL komut yürütme başlatılıyor: %1|WFInstanceStore|  
|[4203 - RenewLockSystemError](4203-renewlocksystemerror.md)|Hata|Kilit zaman aşımı genişletmek için başarısız oldu, kilit zaman aşımı zaten geçirildi veya kilit sahibi silindi. SqlWorkflowInstanceStore durduruluyor.|WFInstanceStore|  
|[4205 - FoundProcessingError](4205-foundprocessingerror.md)|Hata|Komutu başarısız oldu: %1|WFInstanceStore|  
|[4206 - UnlockInstanceException](4206-unlockinstanceexception.md)|Hata|Örnek kilidini açmak çalışırken karşılaşılan %1 özel durumu.|WFInstanceStore|  
|[4207 - MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|Bilgiler|En fazla yeniden deneme sayısı arttıkça SQL komutunu yeniden deneniyor yukarı vererek yapıldı.|Kota WFInstanceStore|  
|[4208 - RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|Bilgiler|Bir SQL komutunu SQL hata numarası: %1'nedeniyle yeniden deneniyor.|WFInstanceStore|  
|[4209 - TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Hata|Bir SQL bağlantı açılmaya çalışılırken zaman aşımı. İşlem, %1 ' ayrılan süre içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.|WFInstanceStore|  
|[4210 - SqlExceptionCaught](4210-sqlexceptioncaught.md)|Uyarı|SQL özel durum sayısı %1 ileti %2 yakalandı.|WFInstanceStore|  
|[4211 - QueuingSqlRetry](4211-queuingsqlretry.md)|Uyarı|Sıraya alma SQL yeniden deneme gecikmesi %1 milisaniye ile.|WFInstanceStore|  
|[4212 - LockRetryTimeout](4212-lockretrytimeout.md)|Uyarı|Örnek kilidi çalışılırken zaman aşımı.  İşlem, %1 ' ayrılan süre içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.|WFInstanceStore|  
|[4213 - RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Hata|Çalıştırılabilir örnekleri algılama şu özel durum nedeniyle başarısız oldu|WFInstanceStore|  
|[4214 - InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Hata|Kurtarma örneği kilitleri şu özel durum nedeniyle başarısız oldu|WFInstanceStore|  
|[39456 - TrackingRecordDropped](39456-trackingrecorddropped.md)|Uyarı|ETW oturumu tarafından %2 sağlayıcısı için izin verilen en fazla kayıt %1 izleme boyutunu aşıyor|WFTracking|  
|[39457 - TrackingRecordRaised](39457-trackingrecordraised.md)|Bilgiler|İzleme kayıt %1 %2'ye yükseltilmiş.|WFRuntime|  
|[39458 - TrackingRecordTruncated](39458-trackingrecordtruncated.md)|Uyarı|%1 ETW oturumu %2 sağlayıcısı ile yazılmış kaydı İzleme kesildi. Veri ek açıklamaları/değişkenler/kullanıcı kaldırıldı|WFTracking|  
|[39459 - TrackingDataExtracted](39459-trackingdataextracted.md)|Ayrıntılı|İzleme verileri: %1 %2'etkinliği ayıklanan.|WFRuntime|  
|[39460 - TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|Uyarı|Ayıklanan bağımsız değişken/değişkeni '%1' serileştirilebilir değil.|WFTracking|  
|[57398 - MaxInstancesExceeded](57398-maxinstancesexceeded.md)|Uyarı|Sistem sınırını 'MaxConcurrentInstances' kısıtlama için basın. Bu kısıtlama için sınır %1'e ayarlanmıştır. Kısıtlama değeri öznitelik 'maxConcurrentInstances' serviceThrottle öğesinde değiştirerek veya davranışını denetlemek ServiceThrottlingBehavior 'MaxConcurrentInstances' özelliğini değiştirerek değiştirilebilir.|WFServices|
