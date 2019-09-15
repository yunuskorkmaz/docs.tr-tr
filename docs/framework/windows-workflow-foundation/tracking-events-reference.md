---
title: İzleme Olayları Başvurusu
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: af0c4441b89345b67c46c714d9ab3e5ceb9e3d6f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988976"
---
# <a name="tracking-events-reference"></a>İzleme Olayları Başvurusu
Yürütme sırasında, içinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bir iş akışı, ömrü boyunca çeşitli aşamalar arasında gezindiğinde olayları izleme işlemleri gerçekleştirir. Ana bilgisayar bu olaylara abone olabilir ve ömrü boyunca iş akışının ilerleme durumu üzerinde güncel kalır. Oluşturulan izleme olayları bu bölümde ele alınmıştır.  
  
## <a name="event-reference"></a>Olay başvurusu  
  
|Olay Kimliği|Olay düzeyi|Olay Iletisi|anahtar sözcükler|  
|--------------|-----------------|-------------------|--------------|  
|[100 - WorkflowInstanceRecord](100-workflowinstancerecord.md)|Bilgiler|TrackRecord = Workflowcerecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, durum =% 5, ek açıklama =% 6, ProfileName =% 7|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[101 - WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Hata|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, SourceName =% 5, SourceId =% 6, SourceInstanceId =% 7, SourceTypeName =% 8, özel durum =% 9, ek açıklama =% 10, ProfileName = % 11|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[102 - WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|Uyarı|TrackRecord = WorkflowInstanceAbortedRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, ek açıklama =% 6, ProfileName =% 7|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[103 - ActivityStateRecord](103-activitystaterecord.md)|Bilgiler|TrackRecord = ActivityStateRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, durum =% 4, ad =% 5, ActivityID =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, arguments =% 9, değişkenler =% 10, ek açıklama =% 11, ProfileName =% 12|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[104 - ActivityScheduledRecord](104-activityscheduledrecord.md)|Bilgiler|TrackRecord = ActivityScheduledRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ad =% 4, ActivityID =% 5, ActivityInstanceId =% 6, ActivityTypeName =% 7, ChildActivityName =% 8, ChildActivityId =% 9, ChildActivityInstanceId =% 10, ChildActivityTypeName =% 11, ek açıklamalar =% 12, ProfileName =% 13|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[105 - FaultPropagationRecord](105-faultpropagationrecord.md)|Uyarı|TrackRecord = FaultPropagationRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, FaultSourceActivityName =% 4, FaultSourceActivityId =% 5, FaultSourceActivityInstanceId =% 6, FaultSourceActivityTypeName =% 7, FaultHandlerActivityName =% 8, FaultHandlerActivityId =% 9, FaultHandlerActivityInstanceId =% 10, FaultHandlerActivityTypeName =% 11, hata =% 12, IsFaultSource =% 13, ek açıklamalar =% 14, ProfileName =% 15|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[106 - CancelRequestRecord](106-cancelrequestrecord.md)|Bilgiler|TrackRecord = CancelRequestedRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ad =% 4, ActivityID =% 5, ActivityInstanceId =% 6, ActivityTypeName =% 7, ChildActivityName =% 8, ChildActivityId =% 9, ChildActivityInstanceId =% 10, ChildActivityTypeName =% 11, ek açıklamalar =% 12, ProfileName =% 13|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[107 -- BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|Bilgiler|TrackRecord = BookmarkResumptionRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ad =% 4, SubInstanceID =% 5, OwnerActivityName =% 6, OwnerActivityId =% 7, OwnerActivityInstanceId =% 8, OwnerActivityTypeName =% 9, ek açıklama =% 10, ProfileName = % 11|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[108 - CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|Bilgiler|TrackRecord = CustomTrackingRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ad =% 4, ActivityName =% 5, ActivityID =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, veri =% 9, ek açıklamalar =% 10, ProfileName =% 11|Kullanıcıetkinlikleri, EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[110 - CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|Uyarı|TrackRecord = CustomTrackingRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ad =% 4, ActivityName =% 5, ActivityID =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, veri =% 9, ek açıklamalar =% 10, ProfileName =% 11|Kullanıcıetkinlikleri, EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[111 - CustomTrackingRecordError](111-customtrackingrecorderror.md)|Hata|TrackRecord = CustomTrackingRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ad =% 4, ActivityName =% 5, ActivityID =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, veri =% 9, ek açıklamalar =% 10, ProfileName =% 11|Kullanıcıetkinlikleri, EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[112 - WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|Bilgiler|TrackRecord = Workflowcesuspendedrecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, ek açıklamalar =% 6, ProfileName =% 7|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[113 - WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Hata|TrackRecord = Workflowınstancesonlandırıo kaydı, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, ek açıklama =% 6, ProfileName =% 7|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|[114 - WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|Bilgiler|TrackRecord = Workflowcerecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, durum =% 5, ek açıklama =% 6, ProfileName =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[115 - WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|Uyarı|TrackRecord = WorkflowInstanceAbortedRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, ek açıklama =% 6, ProfileName =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[116 - WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|Bilgiler|TrackRecord = Workflowcesuspendedrecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, ek açıklamalar =% 6, ProfileName =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[117 - WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Hata|TrackRecord = Workflowınstancesonlandırıo kaydı, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, ek açıklama =% 6, ProfileName =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[118 - WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Hata|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, SourceName =% 5, SourceId =% 6, SourceInstanceId =% 7, SourceTypeName =% 8, özel durum =% 9, ek açıklama =% 10, ProfileName = % 11, WorkflowDefinitionIdentity =% 12|HealthMonitoring, WFTrackingHealthMonitoring, WFTracking|  
|[119 - WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|Bilgiler|TrackRecord = WorkflowInstanceUpdatedRecord, InstanceId =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, State =% 5, OriginalDefinitionIdentity =% 6, UpdatedDefinitionIdentity =% 7, ek açıklama =% 8, ProfileName =% 9|HealthMonitoring, WFTracking|  
|[225 - TraceCorrelationKeys](225-tracecorrelationkeys.md)|Bilgiler|'% 3 ' üst kapsamındaki '% 2 ' değerleri kullanılarak '% 1 ' bağıntı anahtarı hesaplandı.|WFServices sorunlarını giderme|  
|[440 - StartSignpostEvent1](440-startsignpostevent.md)|Bilgiler|Etkinlik sınırı.|WFServices sorunlarını giderme|  
|[441- StopSignpostEvent1](441-stopsignpostevent.md)|Bilgiler|Etkinlik sınırı.|WFServices sorunlarını giderme|  
|[1001 - WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' kapalı durumda tamamlandı.|WFRuntime|  
|[1002 - WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|Bilgiler|WorkflowApplication kimliği: '% 1 ' sonlandırıldı. Hatalı durumda bir özel durumla tamamlandı.|WFRuntime|  
|[1003 - WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' Iptal edildi durumunda tamamlandı.|WFRuntime|  
|[1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' bir özel durumla durduruldu.|WFRuntime|  
|[1005 - WorkflowApplicationIdled](1005-workflowapplicationidled.md)|Bilgiler|WorkflowApplication kimliği: '% 1 ' boşta oldu.|WFRuntime|  
|[1006 - WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Hata|WorkflowInstance kimliği: '% 1 ' işlenmeyen bir özel durumla karşılaştı.  DisplayName: '% 3 ' olan '% 2 ' etkinliğinden kaynaklanan özel durum.  Şu işlem gerçekleştirilecek:% 4.|WFRuntime|  
|[1007 - WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|Bilgiler|WorkflowApplication kimliği: '% 1 ' kalıcı oldu.|WFRuntime|  
|[1008 - WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' kaldırıldı.|WFRuntime|  
|[1009 - ActivityScheduled](1009-activityscheduled.md)|Bilgiler|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 4 ', DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 1 ' üst etkinliği|WFRuntime|  
|[1010 - ActivityCompleted](1010-activitycompleted.md)|Bilgiler|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 4 ', DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 1 ' üst etkinliği|WFRuntime|  
|[1011 - ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir ExecuteActivityWorkItem zamanlandı.|WFRuntime|  
|[1012 - StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir ExecuteActivityWorkItem 'ın yürütülmesi başlatılıyor.|WFRuntime|  
|[1013 - CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir ExecuteActivityWorkItem tamamlandı.|WFRuntime|  
|[1014 - ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' üst etkinliği için bir CompletionWorkItem zamanlandı.  DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' Activity 'si tamamlandı.|WFRuntime|  
|[1015 - StartCompletionWorkItem](1015-startcompletionworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' üst etkinliği için bir CompletionWorkItem 'ın yürütülmesi başlatılıyor. DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' Activity 'si tamamlandı.|WFRuntime|  
|[1016 - CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' üst etkinliği için bir CompletionWorkItem tamamlandı. DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' Activity 'si tamamlandı.|WFRuntime|  
|[1017 - ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir bir bir bir bir bir bir bir bir bir bir bir bir|WFRuntime|  
|[1018 - StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir bir bir bir bir bir bir bir bir bir bir bir bir|WFRuntime|  
|[1019 - CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir bir bir bir bir bir bir bir bir bir bir bir|WFRuntime|  
|[1020 - CreateBookmark](1020-createbookmark.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir yer Işareti oluşturuldu.  BookmarkName:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1021 - ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir BookmarkWorkItem zamanlandı.  BookmarkName:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1022 - StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir BookmarkWorkItem 'ın yürütülmesi başlatılıyor.  BookmarkName:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1023 - CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir BookmarkWorkItem tamamlandı. BookmarkName:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1024 - CreateBookmarkScope](1024-createbookmarkscope.md)|Ayrıntılı|Bir BookmarkScope oluşturuldu:% 1.|WFRuntime|  
|[1025 - BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|Ayrıntılı|TemporaryId olan BookmarkScope: '% 1 ', '% 2 ' kimliğiyle başlatıldı.|WFRuntime|  
|[1026 - ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir TransactionContextWorkItem zamanlandı.|WFRuntime|  
|[1027 - StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir TransactionContextWorkItem 'ın yürütülmesi başlatılıyor.|WFRuntime|  
|[1028 - CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir TransactionContextWorkItem tamamlandı.|WFRuntime|  
|[1029 - ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir FaultWorkItem zamanlandı.  Özel durum DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' etkinliğinden yayılmıştı.|WFRuntime|  
|[1030 - StartFaultWorkItem](1030-startfaultworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir FaultWorkItem 'ın yürütülmesi başlatılıyor.  Özel durum DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' etkinliğinden yayılmıştı.|WFRuntime|  
|[1031 - CompleteFaultWorkItem](1031-completefaultworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir FaultWorkItem tamamlandı. Özel durum DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' etkinliğinden yayılmıştı.|WFRuntime|  
|[1032 - ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir çalışma zamanı çalışma öğesi zamanlandı.|WFRuntime|  
|[1033 - StartRuntimeWorkItem](1033-startruntimeworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir çalışma zamanı çalışma öğesinin yürütülmesine başlanıyor.|WFRuntime|  
|[1034 - CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si için bir çalışma zamanı çalışma öğesi tamamlandı.|WFRuntime|  
|[1035 - RuntimeTransactionSet](1035-runtimetransactionset.md)|Ayrıntılı|Çalışma zamanı işlemi, DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' etkinliğine göre ayarlandı.  Yürütme, DisplayName: '% 5 ', InstanceId: '% 6 ' olan '% 4 ' etkinliğine yalıtılmış.|WFRuntime|  
|[1036 - RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|Ayrıntılı|DisplayName: '% 2 ', InstanceId: '% 3 ' olan '% 1 ' Activity 'si çalışma zamanı işleminin tamamlanmasını zamanladı.|WFRuntime|  
|[1037 - RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|Ayrıntılı|Çalışma zamanı işlemi '% 1 ' durumuyla tamamlandı.|WFRuntime|  
|[1038 - EnterNoPersistBlock](1038-enternopersistblock.md)|Ayrıntılı|Kalıcı olmayan bir blok giriliyor.|WFRuntime|  
|[1039 - ExitNoPersistBlock](1039-exitnopersistblock.md)|Ayrıntılı|Kalıcı olmayan bir bloktan çıkılıyor.|WFRuntime|  
|[1040 - InArgumentBound](1040-inargumentbound.md)|Ayrıntılı|DisplayName: '% 3 ', InstanceId: '% 4 ' olan '% 2 ' etkinliğindeki '% 1 ' bağımsız değişkeninde% 5 değeri ile bağlı.|WFActivities|  
|[1041 - WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|Bilgiler|WorkflowApplication kimliği: '% 1 ' boşta ve sürekli tablo.  Şu işlem gerçekleştirilecek:% 2.|WFRuntime|  
|[1101 - WorkflowActivityStart](1101-workflowactivitystart.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' E2E etkinliği|WFRuntime|  
|[1102 - WorkflowActivityStop](1102-workflowactivitystop.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' E2E etkinliği|WFRuntime|  
|[1103 - WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' E2E etkinliği|WFRuntime|  
|[1104 - WorkflowActivityResume](1104-workflowactivityresume.md)|Bilgiler|WorkflowInstance kimliği: '% 1 ' E2E etkinliği|WFRuntime|  
|[1124 - InvokeMethodIsStatic](1124-invokemethodisstatic.md)|Bilgiler|InvokeMethod '% 1 '-Yöntem Static.|WFRuntime|  
|[1125 - InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|Bilgiler|InvokeMethod '% 1 '-metot static değil.|WFRuntime|  
|[1126 - InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|Bilgiler|'% 1 ' etkinliğinin çağırdığı yöntemde bir özel durum oluşturuldu. %2|WFRuntime|  
|[1131 - InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|Bilgiler|InvokeMethod '% 1 '-Yöntem '% 2 ' ve '% 3 ' zaman uyumsuz modelini kullanıyor.|WFRuntime|  
|[1132 - InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|Bilgiler|InvokeMethod '% 1 '-yöntem zaman uyumsuz model kullanmıyor.|WFRuntime|  
|[1140 - FlowchartStart](1140-flowchartstart.md)|Bilgiler|'% 1 ' akış çizelgesi-başlatma zamanlandı.|WFActivities|  
|[1141 - FlowchartEmpty](1141-flowchartempty.md)|Uyarı|'% 1 ' akış çizelgesi, hiçbir düğüm olmadan yürütüldü. '% 1 ' etkinliğinin çağırdığı yöntemde bir özel durum oluşturuldu. %2|WFActivities|  
|[1143 - FlowchartNextNull](1143-flowchartnextnull.md)|Bilgiler|Akış Çizelgesi '% 1 '/FlowStep-Next node null. Akış çizelgesi yürütme sona acaktır.|WFActivities|  
|[1146 - FlowchartSwitchCase](1146-flowchartswitchcase.md)|Bilgiler|Flowchart '% 1 '/FlowSwitch-Case '% 2 ' seçildi.|WFActivities|  
|[1147 - FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|Bilgiler|Akış Çizelgesi '% 1 '/FlowSwitch-varsayılan durum seçildi.|WFActivities|  
|[1148 - FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|Bilgiler|Akış Çizelgesi '% 1 '/FlowSwitch-bir Case etkinliği veya Ifade sonucuyla eşleşen bir varsayılan durum bulamıyor. Akış çizelgesi yürütme sona acaktır.|WFActivities|  
|[1150 - CompensationState](1150-compensationstate.md)|Bilgiler|CompensableActivity '% 1 ', '% 2 ' durumunda.|WFActivities|  
|[1223 - SwitchCaseNotFound](1223-switchcasenotfound.md)|Bilgiler|'% 1 ' Switch etkinliği Ifade sonucuyla eşleşen bir Case etkinliği bulamadı.|WFActivities|  
|[1449 - WfMessageReceived](1449-wfmessagereceived.md)|Bilgiler|İleti iş akışı tarafından alındı|WFServices|  
|[1450 - WfMessageSent](1450-wfmessagesent.md)|Bilgiler|İleti iş akışından gönderildi|WFServices|  
|[2021 - ExecuteWorkItemStart](2021-executeworkitemstart.md)|Ayrıntılı|Çalışma öğesi başlangıcını yürütme|WFRuntime|  
|[2022 - ExecuteWorkItemStop](2022-executeworkitemstop.md)|Ayrıntılı|İş öğesini Yürüt Durdur|WFRuntime|  
|[2023 - SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|Ayrıntılı|SendMessageChannelCache isabetsizliği|WFRuntime|  
|[2024 - InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|Ayrıntılı|InternalCacheMetadata, '% 1 ' etkinliğinde başladı.|WFRuntime|  
|[2025 - InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|Ayrıntılı|InternalCacheMetadata, '% 1 ' etkinliğinde durdu.|WFRuntime|  
|[2026 - CompileVbExpressionStart](2026-compilevbexpressionstart.md)|Ayrıntılı|'% 1 ' VB ifadesi derleniyor|WFRuntime|  
|[2027 - CacheRootMetadataStart](2027-cacherootmetadatastart.md)|Ayrıntılı|CacheRootMetadata, '% 1 ' etkinliğinde başladı|WFRuntime|  
|[2028 - CacheRootMetadataStop](2028-cacherootmetadatastop.md)|Ayrıntılı|CacheRootMetadata,% 1 etkinliğinde durdu.|WFRuntime|  
|[2029 - CompileVbExpressionStop](2029-compilevbexpressionstop.md)|Ayrıntılı|VB ifadesinin derlenmesi bitti.|WFRuntime|  
|[2576 - TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|Bilgiler|'% 1 ' TryCatch etkinliği '% 2 ' türünde bir özel durum yakaladı.|WFActivities|  
|[2577 - TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|Uyarı|'% 1 ' TryCatch etkinliğinin bir alt etkinliği iptal işlemi sırasında özel durum oluşturdu.|WFActivities|  
|[2578 - TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|Uyarı|'% 1 ' TryCatch etkinliğiyle ilişkili bir catch veya finally etkinliği özel durum oluşturdu.|WFActivities|  
|[3501 - InferredContractDescription](3501-inferredcontractdescription.md)|Bilgiler|Name = '% 1 ' ve Namespace = '% 2 ' olan ContractDescription WorkflowService 'dan çıkarsandı.|WFServices|  
|[3502 - InferredOperationDescription](3502-inferredoperationdescription.md)|Bilgiler|'% 2 ' sözleşmesindeki Name = '% 1 ' olan OperationDescription WorkflowService 'dan çıkarsandı. IsOneWay =% 3.|WFServices|  
|[3503 - DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|Uyarı|Burada = '% 1 ' olan yinelenen bir CorrelationQuery bulundu. Bu yinelenen sorgu, bağıntı hesaplanırken kullanılmayacak.|WFServices|  
|[3507 - ServiceEndpointAdded](3507-serviceendpointadded.md)|Bilgiler|Adres '% 1 ', bağlama '% 2 ' ve Sözleşme '% 3 ' için bir hizmet uç noktası eklendi.|WFServices|  
|[3508 - TrackingProfileNotFound](3508-trackingprofilenotfound.md)|Ayrıntılı|'% 2 ' ActivityDefinitionId için TrackingProfile '% 1 ' bulunamadı. TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.|WFServices|  
|[3550 - BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|Bilgiler|'% 1 ' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.|WFServices|  
|[3551 - BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|Bilgiler|'% 1 ' hizmet örneğindeki '% 2 ' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.|WFServices|  
|[3552 - MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|Uyarı|' Maxpendingiletiperchannel ' kısıtlama '% 1 ' sınırına ulaşıldı. Bu sınırı artırmak için, BufferedReceiveServiceBehavior üzerindeki Maxpendingiletiperchannel özelliğini ayarlayın.|Kota WFServices|  
|[3557 - TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|Bilgiler|ID = '% 1 ' olan CommittableTransaction üzerinde Endcommıt çağrısı şu iletiyle bir TransactionException oluşturdu: '% 2 '.|WFServices|  
|[4201 - EndSqlCommandExecute](4201-endsqlcommandexecute.md)|Ayrıntılı|SQL komutunun yürütülmesini sonlandır:% 1|Wfınstancestore|  
|[4202 - StartSqlCommandExecute](4202-startsqlcommandexecute.md)|Ayrıntılı|SQL komutu yürütme başlatılıyor:% 1|Wfınstancestore|  
|[4203 - RenewLockSystemError](4203-renewlocksystemerror.md)|Hata|Kilit süre sonu genişletilemedi, kilit süre sonu zaten geçti veya kilit sahibi silindi. SqlWorkflowInstanceStore durduruluyor.|Wfınstancestore|  
|[4205 - FoundProcessingError](4205-foundprocessingerror.md)|Hata|Komut başarısız oldu:% 1|Wfınstancestore|  
|[4206 - UnlockInstanceException](4206-unlockinstanceexception.md)|Hata|Örneğin kilidi açılmaya çalışılırken% 1 özel durumuyla karşılaşıldı.|Wfınstancestore|  
|[4207 - MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|Bilgiler|En fazla yeniden deneme sayısı gerçekleştirildiğinden bir SQL komutunun yeniden denenmesine izin veriliyor.|Kota Wfınstancestore|  
|[4208 - RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|Bilgiler|% 1 numaralı SQL hatası nedeniyle bir SQL komutu yeniden deneniyor.|Wfınstancestore|  
|[4209 - TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Hata|SQL bağlantısı açılmaya çalışılırken zaman aşımı oluştu. İşlem ayrılan% 1 zaman aşımı süresi içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.|Wfınstancestore|  
|[4210 - SqlExceptionCaught](4210-sqlexceptioncaught.md)|Uyarı|Yakalanan SQL özel durum numarası% 1 ileti% 2.|Wfınstancestore|  
|[4211 - QueuingSqlRetry](4211-queuingsqlretry.md)|Uyarı|SQL yeniden denemesi% 1 milisaniyesi ile sıraya alınıyor.|Wfınstancestore|  
|[4212 - LockRetryTimeout](4212-lockretrytimeout.md)|Uyarı|Örnek kilidi alınmaya çalışılırken zaman aşımı oluştu.  İşlem ayrılan% 1 zaman aşımı süresi içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.|Wfınstancestore|  
|[4213 - RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Hata|Aşağıdaki özel durum nedeniyle çalıştırılabilir örneklerin algılanması başarısız oldu|Wfınstancestore|  
|[4214 - InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Hata|Aşağıdaki özel durum nedeniyle örnek kilitleri kurtarma başarısız oldu|Wfınstancestore|  
|[39456 - TrackingRecordDropped](39456-trackingrecorddropped.md)|Uyarı|% 1 izleme kaydının boyutu% 2 sağlayıcısının ETW oturumunun izin verdiği üst sınırı aşıyor|WFTracking|  
|[39457 - TrackingRecordRaised](39457-trackingrecordraised.md)|Bilgiler|% 1 izleme kaydı% 2 öğesine yükseltildi.|WFRuntime|  
|[39458 - TrackingRecordTruncated](39458-trackingrecordtruncated.md)|Uyarı|% 2 sağlayıcısı ile ETW oturumuna yazılan% 1 izleme kaydı kesilmiş. Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı|WFTracking|  
|[39459 - TrackingDataExtracted](39459-trackingdataextracted.md)|Ayrıntılı|% 1 izleme verileri% 2 etkinliğinde ayıklandı.|WFRuntime|  
|[39460 - TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|Uyarı|Ayıklanan bağımsız değişken/değişken '% 1 ' seri hale getirilebilir değil.|WFTracking|  
|[57398 - MaxInstancesExceeded](57398-maxinstancesexceeded.md)|Uyarı|Sistem kısıtlama ' MaxConcurrentInstances ' için belirlenen sınıra ulaştı. Bu kısıtlama için sınır% 1 olarak ayarlandı. ' MaxConcurrentInstances ' özniteliği Servicekısıtlaması öğesinde değiştirilerek veya Behavior Servicekısıtlar Lingbehavior üzerinde ' MaxConcurrentInstances ' özelliği değiştirilerek kısıtlama değeri değiştirilebilir.|WFServices|
