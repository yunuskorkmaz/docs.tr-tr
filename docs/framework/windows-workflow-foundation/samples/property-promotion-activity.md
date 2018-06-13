---
title: Özelliği yükseltme etkinliği
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 46e74c8c479e545778db92e15de3cb8798dafa11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519931"
---
# <a name="property-promotion-activity"></a>Özelliği yükseltme etkinliği
Bu örnek tümleşen bir uçtan uca çözümü sağlar <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> yükseltme özelliğini doğrudan yazma deneyimini iş akışına. Yapılandırma öğeleri, iş akışı etkinlikleri ve yükseltme özelliğini kullanımını kolaylaştırmak iş akışı uzantıları koleksiyonu sağlanır. Ayrıca, bu koleksiyonu kullanımı gösterilmiştir basit bir iş akışı örneği içerir.  
  
> [!NOTE]
>  Örnekler yalnızca eğitim amaçlı olarak sağlanır. Bunlar, bir üretim ortamı için tasarlanmamıştır ve bir üretim ortamında test edilmemiştir. Microsoft, bu örnekler için teknik destek sağlamaz.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   Başlatılan bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Örnek Proje  
  
-   **PropertyPromotionActivity** proje yükseltme özel yapılandırma öğeleri, iş akışı etkinlikleri ve iş akışı uzantıları ilgili dosyaları içerir.  
  
-   **CounterServiceApplication** projeyi içeren kullanan bir örnek iş akışı **SqlWorkflowInstanceStorePromotion** projesi.  
  
-   Karşı çalıştırılmalıdır bir SQL betiği (PropertyPromotionActivitySQLSample.sql) <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı.  
  
