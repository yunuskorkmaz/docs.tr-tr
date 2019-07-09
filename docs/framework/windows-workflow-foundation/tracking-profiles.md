---
title: İzleme Profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: a643cf37bbb3e72baefb434249aa54b386060627
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660924"
---
# <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri bir iş akışı örneğinin durumunu çalışma zamanında değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.

## <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, bir iş akışı örneği için izleme bilgileri yayıldığını belirtmek için kullanılır. Ardından profil belirtilmezse, tüm izleme olaylar gönderilir. Bir profili belirtilirse, profilde belirtilen izleme olaylarını yayılan. Çok genel bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur. Buna karşılık, elde edilen ayarlanmış olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin bir çok ayrıntılı profili oluşturabilirsiniz.

İzleme profilleri, bir standart .NET Framework yapılandırma dosyası içinde XML öğeleri olarak kendilerini bildirim veya kodda belirtilen. Aşağıdaki örnek, bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] abone olmak izleme katılımcı izin veren bir yapılandırma dosyası profilinde izleme `Started` ve `Completed` iş akışı olayları.

```xml
<system.serviceModel>
    ...
    <tracking>
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

Aşağıdaki örnek kod kullanılarak oluşturulan profil izleme eşdeğer gösterir.

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

İzleme kayıtları filtre uygulanır aracılığıyla bir izleme profili içinde görünürlük modunu kullanarak <xref:System.Activities.Tracking.ImplementationVisibility> özniteliği. Bileşik bir etkinlik uygulaması oluşturan diğer etkinlikler içeren üst düzey bir etkinliktir. Uygulama oluşturan etkinlikler izlenen varsa belirtmek için bir iş akışı etkinlik içinde bileşik etkinliklerden yayılan izleme kayıtları görünürlük modunu belirtir. İzleme sırasında görünürlük modunu geçerli profil düzeyi. Bir iş akışındaki etkinliklere tek tek kayıtları izleme filtreleme, sorguları izleme profilinde tarafından denetlenir. Daha fazla bilgi için **izleme profili sorgu türleri** bu belgenin bölüm.

Belirtilen iki görünürlük modları `implementationVisibility` izleme profilinde özniteliğinin `RootScope` ve `All`. Kullanarak `RootScope` modu, bileşik bir etkinlik olduğu bir iş akışının kök durumda bir etkinlik uygulaması oluşturan etkinlikler için izleme kayıtları bastırır. Bir iş akışı için diğer etkinlikleri kullanılarak uygulanan bir etkinlik eklendiğinde bu, gelir ve `implementationVisibility` için RootScope ayarlayın, yalnızca üst düzey faaliyet, bileşik bir etkinlik içinde takip edilir. Bir etkinlik iş akışı köküdür. sonra iş akışı uygulamasıdır etkinliğin kendisi ve kayıtları izleme uygulaması oluşturan etkinlikler için gönderilir. Tüm modu kullanılarak, tüm izleme kayıtları için Kök etkinlik yayılan ve tüm bileşik etkinlikleri izin verir.

Örneğin, varsayalım *MyActivity* uygulaması içeren iki etkinlik, bileşik bir etkinlik *Activity1* ve *Activity2*. Ne zaman bu etkinlik bir iş akışına eklenir ve izleme bir izleme profili ile etkinleştirilmiş `implementationVisibility` kümesine `RootScope`, izleme kayıtları yayılan yalnızca *MyActivity*. Ancak, etkinlikler için hiçbir kayıtları yayılan *Activity1* ve *Activity2*.

Ancak, varsa `implementationVisibility` izleme profili kümesine özniteliği `All`, yalnızca için izleme kayıtları yayılan sonra *MyActivity*, ancak etkinlikler için de *Activity1* ve  *Activity2*.

`implementationVisibility` Bayrağı takip izleme kayıt türleri için geçerlidir:

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> Etkinlik uygulamasından yayılan CustomTrackingRecords implementationVisibility ayarı tarafından filtrelenir değil.

`implementationVisibility` İşlevi olarak belirtilen <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> izlemeyi kodda gibi profil:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

`implementationVisibility` İşlevi olarak belirtilen <xref:System.Activities.Tracking.ImplementationVisibility.All> izleme profili bir yapılandırma dosyasında aşağıdaki gibi:

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

`ImplementationVisibility` İzleme profili ayarı, isteğe bağlıdır. Varsayılan olarak, değeri ayarlamak `RootScope`. Bu öznitelik değerlerini ayrıca büyük/küçük harf duyarlıdır.

### <a name="tracking-profile-query-types"></a>İzleme profili sorgu türleri

İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgulamaya izin kayıtları izleme için bildirim abonelikleri olarak yapılandırılmıştır. Birkaç farklı sınıfları için abone izin sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri. İzleme profilleri yapılandırmasında veya kod aracılığıyla belirtilebilir. En sık kullanılan sorgu türleri şunlardır:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery> -Daha önce gösterildiği gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek için bunu kullanın `Started` ve `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  İçin abone durumları belirtilen <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfı.

  Yapılandırma veya iş akışı örnek düzeyi kayıtları için izleme abone olmak için kullanılan kod `Started` durumu örneği kullanarak <xref:System.Activities.Tracking.WorkflowInstanceQuery> aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.ActivityStateQuery> -Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için bunu kullanın. Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz. Bu sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityStateRecord> nesneleri. Abone olmak için kullanılabilir durumları belirtilen <xref:System.Activities.Tracking.ActivityStates>.

  Yapılandırma ve kullanma etkinlik durumu izleme kayıtları abone olmak için kullanılan kod <xref:System.Activities.Tracking.ActivityStateQuery> için `SendEmailActivity` etkinlik, aşağıdaki örnekte gösterilmiştir.

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
  > Birden çok activityStateQuery öğeleri aynı ada sahipse, yalnızca son öğesinde durumları izleme profili kullanılır.

