---
title: İzleme Profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: ceeb0f5533bb4c637ea7df52249f5b00067d9b3d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551393"
---
# <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.

## <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, bir iş akışı örneği için hangi izleme bilgilerinin yayınlandığını belirtmek için kullanılır. Hiçbir profil belirtilmemişse, tüm izleme olayları yayınlanır. Bir profil belirtilmişse, profilde belirtilen izleme olayları yayınlanır. İzleme gereksinimlerinize bağlı olarak, çok genel olan bir profil yazabilirsiniz, bu, bir iş akışındaki küçük bir üst düzey durum değişikliği kümesine abone olabilir. Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok ayrıntılı bir profil oluşturabilirsiniz.

Profiller bildirimi, standart bir .NET Framework yapılandırma dosyası içinde veya kodda belirtilen XML öğeleri olarak kendini takip ediyor. Aşağıdaki örnek, bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] yapılandırma dosyasındaki izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilidir.

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

Aşağıdaki örnek, kod kullanılarak oluşturulan eşdeğer izleme profilini gösterir.

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

İzleme kayıtları, bir izleme profili içindeki görünürlük modu aracılığıyla özniteliği kullanılarak filtrelenir <xref:System.Activities.Tracking.ImplementationVisibility> . Bileşik etkinlik, uygulamasını oluşturan diğer etkinlikleri içeren en üst düzey bir etkinliktir. Görünürlük modu, uygulamayı oluşturan etkinliklerin izlendiğini belirtmek için bir iş akışı etkinliği içinde bileşik etkinliklerden yayılan izleme kayıtlarını belirtir. Görünürlük modu, izleme profili düzeyinde geçerlidir. Bir iş akışı içindeki bireysel etkinliklerin izleme kayıtlarının filtrelenmesi, izleme profili içindeki sorgular tarafından denetlenir. Daha fazla bilgi için bu belgedeki **profil sorgu türlerini izleme** bölümüne bakın.

İzleme profilindeki özniteliği tarafından belirtilen iki görünürlük modu `implementationVisibility` `RootScope` ve ' dir `All` . Modunun kullanılması, `RootScope` bileşik etkinliğin bir iş akışının kökü olmadığı durumda bir etkinliğin uygulanmasını oluşturan etkinliklerin izleme kayıtlarını bastırır. Bu, diğer etkinlikleri kullanarak uygulanan bir etkinlik bir iş akışına eklendiğinde ve `implementationVisibility` RootScope olarak ayarlandığında, yalnızca bu bileşik etkinliğin içindeki en üst düzey etkinliğin izlendiğine ilişkin anlamına gelir. Bir etkinlik iş akışının köküdür, etkinliğin uygulanması iş akışının kendisidir ve izleme kayıtları, uygulamayı oluşturan etkinlikler için yayınlanır. All modunun kullanılması, tüm izleme kayıtlarının kök etkinlik ve tüm bileşik etkinlikleri için oluşturulmasına izin verir.

Örneğin, *MyActivity* , uygulamasında iki etkinlik ( *Activity1* ve *Activity2*) içeren bir bileşik etkinlik olduğunu varsayalım. Bu etkinlik bir iş akışına eklendiğinde ve izleme, olarak ayarlanmış bir izleme profili ile etkinleştirildiğinde `implementationVisibility` `RootScope` , izleme kayıtları yalnızca *MyActivity*için tasarlanmıştır. Ancak, *Activity1* ve *Activity2*etkinlikleri için hiçbir kayıt yayınlanmadı.

Ancak, `implementationVisibility` izleme profili için özniteliği olarak ayarlandıysa `All` , izleme kayıtları yalnızca *MyActivity*için değil, *Activity1* ve *Activity2*etkinlikleri için de geçerlidir.

`implementationVisibility`Bayrak aşağıdaki izleme kayıt türleri için geçerlidir:

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> Etkinlik uygulamasından yayılan CustomTrackingRecords, ImplementationVisibility ayarı tarafından filtrelenmez.

`implementationVisibility`İşlevsellik, <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> koddaki izleme profilinde aşağıdaki gibi belirtilir:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

`implementationVisibility`İşlevselliği, <xref:System.Activities.Tracking.ImplementationVisibility.All> bir yapılandırma dosyasındaki izleme profilinde olarak aşağıdaki gibi belirtilir:

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

`ImplementationVisibility`İzleme profilindeki ayar isteğe bağlıdır. Varsayılan olarak, değeri olarak ayarlanır `RootScope` . Bu özniteliğin değerleri de büyük/küçük harfe duyarlıdır.

### <a name="tracking-profile-query-types"></a>İzleme profili sorgu türleri

İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır. Farklı nesne sınıflarına abone olmanıza imkan tanıyan birkaç sorgu türü vardır <xref:System.Activities.Tracking.TrackingRecord> . İzleme profilleri, yapılandırma veya kod aracılığıyla belirtilebilir. En yaygın sorgu türleri şunlardır:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery> -Bunu, daha önce gösterilen ve gibi iş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanın `Started` `Completed` . <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Abone olabilecek durumlar <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfında belirtilir.

  Kullanılarak örnek durum için iş akışı örnek düzeyi izleme kayıtlarına abone olmak için kullanılan yapılandırma veya kod `Started` <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.ActivityStateQuery> -Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için bunu kullanın. Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz. Bu sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için için gereklidir <xref:System.Activities.Tracking.ActivityStateRecord> . Abone olunacak durumlar içinde belirtilir <xref:System.Activities.Tracking.ActivityStates> .

  Etkinlik için kullanan etkinlik durumu izleme kayıtlarını abone yapmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.ActivityStateQuery> `SendEmailActivity` Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > Birden çok activityStateQuery öğesi aynı ada sahip ise, izleme profilinde yalnızca son öğedeki durumlar kullanılır.

- <xref:System.Activities.Tracking.ActivityScheduledQuery> -Bu sorgu, bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemenize olanak sağlar. Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.ActivityScheduledRecord> .

  Kullanılarak zamanlanmakta olan alt etkinlikle ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod `SendEmailActivity` <xref:System.Activities.Tracking.ActivityScheduledQuery> Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.FaultPropagationQuery> -Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bunu kullanın. Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.FaultPropagationRecord> .

  Kullanılarak hata yayılmaya ilişkin kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.FaultPropagationQuery> Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CancelRequestedQuery> -Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere bunu kullanın. Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.CancelRequestedRecord> .

  Kullanılarak etkinlik iptaline ilişkin kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.CancelRequestedQuery> Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CustomTrackingQuery> -Kod etkinliklerinizde tanımladığınız olayları izlemek için bunu kullanın. Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.CustomTrackingRecord> .

  Kullanılarak özel izleme kayıtlarıyla ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.CustomTrackingQuery> Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.BookmarkResumptionQuery> -Bunu, bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanın. Bu sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için için gereklidir <xref:System.Activities.Tracking.BookmarkResumptionRecord> .

  Kullanılarak yer işareti sürdürme ile ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.BookmarkResumptionQuery> Aşağıdaki örnekte gösterilmiştir.

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a>Ek Açıklamalar

Ek açıklamalar, derleme zamanından sonra yapılandırılabilecek bir değer ile izleme kayıtlarını rastgele etiketlemenize olanak tanır. Örneğin, "posta sunucusu" = = "mail Sunucu1" ile etiketlenecek birkaç iş akışı arasında birkaç izleme kaydının olmasını isteyebilirsiniz. Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.

Bunu gerçekleştirmek için aşağıdaki örnekte gösterildiği gibi bir izleme sorgusuna ek açıklama eklenir.

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a>Izleme profili oluşturma

İzleme sorgusu öğeleri, bir XML yapılandırma dosyası veya kodu kullanarak bir izleme profili oluşturmak için kullanılır [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] . Bir yapılandırma dosyası kullanılarak oluşturulan izleme profiline bir örnek aşağıda verilmiştir.

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> Iş akışı hizmet ana bilgisayarını kullanan bir WF için, izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur. İzleme profilini ve izleme sorgusu API 'sini kullanarak kodla bir izleme profili oluşturmak da mümkündür.

XML yapılandırma dosyası olarak yapılandırılmış bir profil, bir davranış uzantısı kullanılarak bir izleme katılımcısına uygulanır. Bu, [bir Iş akışı Için Izlemeyi yapılandırırken](configuring-tracking-for-a-workflow.md)sonraki bölümde açıklandığı şekilde bir WorkflowServiceHost 'a eklenir.

Konak tarafından yayılan izleme kayıtlarının ayrıntı düzeyi, izleme profili içindeki yapılandırma ayarları tarafından belirlenir. İzleme katılımcısı bir izleme profiline sorgular ekleyerek kayıtları izlemeye abone olur. Tüm izleme kayıtlarına abone olmak için, izleme profilinin \* her sorgu içindeki ad alanlarında "" kullanarak tüm izleme sorgularını belirtmesi gerekir.

Aşağıda, izleme profillerinin bazı yaygın örnekleri verilmiştir.

- İş akışı örneği kayıtlarını ve hatalarını almak için bir izleme profili.

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- Tüm özel izleme kayıtlarını elde etmek için bir izleme profili.

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [SQL İzleme](./samples/sql-tracking.md)
- [Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))
