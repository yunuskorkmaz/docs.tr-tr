---
title: <add> / <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152365"
---
# <a name="add-of-participants"></a>\<\<katılımcıların> ekleme>
Çalışma zamanından doğrudan yayılan izleme kayıtlarını dinleyen bir izleme katılımcısını yapılandırın ve yapılandırılan şekilde işleyin. Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.  
  
 İş akışı izleme ve izleme katılımcıları hakkında daha fazla bilgi için İş [Akışı İzleme ve İzleme katılımcılarını](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) görün. [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md)  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<katılımcılar>**](participants.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**  
  
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
|ad|İzleme katılımcısının adını belirten bir dize.|  
|ProfilAdı|İzleme üyesinin abone olduğu izleme kayıtlarını tanımlayan izleme profilinin adını belirten dize.|  
|type|İzleme katılımcısının türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<katılımcılar>](participants.md)|İzleme katılımcılarının listesi|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme katılımcıları, iş akışından yayılan izleme verilerini almak ve farklı ortamlara depolamak için kullanılır. Aynı şekilde, izleme Kayıtları üzerinde herhangi bir posta işleme de izleme katılımcısı içinde yapılabilir.  
  
 Birden çok izleme katılımcısı izleme olaylarını aynı anda tüketebilir. Her izleme katılımcısı farklı bir izleme profili ile ilişkilendirilebilir.  
  
 İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır. Katılımcı, yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek iş akışı hizmetinde yapılandırılır. Bir ETW izleme katılımcısını etkinleştirmek, izleme kayıtlarının olay görüntüleyicisinde görüntülenmesini sağlar. Bu gereksinimlerinizi karşılamazsa, özel bir izleme katılımcısı da yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılan standart ETW izleme katılımcısını gösterir.  
  
 ETW İzleme Katılımcısının İzleme Kayıtlarını ETW'ye yazmak için kullandığı Sağlayıcı ** \<Kimliği, tanılama>** bölümünde tanımlanır. İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için onunla ilişkili bir profili vardır. Bu, ** \<>öğe ekle** öğesinin **profileName** özniteliği ile tanımlanır. Bunlar tanımlandıktan sonra, İzleme Katılımcısı ** \<etwTracking>** hizmet davranışına eklenir. Bu, seçili İzleme Katılımcılarını İş Akışı örneğinin uzantılarına ekleyerek İzleme Kayıtlarını almaya başlar.  
  
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
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Katılımcıları](../../../windows-workflow-foundation/tracking-participants.md)