- <xref:System.Activities.Tracking.ActivityScheduledQuery> -Bu sorgu yürütme için zamanlanan bir etkinlik üst etkinliği tarafından izlemenize olanak tanır. Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityScheduledRecord> nesneleri.

  Kayıtları abone olmak için kullanılan kod ve yapılandırmayı ilgili `SendEmailActivity` alt etkinlik kullanarak zamanlanmasını <xref:System.Activities.Tracking.ActivityScheduledQuery> aşağıdaki örnekte gösterilen.

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

- <xref:System.Activities.Tracking.FaultPropagationQuery> -Bir etkinlik içinde oluşan hataların işlenmesi izlemek için bunu kullanın. Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.FaultPropagationRecord> nesneleri.

  Kayıtları abone olmak için kullanılan kod ve yapılandırmayı ilgili hata yayma kullanarak <xref:System.Activities.Tracking.FaultPropagationQuery> aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.CancelRequestedQuery> -Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için bunu kullanın. Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CancelRequestedRecord> nesneleri.

  Kayıtları abone olmak için kullanılan kod ve yapılandırmayı ilgili etkinlik iptal kullanarak <xref:System.Activities.Tracking.CancelRequestedQuery> aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.CustomTrackingQuery> -Kod etkinlikleriniz tanımlayan olayları izlemek için bunu kullanın. Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri.

  Kayıtları abone olmak için kullanılan kod ve yapılandırmayı kullanarak özel izleme kayıtları için ilgili <xref:System.Activities.Tracking.CustomTrackingQuery> aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.BookmarkResumptionQuery> -İş akışı örneği içinde yer işaretinin sürdürme izlemek için bunu kullanın. Bu sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.BookmarkResumptionRecord> nesneleri.

  İlgili kayıtlara abone olmak için kullanılan kod ve yapılandırmayı sürdürme yer işareti kullanarak <xref:System.Activities.Tracking.BookmarkResumptionQuery> aşağıdaki örnekte gösterilmiştir.

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

Ek açıklamaları, rasgele yapı saatinden yapılandırılabilir bir değerle kayıtları izleme etiket izin verir. Örneğin, "Posta sunucusu ile" etiketlemek için birkaç iş akışları arasında birkaç izleme kayıtları isteyebilirsiniz "Posta Sunucu1" ==. Bu etikete sahip tüm kayıtları izleme kayıtları daha sonra sorgulanırken bulma kolaylaştırır.

Bunu gerçekleştirmek için bir ek açıklama bir izleme sorguya aşağıdaki örnekte gösterildiği gibi eklenir.

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

### <a name="how-to-create-a-tracking-profile"></a>Bir izleme profili oluşturma

Sorgu öğeleri izleme bir izleme profili kullanarak bir XML yapılandırma dosyasını oluşturmak için kullanılan veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kod. Bir yapılandırma dosyası kullanılarak oluşturulan bir izleme profili bir örneği aşağıda verilmiştir.

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
> İş akışı hizmeti konağı kullanarak WF izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur. İzleme profili kullanarak ve sorgu API'si izleme kodu ile bir izleme profili oluşturmak mümkündür.

Bir XML yapılandırma dosyası olarak yapılandırılan bir profili bir davranış uzantısı kullanarak bir izleme katılımcı uygulanır. Bu sonraki bölümde açıklandığı gibi bir WorkflowServiceHost eklenir [yapılandırma izleme için bir iş akışı](configuring-tracking-for-a-workflow.md).

Ayrıntı düzeyini ana bilgisayar tarafından yayılan izleme kayıtları izleme profili yapılandırma ayarlarında belirlenir. İzleme katılımcı, sorgular için bir izleme profili ekleyerek kayıtları izleme için abone olur. Tüm izleme kayıtları abone olmak izleme profili kullanarak tüm izleme sorguları belirtilmesi gerekiyor "\*" her bir sorgu ad alanları.

İzleme profilleri, sık karşılaşılan örneklerden bazıları aşağıda verilmiştir.

- İş akışı örneği kayıtlarını ve hataları elde etmek için bir izleme profili.

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

- Tüm özel izleme kayıtları almak için bir izleme profili.

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
- [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
