---
title: Özellik yükseltme etkinliği
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 6e059a0d344e6c62833feaa890c459c141a49673
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747060"
---
# <a name="property-promotion-activity"></a>Özellik yükseltme etkinliği
Bu örnek sağlayan tümleşik bir uçtan uca çözüm <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> doğrudan yazma deneyimini iş akışı içinde yükseltme özelliği. Yapılandırma öğeleri, iş akışı etkinlikleri ve basitleştirin promosyon özelliğinin kullanımına iş akışı uzantıları koleksiyonu sağlanır. Ayrıca, bu koleksiyon kullanmayı gösteren basit bir iş akışı örneği içerir.  
  
> [!NOTE]
>  Örnekler yalnızca eğitim amaçlı olarak sağlanır. Bunlar, bir üretim ortamı için tasarlanmamıştır ve bir üretim ortamında test edilmemiştir. Microsoft, bu örnekler için teknik destek sağlamaz.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   Başlatılan bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Örnek Proje  
  
-   **PropertyPromotionActivity** proje yükseltme özgü yapılandırma öğeleri, iş akışı etkinlikleri ve iş akışı uzantıları ilişkin dosyaları içerir.  
  
-   **CounterServiceApplication** projesini içeren kullanan bir örnek iş akışı **SqlWorkflowInstanceStorePromotion** proje.  
  
-   Karşı çalıştırılmalıdır SQL betiği (PropertyPromotionActivitySQLSample.sql) <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı.  
  
