---
title: Veritabanı erişimi etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: e9c7627738d3c5313a4f3e6e4451daf78b87839a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="database-access-activities"></a>Veritabanı erişimi etkinlikleri
Veritabanı erişimi etkinliklerini, bir iş akışındaki bir veritabanına erişmek izin verir. Bu etkinliklerin almak veya bilgileri değiştirin ve kullanmak için veritabanlarına erişim ver [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) veritabanına erişmek için.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse (indirme) gidin tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a>Veritabanı etkinlikleri  
 Aşağıdaki bölümlerde bu örnekte dahil etkinliklerin listesini ayrıntılı olarak açıklanmaktadır.  
  
## <a name="dbupdate"></a>DbUpdate  
 (Ekleme, güncelleştirme, silme ve diğer tüm değişiklikleri) veritabanında değişiklik üreten bir SQL sorgusunu çalıştırır.  
  
 Bu sınıf, iş zaman uyumsuz olarak gerçekleştirir (öğesinden türetilen <xref:System.Activities.AsyncCodeActivity> ve zaman uyumsuz yeteneklerini kullanır).  
  
 Bağlantı bilgilerini sağlayıcı sabit adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasından.  
  
 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreleri üzerinden geçirilir `Parameters` koleksiyonu.  
  
 Sonra `DbUpdate` olan yürütülen, etkilenen kayıtların sayısı döndürülür `AffectedRecords` özelliği.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
|Bağımsız Değişken|Açıklama|  
|-|-|  
|ProviderName|ADO.NET sağlayıcı sabit adı. Bu değişken ayarlanmışsa, sonra `ConnectionString` de ayarlamanız gerekir.|  
|connectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|  
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|  
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|  
|SQL|Çalıştırılacak SQL komutu.|  
|Parametreler|SQL sorgu parametreleri topluluğu.|  
|AffectedRecords|Son işlem tarafından etkilenen kayıtların sayısı.|  
  
## <a name="dbqueryscalar"></a>DbQueryScalar  
 Veritabanından tek bir değer alır bir sorgu yürütür.  
  
 Bu sınıf, iş zaman uyumsuz olarak gerçekleştirir (öğesinden türetilen <xref:System.Activities.AsyncCodeActivity%601> ve zaman uyumsuz yeteneklerini kullanır).  
  
 Bağlantı bilgilerini sağlayıcı sabit adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasından.  
  
 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreleri üzerinden geçirilir `Parameters` koleksiyonu.  
  
 Sonra `DbQueryScalar` olan yürütülen, skaler döndürülür `Result``out` bağımsız değişkeni (tür `TResult`, diğer bir deyişle taban sınıf içinde tanımlanan <xref:System.Activities.AsyncCodeActivity%601>).  
  
