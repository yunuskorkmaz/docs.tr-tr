---
title: Profillerini izleme
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 4f70964ea7e2456f82aeac4bfb9aedfdb239d58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519990"
---
# <a name="tracking-profiles"></a>Profillerini izleme
İzleme profilleri çalışma zamanında bir iş akışı örneğinin durumu değiştiğinde, gösterilen iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.  
  
## <a name="tracking-profiles"></a>Profillerini izleme  
 İzleme profilleri hangi izleme bilgileri için bir iş akışı örneği gösterilen belirtmek için kullanılır. Profil yok belirtilmişse, tüm izleme olaylarını yayılan. Bir profili belirtilirse, profilinde belirtilen izleme olaylarını yayılan. İzleme gereksinimlerinize bağlı olarak çok genel bir profili yazabilir, üst düzey durum değişiklikleri bir iş akışında, küçük bir kümesini için abone olur. Buna karşılık, sonuçta ortaya çıkan, olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin çok ayrıntılı bir profil oluşturabilirsiniz.  
  
 İzleme profili XML öğeleri içinde bir standart olarak kendilerini bildirim [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma dosyası veya belirtilen kod. Aşağıdaki örnek sahip bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] abone olmak izleme katılımcı izin veren bir yapılandırma dosyası profilinde izleme `Started` ve `Completed` iş akışı olayları.  
  
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
  
 Aşağıdaki örnek kod kullanılarak oluşturulan profili izleme eşdeğer gösterir.  
  
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
  
 İzleme kayıtları izleme profilindeki görünürlük modunu aracılığıyla kullanılarak filtrelenir <xref:System.Activities.Tracking.ImplementationVisibility> özniteliği. Bileşik etkinlik uygulaması form diğer etkinlikler içeren üst düzey bir etkinliktir. Uygulama form etkinlikleri izlenen olmadığını belirtmek için bir iş akışı aktivitesi içinde bileşik etkinliklerden yayılan izleme kayıtları görünürlük modunu belirtir.  İzleme sırasında görünürlük modunu uygular profil düzeyi. Bir iş akışındaki etkinliklere tek tek kayıtları izleme filtreleme izleme profili sorgulara tarafından denetlenir. Daha fazla bilgi için bkz: **izleme profili sorgu türleri** bu belgede bölüm.  
  
 Belirtilen iki görünürlük modları `implementationVisibility` özniteliğinin izleme profilinde `RootScope` ve `All`. Kullanarak `RootScope` modu bileşik bir etkinlik olduğu bir iş akışının kök durumda bir etkinlik uyarlamasını form etkinlikler için izleme kayıtları gizler.  Diğer etkinlikler kullanılarak uygulanan bir etkinlik bir iş akışına eklendiğinde bu, gelir ve `implementationVisibility` RootScope için ayarlanırsa, bu bileşik etkinlik içinde yalnızca üst düzey etkinlik izlenir. Bir etkinlik iş akışı köküdür. ardından etkinliği iş akışı uygulamasıdır kendisi ve kayıtları izleme uygulaması form etkinlikler için gösterilen. Tüm modunu kullanan tüm izleme kayıtları için Kök etkinlik yayınlaması ve tüm bileşik etkinliklerini izin verir.  
  
 Örneğin, varsayalım *MyActivity* olan uygulaması içeren iki etkinlik, bileşik bir etkinliği *Activity1* ve *Activity2*.  Ne zaman bu etkinlik bir iş akışına eklenir ve izleme sahip bir izleme profili etkinleştirilmiş `implementationVisibility` kümesine `RootScope`, izleme kayıtları yalnızca yayılan *MyActivity*.  Ancak, hiçbir kayıt etkinlikler için gösterilen *Activity1* ve *Activity2*.  
  
 Ancak, varsa `implementationVisisbility` izleme profili kümesine özniteliğinin `All`, izleme kayıtları yalnızca için gösterilen sonra *MyActivity*, ancak etkinlikler için de *Activity1* ve  *Activity2*.  
  
 `implementationVisibility` Bayrağı uygulanır şu izleme kayıt türlerini için:  
  
-   ActivityStateRecord  
  
-   FaultPropagationRecord  
  
-   CancelRequestedRecord  
  
-   ActivityScheduledRecord  
  
> [!NOTE]
>  Etkinlik uygulamasından yayılan CustomTrackingRecords implementationVisibility ayarıyla filtrelendi değil.  
  
 `implementationVisibility` İşlevselliği olarak belirtildiğinde <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> izlemeyi kodunun profilini oluşturma gibi:  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 `implementationVisibility` İşlevselliği olarak belirtildiğinde <xref:System.Activities.Tracking.ImplementationVisibility.All> izleme profili, yapılandırma dosyasında aşağıdaki gibi:  
  
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
  
 `ImplementationVisibility` İzleme profilindeki ayardır isteğe bağlıdır. Varsayılan olarak, değerini ayarlamak `RootScope`. Bu öznitelik değerlerini da büyük/küçük harf duyarlıdır.  
  