-   İki bağlanan bir çözüm dosyasını [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projeleri (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Ayarlamak ve örneği çalıştırmak için  
  
1.  Bir iş akışı Kalıcılık veritabanını başlatılamadı.  
  
    1.  Örnek dizine (\WF\Basic\Persistence\PropertyPromotionActivity) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
    2.  Yönetici ayrıcalıkları kullanılabilir değilse, bir SQL Server oturumu oluşturun. SQL Server Management Studio'da Git **güvenlik**, **oturumları**. Sağ **oturumları** ve yeni bir oturum oluşturun. ACL kullanıcı açarak SQL role ekleyin **veritabanları**, **InstanceStore**, **güvenlik**. Sağ **kullanıcılar** seçip **yeni kullanıcı**. Ayarlama **oturum açma adı** yukarıda oluşturduğunuz kullanıcı. Veritabanı rolü üyeliği System.Activities.DurableInstancing.InstanceStoreUsers kullanıcıya (ve diğerleri) ekleyin. Kullanıcı zaten (örneğin, dbo kullanıcısı) bulunmayabilir unutmayın.  
  
2.  PropertyPromotionActivity.sln çözüm dosyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Yerel SQL Server Express yüklemesi dışında bir veritabanında örnek deposuna oluşturduysanız, veritabanı bağlantı dizesi güncelleştirmeniz gerekir. App.config dosyasını alter **CounterServiceApplication** değerini ayarlayarak `connectionString` özniteliği `sqlWorkflowInstanceStorePromotion` düğümü başlatıldı Kalıcılık veritabanına işaret eden, adım 1.  
  
4.  Derleme ve çözümü çalıştırın. Bu sayaç WF hizmetini başlatın ve bir iş akışı örneği otomatik olarak başlat.  
  
5.  Hızlı bir şekilde tüm satırları [dbo] seçin. (Bu görünüm 1. adımda CreateInstanceStore.cmd çalıştırarak eklendi) [counterService] görünümü Kalıcılık veritabanınızdaki. Bir sonuç kümesi aşağıdakine benzer görürsünüz:  
  
    |örnek kimliği|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Görünümü yenileme tutmak gibi CounterValue ve CounterValueLastUpdated her iki saniye değiştirme fark edeceksiniz. Bu sayaç kendisini güncelleştirir aralığıdır. CounterValue ve CounterValueLastUpdated bu iş akışı için yükseltilen özellikleri temsil eder.  
  
## <a name="to-remove-the-sample"></a>Örnek kaldırmak için  
  
-   RemoveInstanceStore.cmd örnek dizininde (\WF\Basic\Persistence\PropertyPromotionActivity) çalıştırın.  
  
## <a name="understanding-this-sample"></a>Bu örnek anlama  
 Örnek bir SQL dosyasını ve iki proje içerir:  
  
-   **CounterServiceApplication** basit bir sayaç WF hizmeti barındıran bir konsol uygulamasıdır. Üzerinden tek yönlü bir ileti alır almaz `Start` uç noktası, iş akışı sayısı 0'dan her iki saniyede bir sayaç değişkeni artırma 29 için. Her sayacı artırma sonra iş akışı devam ederse ve yükseltilen özellikleri [dbo] güncelleştirilir. [CounterService] görüntüleyin. Konsol uygulamasını çalıştırdığınızda, WF hizmetini barındıran ve bir ileti gönderir `Start` uç noktası, bir sayaç WF örneği oluşturma.  
  
-   **PropertyPromotionActivity** yapılandırma öğeleri, iş akışı etkinlikleri ve iş akışı uzantıları içeren bir sınıf kitaplığı, **CounterServiceApplication** kullanır.  
  
-   **PropertyPromotionActivitySQLSample.sql** oluşturur ve görünüm [dbo] ekler. [ Veritabanına counterService].  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>SqlWorkflowInstanceStorePromotion yapılandırma öğesi kullanma  
 `SqlWorkflowInstanceStorePromotion` Yapılandırma öğesi devraldığı `SqlWorkflowInstanceStore` yapılandırma öğesi, ancak adlı bir ek yapılandırma öğesi ekler `promotionSets`. `promotionSets` Öğesi yükseltilen özellikleri yapılandırma yoluyla belirtmesini sağlar. Bu örnek tarafından kullanılan yapılandırma dosyası.  
  
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
  
 [Dbo] tanımı inceleyin. [CounterService] görüntüleyin.  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Bir iş akışı örneği devam ediyorsa, bir satır eklenir `InstancePromotedProperties` görüntülemek için her `PromotionSet` yapılandırmasında tanımlanmış. Bu satır yükseltilen tüm özelliklerini içerir `PromotionSet` (bir yükseltilmiş özelliği sütun başına). Bu `PromotionSet` tanımlama grubu tarafından Anahtarlanan: `InstanceId, PromotionName`. Bu örnekte, biri sahibiz `PromotionSet` , adı özniteliği yapılandırmasında tanımlı `CounterService`. Not nasıl `PromotionName` sütun değeri için name özniteliği eşittir `PromotionSet` öğesi.  
  
 Sırasını `promotedValue` öğeleri karşılık gelen yükseltilen özelliklerinde yerleştirme `InstancePromotedProperties` görünümü. `Count` İlk `promotedValue` öğesi. Sonuç olarak, bu eşlenmiş `Value1` sütununda `InstancePromotedProperties` görünümü. `LastIncrementedAt` İkinci `promotedValue` öğesi. Sonuç olarak, bu eşlenmiş `Value2` sütununda `InstancePromotedProperties` görünümü.  
  
#### <a name="using-the-promotevalue-activity"></a>PromoteValue etkinliğini kullanma  
 Windows Workflow Foundation Tasarımcısı'nda CounterService.xamlx dosyasını inceleyin. WF tanımında iki özel etkinlikler olduğuna dikkat edin: `PromoteValue<DateTime>` ve `PromoteValue<Int32>`.  
  
 `PromoteValue<Int32>` Etkinlik sahip kendi `Name` üye olarak tanımlanan `Count`. Bu ilk eşleşen `promotedValue` yapılandırma öğesi ve kendi `Value` olarak tanımlanan `Counter` iş akışı değişkeni. İş akışı devam ederse, `Counter` yükseltilen bir özellik olarak iş akışı değişken kalıcı `Value1` sütunu `InstancePromotedProperties` görünümü.  
  
 `PromoteValue<DateTime>` Etkinlik sahip kendi `Name` üye olarak tanımlanan `LastIncrementedAt`. Bu ikinci ile eşleşen `promotedValue` yapılandırma öğesi ve kendi `Value` olarak tanımlanan `TimeLastIncremented` iş akışı değişkeni. İş akışı devam ederse, değeri buna `TimeLastIncremented` iş akışı değişken kalıcı hale yükseltilen bir özellik olarak `Value2` sütunu `InstancePromotedProperties` görünümü.  
  
 Unutmayın `PromotedValue` etkinlik ayrıca adlı bir Boolean üyeye sahip `ClearExistingPromotedData`. Bu üye ayarlandığında `true`, bu iş akışı bu noktaya kadar tüm yükseltilen özellik değerlerini temizler. Sıralı etkinlik olarak tanımlanır, örneğin, aşağıdaki gibidir:  
  
1.  PromoteValue {adı "Count", değer = 3 =}  
  
2.  PromoteValue {adı "LastIncrementedAt", değer = 1-1-2000 =}  
  
3.  Sürdür  
  
4.  PromoteValue {adı "Count", değer = 4, ClearExistingPromotedData = = true}  
  
5.  Sürdür  
  
 Yükseltilen değeri ikinci devam ettir üzerinde `Count` 4 olacaktır. Ancak, yükseltilen değeri `LastIncrementedAt` olacaktır `NULL`. Varsa `ClearExistingPromotedData` ayarlanmadı `true` 4. adımda, ardından ikinci devam ettir sonra yükseltilen değeri sayısı için 4 olacaktır. Sonuç olarak, yükseltilen değeri `LastIncrementedAt` 1-1-2000 hala olacaktır.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Bu sınıf kitaplığı kullanımını kolaylaştırmak için şu ortak sınıfları içerir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> yükseltme özelliği.  
  
#### <a name="promotevalue-class"></a>PromoteValue sınıfı  
 Bu sınıf, bir özellik yükseltir. Yükseltilen özellik adı bir ad özniteliği eşleşmelidir bir `promotedValue` yapılandırma öğesi. Bu etkinliği iş akışı Tasarımcısı'nda kullanılabilir. Kullanım örneği CounterServiceApplication bakın.  
  
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
 Bu etkinlik önce yükseltilmiş tüm değerleri temizler.  
  
 adı (dize)  
 Bu özellik temsil eden adı. Bu ad özniteliği eşleşmelidir bir \<promotedValue > yapılandırma öğesi.  
  
 Değer (InArgument\<T >)  
 Değişken / sütunda depolamak istediğiniz değer.  
  
#### <a name="promotevalues-class"></a>PromoteValues sınıfı  
 Birden çok özelliklerini yükseltir. Yükseltilen özellik adlarını tüm adı öznitelikleri eşleşmelidir `promotedValue` yapılandırma öğeleri. Kullanım benzer `PromoteValue` etkinlik, aynı anda birden çok özellikler yükseltilebilir olgu dışında. Bu etkinliği iş akışı Tasarımcısı'nda kullanılamaz.  
  
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
 Türetilen `SqlWorkflowInstanceStoreBehavior`. Bu türetilmiş sınıf özel Kalıcılık katılımcı (aynı zamanda bu kitaplığı parçası) bir iş akışı uzantısı olarak ekler. Önceki iki iş akışı etkinlikleri uyarlamasını bu özel Kalıcılık katılımcı kullanır.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Bu sınıf kitaplığı da içeren `ConfigurationElement` uygulanması için `SqlWorkflowInstanceStorePromotionElement` ve önceki yükseltme etkinlikler tarafından kullanılan özel Kalıcılık katılımcı.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Bu SQL dosyası oluşturur bir `[dbo].[CounterService]` ek olarak görüntülemek `[InstancePromotedProperties]` CounterService yükseltme kümesine sahip tüm örneklerini sorgulamak için görünümü.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
