---
title: Veritabanı Erişimi Etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: ed3f0ad3f2fd19f622c9cb0faf7d5cd864b81995
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094650"
---
# <a name="database-access-activities"></a>Veritabanı Erişimi Etkinlikleri

Veritabanı erişim etkinlikleri, bir iş akışı içindeki bir veritabanına erişmenizi sağlar. Bu etkinlikler, veritabanlarına erişim sağlamak veya bilgileri değiştirmek ve veritabanına erişmek için [ADO.net](../../data/adonet/index.md) kullanmayı sağlar.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek için (sayfayı indir) bölümüne gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Veritabanı etkinlikleri

Aşağıdaki bölümler, bu örneğe dahil edilen etkinliklerin listesini ayrıntılandırır.

## <a name="dbupdate"></a>DbUpdate

Veritabanında değişiklik üreten bir SQL sorgusu yürütür (ekleme, güncelleştirme, silme ve diğer değişiklikler).

Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (<xref:System.Activities.AsyncCodeActivity> türetilir ve zaman uyumsuz yeteneklerini kullanır).

Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.

Yürütülecek sorgu `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyonundan geçirilir.

`DbUpdate` yürütüldükten sonra, etkilenen kayıtların sayısı `AffectedRecords` özelliğinde döndürülür.

```csharp
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
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa, `ConnectionString` de ayarlanmalıdır.|
|ConnectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa, `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Yürütülecek <xref:System.Data.Common.DbCommand> türü.|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|AffectedRecords|Son işlemden etkilenen kayıt sayısı.|

## <a name="dbqueryscalar"></a>DbQueryScalar

Veritabanından tek bir değer alan bir sorgu yürütür.

Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (<xref:System.Activities.AsyncCodeActivity%601> türetilir ve zaman uyumsuz yeteneklerini kullanır).

Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.

Yürütülecek sorgu `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyonundan geçirilir.

`DbQueryScalar` yürütüldükten sonra skaler, `Result out` bağımsız değişkeninde (`TResult`türünde, temel sınıfta tanımlanan <xref:System.Activities.AsyncCodeActivity%601>) döndürülür.

```csharp
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
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa, `ConnectionString` de ayarlanmalıdır.|
|ConnectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa, `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Yürütülecek <xref:System.Data.Common.DbCommand> türü.|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|Sonuç|Sorgu yürütüldükten sonra elde edilen skaler. Bu bağımsız değişken `TResult`türündedir.|

## <a name="dbquery"></a>DbQuery

Bir nesne listesini alan bir sorgu yürütür. Sorgu yürütüldükten sonra bir eşleme işlevi yürütülür (<xref:System.Func%601><`DbDataReader`, `TResult`> veya <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>) olabilir. Bu eşleme işlevi `DbDataReader` bir kayıt alır ve bunu döndürülecek nesneyle eşler.

Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.

Yürütülecek sorgu `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyonundan geçirilir.

SQL sorgusunun sonuçları bir `DbDataReader`kullanılarak alınır. Etkinlik `DbDataReader` boyunca yinelenir ve `DbDataReader` satırları `TResult`bir örneğine eşler. `DbQuery` kullanıcısının eşleme kodunu sağlaması gerekir ve bu iki şekilde yapılabilir: <xref:System.Func%601><`DbDataReader`, `TResult`> veya <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`> kullanımı. İlk durumda, eşleme tek bir yürütme darbeli yapılır. Bu nedenle daha hızlıdır, ancak bu XAML 'e serileştirilemiyor. Son durumda, eşleme birden çok pulda gerçekleştirilir. Bu nedenle, daha yavaş olabilir ancak XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (varolan herhangi bir etkinlik eşlemeye katılabilir).

