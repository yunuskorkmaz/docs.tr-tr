---
title: 101 - WorkflowInstanceUnhandledExceptionRecord
ms.date: 03/30/2017
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
ms.openlocfilehash: f62868a09b72ef4fe567fbedc1729cd6bad309f0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239763"
---
# <a name="101---workflowinstanceunhandledexceptionrecord"></a>101 - WorkflowInstanceUnhandledExceptionRecord

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|101|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Düzey|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı örneği Workflowunhandledexceptionrecord ' i yayıyorsa ETW izleme katılımcısı tarafından yayılır.  
  
## <a name="message"></a>İleti  

 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, özel durum = %9, ek açıklamalar = %10, ProfileName = %11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|ActivityDefinitionId|xs: String|İş akışındaki Kök etkinliğin adı|  
|Kaynak|xs: String|Hatalı kaynak etkinliğin adı, unhandledException ile sonuçlanır|  
|ID|xs: String|Hata kaynağı etkinliğinin etkinlik kimliği|  
|SourceInstanceId|xs: String|Hata kaynağı etkinliğinin etkinlik örneği kimliği|  
|SourceTypeName|xs: String|Hatalı olan kaynak etkinlik türü adı, unhandledException ile sonuçlanır|  
|Özel durum|xs: String|İşlenmeyen özel durum için özel durum ayrıntıları|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçim, ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' örneği olarak tanımlanmıştır: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
