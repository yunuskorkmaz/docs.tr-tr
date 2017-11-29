---
title: "&lt;ekleme&gt; , &lt;katılımcıları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d95c6d3768a26a8db92bf54bb454b350ced03d7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltparticipantsgt"></a>&lt;ekleme&gt; , &lt;katılımcıları&gt;
Çalışma zamanı ' doğrudan gösterilmesini izleme kayıtları dinleyen bir izleme katılımcı yapılandırın ve herhangi bir şekilde yapılandırılan işlem. Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.  
  
 İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
\<system.serviceModel >  
\<İzleme >  
\<Katılımcıları >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|name|İzleme katılımcı adını belirten dize.|  
|ProfilAdı|İzleme katılımcı abone izleme kayıtları tanımlayan izleme profilin adını belirten dize.|  
|türü|İzleme katılımcı türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Katılımcıların izleme listesi|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar. Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.  
  
 Birden çok izleme katılımcıları izleme olaylarını aynı anda kullanabilir. Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.  
  
 Standart izleme katılımcı hangi izleme kayıtları ETW oturumuna Yazar sağlanır. Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır. Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar. Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.  
  
 ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü. İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var. Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi. Bunlar tanımlandıktan sonra izleme katılımcı eklenen  **\<etwTracking >** hizmet davranışı. Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [İzleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Katılımcıların izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