```csharp
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
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa, `ConnectionString` de ayarlanmalıdır.|
|ConnectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa, `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Yürütülecek <xref:System.Data.Common.DbCommand> türü.|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|Eşleyici|Eşleme işlevi (<xref:System.Func%601><`DbDataReader`, `TResult`>) sorguyu yürütmenin sonucu olarak elde edilen `DataReader` bir kayıt alır ve `TResult` koleksiyonuna eklenmek üzere `Result` türünde bir nesnenin örneğini döndürür.<br /><br /> Bu durumda, eşleme tek bir yürütmede yürütme yapılır, ancak tasarımcı kullanılarak bildirimli olarak yazılamıyor.|
|MapperFunc|Eşleme işlevi (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) sorguyu yürütmenin sonucu olarak elde edilen `DataReader` bir kayıt alır ve `TResult` koleksiyonuna eklenmek üzere `Result` türünde bir nesnenin örneğini döndürür.<br /><br /> Bu durumda, eşleme birden çok sayıda yürütmede yapılır. Bu işlev XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (var olan herhangi bir etkinlik eşlemede yer alabilir).|
|Sonuç|Sorguyu yürütmenin ve `DataReader`her kayıt için eşleme işlevinin yürütüldüğü sonuç olarak elde edilen nesnelerin listesi.|

## <a name="dbquerydataset"></a>DbQueryDataSet

<xref:System.Data.DataSet>döndüren bir sorgu yürütür. Bu sınıf, zaman uyumsuz olarak işini gerçekleştirir. <xref:System.Activities.AsyncCodeActivity><`TResult`> türetilir ve zaman uyumsuz yeteneklerini kullanır.

Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.

Yürütülecek sorgu `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyonundan geçirilir.

`DbQueryDataSet` yürütüldükten sonra, `DataSet` `Result out` bağımsız değişkenine döndürülür (`TResult`türü, temel sınıfta tanımlanmıştır <xref:System.Activities.AsyncCodeActivity%601>).

```csharp
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
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa, `ConnectionString` de ayarlanmalıdır.|
|ConnectionString|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa, `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.|
|CommandType|Yürütülecek <xref:System.Data.Common.DbCommand> türü.|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|Sonuç|Sorgu yürütüldükten sonra elde edilen <xref:System.Data.DataSet>.|

## <a name="configuring-connection-information"></a>Bağlantı bilgilerini yapılandırma

Tüm Dbacmize aynı yapılandırma parametrelerini paylaşır. İki şekilde yapılandırılabilirler:

- `ConnectionString + InvariantName`: ADO.NET sağlayıcısı sabit adını ve bağlantı dizesini ayarlayın.

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- `ConfigName`: bağlantı bilgilerini içeren yapılandırma bölümünün adını ayarlayın.

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- Etkinlikte:

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a>Bu örnek çalıştırılıyor

### <a name="setup-instructions"></a>Kurulum yönergeleri

Bu örnek bir veritabanı kullanır. Örnekle birlikte bir kurulum ve yükleme betiği (Setup. cmd) sağlanır. Komut istemi 'ni kullanarak bu dosyayı yürütmeniz gerekir.

Setup. cmd betiği, aşağıdakileri yapan SQL komutlarını içeren CreateDb. SQL komut dosyasını çağırır:

- DbActivitiesSample adlı bir veritabanı oluşturur.

- Roller tablosu oluşturur.

- Çalışanlar tablosu oluşturur.

- Roller tablosuna üç kayıt ekler.

- Çalışanlar tablosuna on iki kayıt ekler.

##### <a name="to-run-setupcmd"></a>Setup. cmd dosyasını çalıştırmak için

1. Bir komut istemi açın.

2. Dbacmize Sample klasörüne gidin.

3. "Setup. cmd" yazın ve ENTER tuşuna basın.

    > [!NOTE]
    > Setup. cmd, örneği yerel makinenizde SqlExpress örneğine yüklemeye çalışır. Bunu başka bir SQL Server örneğine yüklemek istiyorsanız, Setup. cmd dosyasını yeni örnek adıyla düzenleyin.

##### <a name="to-uninstall-the-sample-database"></a>Örnek veritabanını kaldırmak için

1. Komut isteminde Sample klasöründen Cleanup. cmd ' i çalıştırın.

##### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Çözümü Visual Studio 2010 ' de açın

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Örneği hata ayıklama olmadan çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
