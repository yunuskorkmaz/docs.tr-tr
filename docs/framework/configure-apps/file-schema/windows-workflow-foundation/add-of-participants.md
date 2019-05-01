---
title: <add> / <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 291d1a006bc16769e36774dd9507017cb555e547
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790383"
---
# <a name="add-of-participants"></a>\<Ekle >, \<katılımcıları >
Çalışma zamanını şuradan doğrudan yayılan izleme kayıtları için bekleyen bir izleme katılımcı yapılandırın ve bunları yapılandırılan hangi yolla işlem. Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.  
  
 İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz. [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
\<system.serviceModel>  
\<İzleme >  
\<Katılımcıları >  
\<Ekle >  
  
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
|ProfilAdı|İzleme kayıtları tanımlayan izleme profilinin adını belirten bir dize için izleme katılımcı abone oldu.|  
|türü|İzleme katılımcı türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Katılımcıların izleme listesi|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme katılımcıları akışından yayılan izleme verilerini almak için kullanılır ve farklı ortamları depolar. Benzer şekilde, herhangi işleme kayıtları da içinde izleme katılımcı yapılabilir izleme gönderin.  
  
 Aynı anda birden çok izleme katılımcıları izleme olaylarını kullanabilir. Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.  
  
 Standart izleme katılımcı, izleme kayıtları bir ETW oturumu Yazar sağlanır. Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranışı ekleyerek yapılandırılır. Etkinleştirme bir ETW İzleme katılımcı olacak şekilde kayıtları izleme Olay Görüntüleyicisi'görüntülemesini sağlar. Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.  
  
 ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü. İzleme katılımcı abone izleme kayıtları belirtmek için ile ilişkili bir profil var. Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi. Bunlar tanımlandıktan izleme katılımcı eklenir  **\<etwTracking >** hizmet davranışı. Böylece bunlar izleme kayıtları almak başlayabilirsiniz bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekleyecektir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
