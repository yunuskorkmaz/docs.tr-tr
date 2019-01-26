---
title: Veritabanı erişimi etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: db79f2d7605a71997ede134152b12395b9193f95
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066096"
---
# <a name="database-access-activities"></a>Veritabanı erişimi etkinlikleri
Veritabanı erişimi etkinlikleri iş akışı içindeki bir veritabanına erişmek izin verin. Bu etkinliklerin alma veya bilgileri değiştirin ve veritabanlarına erişim ver [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) veritabanına erişmek için.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  Bu dizin mevcut değilse (indirme sayfası) Git tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Veritabanı etkinlikleri
 Bu örnekte bulunan etkinliklerinin listesini aşağıdaki bölümlerde ayrıntılı olarak açıklanmaktadır.

## <a name="dbupdate"></a>DbUpdate
 (Ekleme, güncelleştirme, silme ve diğer değişikliklerin) veritabanında değişiklik üreten bir SQL sorgusunu çalıştırır.

 Bu sınıf, zaman uyumsuz olarak kendi işini gerçekleştirir (türetildiği <xref:System.Activities.AsyncCodeActivity> ve zaman uyumsuz özelliklerini kullanır).

 Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.

 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.

 Sonra `DbUpdate` olan yürütüldü, etkilenen kayıtların sayısı döndürülür `AffectedRecords` özelliği.

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
|ProviderName|ADO.NET sağlayıcısı değişmez adı. Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.|
|bağlantı dizesi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|
|Sql|Çalıştırılacak SQL komutu.|
|Parametreler|SQL sorgu parametreleri koleksiyonu.|
|AffectedRecords|Son işlem tarafından etkilenen kayıtların sayısı.|

## <a name="dbqueryscalar"></a>DbQueryScalar
 Veritabanından tek bir değer alır. bir sorgu yürütür.

 Bu sınıf, zaman uyumsuz olarak kendi işini gerçekleştirir (türetildiği <xref:System.Activities.AsyncCodeActivity%601> ve zaman uyumsuz özelliklerini kullanır).

 Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.

 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.

 Sonra `DbQueryScalar` olan yürütüldü, skaler döndürülür `Result out` bağımsız değişken (tür `TResult`, yani temel sınıfta tanımlanan <xref:System.Activities.AsyncCodeActivity%601>).

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
|ProviderName|ADO.NET sağlayıcısı değişmez adı. Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.|
|bağlantı dizesi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|
|Sql|Çalıştırılacak SQL komutu.|
|Parametreler|SQL sorgu parametreleri koleksiyonu.|
|Sonuç|Sorgu yürütüldükten sonra elde edilen skaler. Bu bağımsız değişken türünde `TResult`.|