### <a name="tracking-profile-query-types"></a>İzleme profili sorgu türleri  
 İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgu izin kayıtları izleme için bildirim temelli abonelikler olarak yapılandırılmıştır. Farklı sınıflardaki abone izin birkaç sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri. Profilleri izleme yapılandırmasında veya kod aracılığıyla belirtilebilir. En yaygın sorgu türleri şunlardır:  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceQuery> -Daha önce gösterildiği gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek için bunu kullanın `Started` ve `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     İçin abone durumları belirtilen <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfı.  
  
     Yapılandırma veya iş akışı örneği düzeyi kayıtları için izleme abone olmak için kullanılan kod `Started` durumu örneğini kullanarak <xref:System.Activities.Tracking.WorkflowInstanceQuery> aşağıdaki örnekte gösterilen.  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.ActivityStateQuery> -Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için bunu kullanın. Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz. Bu sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityStateRecord> nesneleri. Abone olmak için kullanılabilir durumları belirtilen <xref:System.Activities.Tracking.ActivityStates>.  
  
     Yapılandırma ve kullanma etkinlik durumu izleme kayıtları abone olmak için kullanılan kod <xref:System.Activities.Tracking.ActivityStateQuery> için `SendEmailActivity` etkinlik, aşağıdaki örnekte gösterilir.  
  
    ```xml  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
    ```  
  
    ```  
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
    >  Birden çok activityStateQuery öğeleri aynı ada sahipse, yalnızca son öğesinde durumları izleme profili kullanılır.  
  
-   <xref:System.Activities.Tracking.ActivityScheduledQuery> -Bu sorgu, çalıştırılmak üzere zamanlanmış bir etkinlik üst etkinliği tarafından izlemenize olanak sağlar. Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityScheduledRecord> nesneleri.  
  
     Kayıtlara abone olmak için kullanılan kod ve yapılandırma ile ilgili `SendEmailActivity` alt etkinlik kullanarak zamanlanma <xref:System.Activities.Tracking.ActivityScheduledQuery> aşağıdaki örnekte gösterilen.  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.FaultPropagationQuery> -İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bunu kullanın. Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.FaultPropagationRecord> nesneleri.  
  
     Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili yayma hataya kullanmaya <xref:System.Activities.Tracking.FaultPropagationQuery> aşağıdaki örnekte gösterilir.  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.CancelRequestedQuery> -Alt etkinliği üst etkinlik tarafından iptal etme istekleri izlemek için bunu kullanın. Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CancelRequestedRecord> nesneleri.  
  
     Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili iptal etkinlik kullanmaya <xref:System.Activities.Tracking.CancelRequestedQuery> aşağıdaki örnekte gösterilir.  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.CustomTrackingQuery> -Kod etkinliklerinizi tanımladığınız olaylarını izlemek için bunu kullanın. Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri.  
  
     Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili kullanarak özel izleme kayıtları <xref:System.Activities.Tracking.CustomTrackingQuery> aşağıdaki örnekte gösterilir.  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.BookmarkResumptionQuery> -Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için bunu kullanın. Bu sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.BookmarkResumptionRecord> nesneleri.  
  
     Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili sürdürme yer işareti kullanmaya <xref:System.Activities.Tracking.BookmarkResumptionQuery> aşağıdaki örnekte gösterilir.  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
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
 Ek açıklamalar, rasgele yapı zamanından sonra yapılandırılmış bir değerle kayıtları izleme etiketi izin verir. Örneğin, "Posta sunucusuyla" etiketli için çeşitli iş akışları arasında birkaç izleme kayıtları istiyor olabilirsiniz "Posta Sunucu1" ==. Bu izleme kayıtları daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.  
  
 Bunu başarmak için ek açıklamanın izleme sorguda aşağıdaki örnekte gösterildiği gibi eklenir.  
  
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
  
### <a name="how-to-create-a-tracking-profile"></a>İzleme profili oluşturma  
 İzleme sorgu öğeleri bir XML yapılandırma dosyası kullanarak bir izleme profili oluşturmak için kullanılan veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu.  Bir yapılandırma dosyası kullanılarak oluşturulan bir izleme profili bir örneği burada verilmiştir.  
  
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
>  İş akışı hizmeti ana bilgisayarı kullanarak WF izleme profili genellikle bir yapılandırma dosyası kullanarak oluşturulur. İzleme profili kullanarak ve sorgu API izleme koduyla bir izleme profili oluşturmak mümkündür.  
  
 XML yapılandırma dosyası olarak yapılandırılmış bir profil bir davranış uzantısı kullanılarak izleme Katılımcısı uygulanır. Bu sonraki bölümde açıklandığı gibi bir WorkflowServiceHost eklenir [yapılandırma izleme iş akışı için](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 Ana bilgisayar tarafından gösterilen izleme kayıtları ayrıntı izleme profilindeki yapılandırma ayarları tarafından belirlenir. İzleme katılımcı bir izleme profili sorguları ekleyerek kayıtları izleme için abone olur. Tüm izleme kayıtları abone olmak için izleme profili kullanarak tüm izleme sorguları belirtilmesi gerekiyor "*" ad alanlarında her sorgular.  
  
 Profilleri izleme ortak örnekleri bazıları aşağıda verilmiştir.  
  
-   İş akışı örneği kayıtlarını ve hataları elde etmek için bir izleme profili.  
  
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
  
1.  Tüm özel izleme kayıtları almak için bir izleme profili.  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL İzleme](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