-   İki bağlantı bir çözüm dosyası [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projeleri (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Ayarlama ve çalıştırma örneği  
  
1.  Bir iş akışı Kalıcılık veritabanı başlatın.  
  
    1.  Örnek dizine (\WF\Basic\Persistence\PropertyPromotionActivity) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
    2.  Yönetici ayrıcalıkları kullanılabilir durumda değilse, bir SQL Server oturumu oluşturun. SQL Server Management Studio'da Git **güvenlik**, **oturumları**. Sağ **oturumları** ve yeni bir oturum oluşturun. Açarak SQL role ACL Kullanıcınızı eklemek **veritabanları**, **InstanceStore**, **güvenlik**. Sağ **kullanıcılar** seçip **yeni kullanıcı**. Ayarlama **oturum açma adı** yukarıda oluşturulan kullanıcı. Kullanıcı için veritabanı rolü üyeliği System.Activities.DurableInstancing.InstanceStoreUsers (ve diğerleri) ekleyin. Kullanıcı zaten (örneğin, dbo kullanıcısı) bulunmayabilir unutmayın.  
  
2.  PropertyPromotionActivity.sln çözüm dosyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Yerel SQL Server Express yüklemesi dışında bir veritabanında örnek deposu oluşturduysanız, veritabanı bağlantı dizesini güncelleştirmeniz gerekir. App.config dosyasını altında alter **CounterServiceApplication** değerini ayarlayarak `connectionString` özniteliği `sqlWorkflowInstanceStorePromotion` düğümü başlatıldı Kalıcılık veritabanına işaret eden, adım 1.  
  
4.  Derleme ve çözümü çalıştırın. Bu sayaç WF hizmeti başlatın ve otomatik olarak bir iş akışı örneği başlatın.  
  
5.  Hızlı bir şekilde tüm satırları [dbo] seçin. (Bu görünüm 1. adımda CreateInstanceStore.cmd çalıştırarak eklendi) [counterService] görünümü Kalıcılık veritabanı. Ayarlama aşağıdakine benzer bir sonuç göreceksiniz:  
  
    |InstanceId|Ort|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Görünümü yenileniyor tutmak gibi her iki saniye Ort ve CounterValueLastUpdated değiştirme fark edeceksiniz. Bu sayaç kendisini güncelleştirir aralığıdır. Ort ve CounterValueLastUpdated bu iş akışı için yükseltilen özellikleri temsil eder.  
  
## <a name="to-remove-the-sample"></a>Örnek kaldırmak için  
  
-   RemoveInstanceStore.cmd örnek dizinde (\WF\Basic\Persistence\PropertyPromotionActivity) çalıştırın.  
  
## <a name="understanding-this-sample"></a>Bu örnek anlama  
 Örnek, iki proje dosyası ve SQL içerir:  
  
-   **CounterServiceApplication** basit bir sayaç WF hizmetini barındıran bir konsol uygulamasıdır. Bir tek yönlü mesaj aracılığıyla bağlı `Start` uç noktası, iş akışı sayısı 0'dan bir sayaç değişkeni her iki saniye artan 29 için. Her sayacı artırma sonra iş akışı devam ediyorsa ve yükseltilen özellikleri [dbo] güncelleştirilir. [CounterService] görüntüleyin. Konsol uygulamasını çalıştırdığınızda, WF hizmetini barındıran ve bir ileti gönderir `Start` uç noktası, bir sayaç WF örneği oluşturma.  
  
-   **PropertyPromotionActivity** yapılandırma öğeleri, iş akışı etkinlikleri ve iş akışı uzantıların bulunduğu bir sınıf kitaplığı, **CounterServiceApplication** kullanır.  
  
-   **PropertyPromotionActivitySQLSample.sql** oluşturur ve ekler görünümü [dbo]. [ Veritabanına counterService].  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>SqlWorkflowInstanceStorePromotion yapılandırma öğesini kullanarak  
 `SqlWorkflowInstanceStorePromotion` Yapılandırma öğesi devraldığı `SqlWorkflowInstanceStore` yapılandırma öğesi, ancak adlı bir ek yapılandırma öğesi ekler `promotionSets`. `promotionSets` Öğesi yapılandırması yükseltilen özelliklerinden belirtmesini sağlar. Bu örnek tarafından kullanılan yapılandırma dosyasıdır:  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 [Dbo] tanımını inceleyin. [CounterService] görüntüleyin.  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Bir iş akışı örneği devam ederse, bir satır içine eklenir `InstancePromotedProperties` görüntülemek için her `PromotionSet` yapılandırmasında tanımlanmış. Bu satır yükseltilen tüm özelliklerini içerir `PromotionSet` (bir yükseltilen özellik sütun başına). Bu `PromotionSet` tanımlama grubu tarafından Anahtarlanan: `InstanceId, PromotionName`. Bu örnekte, bir sahip olduğumuz `PromotionSet` olan adı özniteliği yapılandırmasında tanımlı `CounterService`. Not nasıl `PromotionName` öğesinin ad özniteliği için sütun değeri eşittir `PromotionSet` öğesi.  
  
 Sırasını `promotedValue` öğeleri karşılık gelen yükseltilen özelliklerinde yerleşimini ile `InstancePromotedProperties` görünümü. `Count` İlk `promotedValue` öğesi. Sonuç olarak, eşlenmiş `Value1` sütununda `InstancePromotedProperties` görünümü. `LastIncrementedAt` İkinci `promotedValue` öğesi. Sonuç olarak, eşlenmiş `Value2` sütununda `InstancePromotedProperties` görünümü.  
  
#### <a name="using-the-promotevalue-activity"></a>PromoteValue etkinliğini kullanma  
 Windows Workflow Foundation Designer CounterService.xamlx dosyasını inceleyin. WF tanımında iki özel etkinliği olduğuna dikkat edin: `PromoteValue<DateTime>` ve `PromoteValue<Int32>`.  
  
 `PromoteValue<Int32>` Etkinliğinde, `Name` üye olarak tanımlanan `Count`. Bu ilk eşleşen `promotedValue` yapılandırma öğesi ve kendi `Value` olarak tanımlanan `Counter` iş akışı değişkeni. İş akışı devam ederse, `Counter` iş akışı değişkeninin yükseltilen bir özellikte olarak kalıcıdır `Value1` sütununun `InstancePromotedProperties` görünümü.  
  
 `PromoteValue<DateTime>` Etkinliğinde, `Name` üye olarak tanımlanan `LastIncrementedAt`. Bu ikinci ile eşleşen `promotedValue` yapılandırma öğesi ve kendi `Value` olarak tanımlanan `TimeLastIncremented` iş akışı değişkeni. Bunun anlamı, değerini iş akışı devam ederse `TimeLastIncremented` iş akışı değişkeni kalıcı olarak yükseltilen bir özellikte `Value2` sütununun `InstancePromotedProperties` görünümü.  
  
 Unutmayın `PromotedValue` ayrıca etkinliğinde adlı bir Boolean üye `ClearExistingPromotedData`. Bu üye ayarlandığında `true`, bu iş akışında o noktaya kadar tüm yükseltilen özellik değerleri temizler. Örneğin, bir sıralama etkinliği olarak tanımlanması durumunda aşağıdaki gibidir:  
  
1.  PromoteValue {adı "Count", değer = 3 =}  
  
2.  PromoteValue {adı "LastIncrementedAt", değer = 1-1-2000 =}  
  
3.  Kalıcı  
  
4.  PromoteValue {adı "Count", değer = 4, ClearExistingPromotedData = true =}  
  
5.  Kalıcı  
  
 Yükseltilen değeri ikinci devam ettir üzerinde `Count` 4 olur. Ancak, yükseltilen değeri `LastIncrementedAt` olacaktır `NULL`. Varsa `ClearExistingPromotedData` ayarlanmadı `true` 4. adımda, ardından ikinci devam ettir sonra yükseltilen sayısı değeri 4 olur. Sonuç olarak, yükseltilen değeri `LastIncrementedAt` 1-1-2000 olmaya.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Bu sınıf kitaplığı kullanımını kolaylaştırmak için aşağıdaki genel sınıfları içeren <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> yükseltme özelliği.  
  
#### <a name="promotevalue-class"></a>PromoteValue sınıfı  
 Bu sınıf, bir özellik yükseltir. Yükseltilen özellik adını bir ad özniteliği eşleşmelidir bir `promotedValue` yapılandırma öğesi. Bu etkinlik iş akışı Tasarımcısı'nda kullanılabilir. CounterServiceApplication kullanım örneği için bkz.  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 ClearExistingPromotedData (Boole)  
 Bu etkinlik önce yükseltilen tüm değerleri temizler.  
  
 Adı (dize)  
 Bu özellik temsil eden adı. Bu ad özniteliği eşleşmelidir bir \<promotedValue > yapılandırma öğesi.  
  
 Değer (InArgument\<T >)  
 Değişken / Sütun saklamak istediğiniz değer.  
  
#### <a name="promotevalues-class"></a>PromoteValues sınıfı  
 Birden çok özellik yükseltir. Yükseltilen özellik adlarının tüm adı öznitelikler eşleşmelidir `promotedValue` yapılandırma öğeleri. Kullanım benzer `PromoteValue` aynı anda birden çok özellik yükseltilebilir olgu dışında bir etkinlik. Bu etkinlik iş akışı Tasarımcısı'nda kullanılamaz.  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a>SqlWorkflowInstanceStorePromotionBehavior  
 Öğesinden türetilen `SqlWorkflowInstanceStoreBehavior`. Bu türetilmiş sınıf özel Kalıcılık Katılımcısı (Ayrıca bu kitaplık bir parçası) bir iş akışı uzantısı ekler. Önceki iki iş akışı etkinlikleri uygulanması, bu özel Kalıcılık Katılımcısı kullanır.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Bu sınıf kitaplığını da içeren `ConfigurationElement` logrequest olayını `SqlWorkflowInstanceStorePromotionElement` ve önceki yükseltme etkinlikleri tarafından kullanılan özel Kalıcılık Katılımcısı.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Bu SQL dosyası oluşturur bir `[dbo].[CounterService]` ek olarak görüntülemek `[InstancePromotedProperties]` CounterService yükseltme kümesine sahip tüm örneklerini sorgulamak için görünümü.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