## <a name="dbquery"></a>DbQuery
 Nesnelerin bir listesini alır. bir sorgu yürütür. Sorgu yürütüldükten sonra bir eşleme işlev yürütülür (olabilir <xref:System.Func%601> < `DbDataReader`, `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Bu eşleme işlevi bir kaydı alır bir `DbDataReader` ve döndürülecek nesnesine eşler.

 Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.

 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.

 Kullanarak SQL sorgusunun sonuçları alınırken bir `DbDataReader`. Etkinlik gezinir `DbDataReader` ve satırlarda eşler `DbDataReader` örneğine `TResult`. Kullanıcıyı `DbQuery` eşleme kod ve bu iki şekilde yapılır sağlamalıdır: kullanarak bir <xref:System.Func%601> < `DbDataReader`, `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. Bu durumda, tek bir yürütme nabzını içinde Haritası gerçekleştirilir. Bu nedenle, daha hızlı, ancak bu XAML için seri hale getirilemiyor. En son durumda birden çok darbelerin Haritası gerçekleştirilir. Bu nedenle, bunu daha yavaş olabilir, ancak XAML için sıralanabilir ve bildirimli olarak yazılmış (herhangi bir mevcut etkinlik eşlemede katılabilir).

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
|ProviderName|ADO.NET sağlayıcısı değişmez adı. Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.|
|bağlantı dizesi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|
|Sql|Çalıştırılacak SQL komutu.|
|Parametreler|SQL sorgu parametreleri koleksiyonu.|
|Eşleyici|İşlev eşleme mapping (<xref:System.Func%601><`DbDataReader`, `TResult`>) bir kayda alan `DataReader` sorgu yürütülürken zaman almış ve türünde bir nesne örneğini döndürür `TResult` içineklenecek`Result` koleksiyonu.<br /><br /> Bu durumda, tek bir yürütme nabzını içinde eşleme gerçekleştirilir, ancak bildirimli olarak Tasarımcısı'nı kullanarak yazılması olamaz.|
|MapperFunc|İşlev eşleme mapping (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) bir kayda alan `DataReader` sorgu yürütülürken zaman almış ve türünde bir nesne örneğini döndürür `TResult` içineklenecek`Result` koleksiyonu.<br /><br /> Bu durumda, eşleme, birden çok yürütme darbelerin gerçekleştirilir. Bu işlev için XAML sıralanabilir ve bildirimli olarak yazılmış (herhangi bir mevcut etkinlik eşlemede katılabilir).|
|Sonuç|Nesnelerinin listesi elde sorgusunun yürütülmesi ve her kayıt için eşleme işlev yürütme doğrulanamadığı `DataReader`.|

## <a name="dbquerydataset"></a>DbQueryDataSet
 Döndüren bir sorgu yürütür bir <xref:System.Data.DataSet>. Bu sınıf, zaman uyumsuz olarak kendi işini gerçekleştirir. Öğesinden türetilen <xref:System.Activities.AsyncCodeActivity> < `TResult`> ve zaman uyumsuz özelliklerini kullanır.

 Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.

 Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.

 Sonra `DbQueryDataSet` yürütülür `DataSet` döndürülür `Result out` bağımsız değişken (tür `TResult`, diğer bir deyişle temel sınıfta tanımlanan <xref:System.Activities.AsyncCodeActivity%601>).

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
|ProviderName|ADO.NET sağlayıcısı değişmez adı. Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.|
|bağlantı dizesi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Tür <xref:System.Data.Common.DbCommand> yürütülecek.|
|Sql|Çalıştırılacak SQL komutu.|
|Parametreler|SQL sorgu parametreleri koleksiyonu.|
|Sonuç|<xref:System.Data.DataSet> Sorgu yürütüldükten sonra elde edilir.|

## <a name="configuring-connection-information"></a>Bağlantı bilgilerini yapılandırma
 Tüm DbActivities aynı yapılandırma parametrelerini paylaşın. İki şekilde yapılandırılabilir:

-   `ConnectionString + InvariantName`: ADO.NET sağlayıcısı sabit adı ve bağlantı dizesini ayarlayalım.

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

-   Etkinlik:

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a>Bu örneği çalıştırmadan

### <a name="setup-instructions"></a>Kurulum yönergeleri
 Bu örnek, bir veritabanı kullanır. Kurulum ve yükleme komut dosyası (Setup.cmd) örnek ile sağlanır. Komut istemi kullanarak bu dosyayı yürütmeniz gerekir.

 Setup.cmd betiği aşağıdakileri SQL komutlarını içeren CreateDb.sql komut dosyasını çağırır:

-   DbActivitiesSample adlı bir veritabanı oluşturur.

-   Rolleri tablo oluşturur.

-   Çalışanlar bir tablo oluşturur.

-   Üç kayıt rolleri tabloya ekler.

-   On iki kayıtları çalışanlar tabloya ekler.

##### <a name="to-run-setupcmd"></a>Setup.cmd çalıştırmak için

1.  Bir komut istemi açın.

2.  DbActivities örnek klasörüne gidin.

3.  "Setup.cmd" yazın ve ENTER tuşuna basın.

    > [!NOTE]
    >  Setup.cmd yerel makine SqlExpress Örneğinizde örneği yüklemek çalışır. Diğer SQL server örneği'nde yüklemek istiyorsanız, Setup.cmd ile yeni örnek adını düzenleyin.

##### <a name="to-uninstall-the-sample-database"></a>Örnek veritabanını kaldırmak için

1.  Örnek klasöründeki bir komut isteminde CleanUp.cmd çalıştırın.

##### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1.  Visual Studio 2010'da çözümü açın

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3.  Hata ayıklama olmadan örneği çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