```  
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|Bağımsız Değişken|Açıklama|  
|-|-|  
|ProviderName|ADO.NET sağlayıcı sabit adı. Bu değişken ayarlanmışsa, sonra `ConnectionString` de ayarlamanız gerekir.|  
|connectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|  
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|  
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|  
|SQL|Çalıştırılacak SQL komutu.|  
|Parametreler|SQL sorgu parametreleri topluluğu.|  
|Sonuç|Sorgu yürütüldükten sonra elde edilen sayılabilir. Bu bağımsız değişken türü ise `TResult`.|  
  
## <a name="dbquery"></a>DbQuery  
 Nesnelerin bir listesini alır. bir sorgu yürütür. Bir eşleme işlev sorgu yürütüldükten sonra yürütülür (Bu olabilir <xref:System.Func%601> < `DbDataReader`, `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Bu eşleme işlev kayıt alır bir `DbDataReader` ve döndürülecek nesnesine eşler.  
  
 Bağlantı bilgilerini sağlayıcı sabit adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasından.  
  
 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreleri üzerinden geçirilir `Parameters` koleksiyonu.  
  
 SQL sorgusu sonuçlarını kullanarak alınır bir `DbDataReader`. Etkinlik dolaşır `DbDataReader` ve satırları eşler `DbDataReader` örneğine `TResult`. Kullanıcıyı `DbQuery` eşleme kodu ve bunu iki şekilde yapılır sağlaması gereken: kullanarak bir <xref:System.Func%601> < `DbDataReader`, `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. İlk durumda eşleme tek bir yürütme pulse içinde yapılır. Bu nedenle, daha hızlı olur, ancak bu XAML için seri hale getirilemez. En son durumda eşleme birden çok darbelerin gerçekleştirilir. Bu nedenle, bu daha yavaş olabilir ancak için XAML sıralanabilir ve bildirimli olarak yazılan (herhangi bir varolan etkinliği eşlemesinde katılabilir).  
  
```  
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [OverloadGroup("DirectMapping")]  
    [DefaultValue(null)]  
    public Func<DbDataReader, TResult> Mapper { get; set; }  
  
    [OverloadGroup("MultiplePulseMapping")]  
    [DefaultValue(null)]  
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }  
}  
```  
  
|Bağımsız Değişken|Açıklama|  
|-|-|  
|ProviderName|ADO.NET sağlayıcı sabit adı. Bu değişken ayarlanmışsa, sonra `ConnectionString` de ayarlamanız gerekir.|  
|connectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|  
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|  
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|  
|SQL|Çalıştırılacak SQL komutu.|  
|Parametreler|SQL sorgu parametreleri topluluğu.|  
|Eşleyici|İşlev eşleme (<xref:System.Func%601><`DbDataReader`, `TResult`>) bir kayıt alan `DataReader` sorgu yürütülürken zaman alınabilir ve türünde bir nesne örneğini döndürür `TResult` eklemekiçin`Result` koleksiyonu.<br /><br /> Bu durumda, eşleme tek bir yürütme pulse içinde yapılır, ancak bildirimli olarak Tasarımcısı'nı kullanarak yazılmayı olamaz.|  
|MapperFunc|İşlev eşleme (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) bir kayıt alan `DataReader` sorgu yürütülürken zaman alınabilir ve türünde bir nesne örneğini döndürür `TResult` eklemekiçin`Result` koleksiyonu.<br /><br /> Bu durumda, eşleme yürütme birden çok darbelerin yapılır. Bu işlev için XAML sıralanabilir ve bildirimli olarak yazılan (herhangi bir varolan etkinliği eşlemesinde katılabilir).|  
|Sonuç|Nesnelerinin listesi elde sorgu yürütülürken ve her kayıt için eşleme işlev yürütülürken zaman `DataReader`.|  
  
## <a name="dbquerydataset"></a>DbQueryDataSet  
 Döndüren bir sorgu yürüten bir <xref:System.Data.DataSet>. Bu sınıf, iş zaman uyumsuz olarak gerçekleştirir. Öğesinden türetilen <xref:System.Activities.AsyncCodeActivity> < `TResult`> ve zaman uyumsuz yeteneklerini kullanır.  
  
 Bağlantı bilgilerini sağlayıcı sabit adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasından.  
  
 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreleri üzerinden geçirilir `Parameters` koleksiyonu.  
  
 Sonra `DbQueryDataSet` yürütülür `DataSet` döndürülür `Result``out` bağımsız değişkeni (tür `TResult`, diğer bir deyişle taban sınıf içinde tanımlanan <xref:System.Activities.AsyncCodeActivity%601>).  
  
```  
public class DbQueryDataSet : AsyncCodeActivity<DataSet>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|Bağımsız Değişken|Açıklama|  
|-|-|  
|ProviderName|ADO.NET sağlayıcı sabit adı. Bu değişken ayarlanmışsa, sonra `ConnectionString` de ayarlamanız gerekir.|  
|connectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|  
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|  
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|  
|SQL|Çalıştırılacak SQL komutu.|  
|Parametreler|SQL sorgu parametreleri topluluğu.|  
|Sonuç|<xref:System.Data.DataSet> Sorgu yürütüldükten sonra elde edilir.|  
  
## <a name="configuring-connection-information"></a>Bağlantı bilgilerini yapılandırma  
 Tüm DbActivities aynı yapılandırma parametreleri paylaşır. İki şekilde yapılandırılabilir:  
  
-   `ConnectionString + InvariantName`: ADO.NET sağlayıcısı değişmez adını ve bağlantı dizesini ayarlayın.  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<DateTime>()  
    {  
        ProviderName = "System.Data.SqlClient",  
        ConnectionString = @"Data Source=.\SQLExpress;  
                             Initial Catalog=DbActivitiesSample;  
                             Integrated Security=True",  
        Sql = "SELECT GetDate()"  
    };  
    ```  
  
-   `ConfigName`: Bağlantı bilgilerini içeren yapılandırma bölümünün adını ayarlayın.  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   Etkinliğin:  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a>Bu örnek çalışıyor  
  
### <a name="setup-instructions"></a>Kurulum yönergeleri  
 Bu örnek bir veritabanı kullanır. Kurulum ve yükleme komut dosyası (Setup.cmd) örneği ile sağlanır. Komut istemini kullanarak bu dosyayı yürütmeniz gerekir.  
  
 Setup.cmd komut dosyası şunları SQL komutlarını içeren CreateDb.sql komut dosyasını çağırır:  
  
-   DbActivitiesSample adlı bir veritabanı oluşturur.  
  
-   Rolleri tablosu oluşturur.  
  
-   Çalışanlar bir tablo oluşturur.  
  
-   Üç kayıt rolleri tabloya ekler.  
  
-   On iki kayıtları çalışanların tabloya ekler.  
  
##### <a name="to-run-setupcmd"></a>Setup.cmd çalıştırmak için  
  
1.  Bir komut istemi açın.  
  
2.  DbActivities örnek klasöre gidin.  
  
3.  "Setup.cmd" yazın ve ENTER tuşuna basın.  
  
    > [!NOTE]
    >  Setup.cmd örnek yerel makine SqlExpress örneğinizi yüklemeyi dener. Diğer SQL server örneği yüklemek istiyorsanız, yeni örnek adıyla Setup.cmd düzenleyin.  
  
##### <a name="to-uninstall-the-sample-database"></a>Örnek veritabanını kaldırmak için  
  
1.  Bir komut istemi örnek klasöründeki CleanUp.cmd çalıştırın.  
  
##### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Hata ayıklama olmadan örneği çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
