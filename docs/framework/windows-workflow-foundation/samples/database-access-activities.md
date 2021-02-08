---
description: 'Daha fazla bilgi edinin: veritabanı erişim etkinlikleri'
title: Veritabanı Erişimi Etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 421da4a55997dac62ccc5c598bc401a20711ec61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792550"
---
# <a name="database-access-activities"></a>Veritabanı Erişimi Etkinlikleri

Veritabanı erişim etkinlikleri, bir iş akışı içindeki bir veritabanına erişmenizi sağlar. Bu etkinlikler, veritabanlarına erişim sağlamak veya bilgileri değiştirmek ve veritabanına erişmek için [ADO.net](../../data/adonet/index.md) kullanmayı sağlar.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için (indirme sayfası) bölümüne gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Veritabanı etkinlikleri

Aşağıdaki bölümler, bu örneğe dahil edilen etkinliklerin listesini ayrıntılandırır.

## <a name="dbupdate"></a>DbUpdate

Veritabanında değişiklik üreten bir SQL sorgusu yürütür (ekleme, güncelleştirme, silme ve diğer değişiklikler).

Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (öğesinden türetilir <xref:System.Activities.AsyncCodeActivity> ve zaman uyumsuz yeteneklerini kullanır).

Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .

Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.

`DbUpdate`Yürütüldükten sonra, etkilenen kayıtların sayısı, `AffectedRecords` özelliğinde döndürülür.

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

|Bağımsız Değişken|Description|
|-|-|
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.|
|Dizisi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.|
|CommandType|Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|AffectedRecords|Son işlemden etkilenen kayıt sayısı.|

## <a name="dbqueryscalar"></a>DbQueryScalar

Veritabanından tek bir değer alan bir sorgu yürütür.

Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (öğesinden türetilir <xref:System.Activities.AsyncCodeActivity%601> ve zaman uyumsuz yeteneklerini kullanır).

Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .

Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.

`DbQueryScalar`Yürütüldükten sonra skaler, `Result out` bağımsız değişkende ( `TResult` temel sınıfta tanımlanan türünde <xref:System.Activities.AsyncCodeActivity%601> ) döndürülür.

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

|Bağımsız Değişken|Description|
|-|-|
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.|
|Dizisi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.|
|CommandType|Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|Sonuç|Sorgu yürütüldükten sonra elde edilen skaler. Bu bağımsız değişken türündedir `TResult` .|

## <a name="dbquery"></a>DbQuery

Bir nesne listesini alan bir sorgu yürütür. Sorgu yürütüldükten sonra bir eşleme işlevi yürütülür (Bu <xref:System.Func%601> < `DbDataReader` , `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult`> olabilir). Bu eşleme işlevi, içindeki bir kaydı alır `DbDataReader` ve döndürülecek nesne ile eşler.

Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .

Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.

SQL sorgusunun sonuçları bir kullanılarak alınır `DbDataReader` . Etkinlik `DbDataReader` öğesinde yinelenir ve içindeki satırları `DbDataReader` bir örneğine eşler `TResult` . Kullanıcısının `DbQuery` eşleme kodunu sağlaması gerekir ve bu iki şekilde yapılabilir: bir <xref:System.Func%601> < `DbDataReader` , `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult`> kullanarak. İlk durumda, eşleme tek bir yürütme darbeli yapılır. Bu nedenle daha hızlıdır, ancak bu XAML 'e serileştirilemiyor. Son durumda, eşleme birden çok pulda gerçekleştirilir. Bu nedenle, daha yavaş olabilir ancak XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (varolan herhangi bir etkinlik eşlemeye katılabilir).

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

|Bağımsız Değişken|Description|
|-|-|
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.|
|Dizisi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.|
|CommandType|Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|Eşleyici|<xref:System.Func%601> < `DbDataReader` `TResult` Sorgu yürütmenin sonucu olarak elde edilen bir kaydı alan eşleme işlevi (,>) `DataReader` ve `TResult` koleksiyona eklenmek üzere türünde bir nesnenin örneğini döndürür `Result` .<br /><br /> Bu durumda, eşleme tek bir yürütmede yürütme yapılır, ancak tasarımcı kullanılarak bildirimli olarak yazılamıyor.|
|MapperFunc|<xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult` Sorgu yürütmenin sonucu olarak elde edilen bir kaydı alan eşleme işlevi (,>) `DataReader` ve `TResult` koleksiyona eklenmek üzere türünde bir nesnenin örneğini döndürür `Result` .<br /><br /> Bu durumda, eşleme birden çok sayıda yürütmede yapılır. Bu işlev XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (var olan herhangi bir etkinlik eşlemede yer alabilir).|
|Sonuç|Sorguyu yürütmenin ve içindeki her kayıt için eşleme işlevinin yürütüldüğü sonuç olarak elde edilen nesnelerin listesi `DataReader` .|

## <a name="dbquerydataset"></a>DbQueryDataSet

Döndüren bir sorgu yürütür <xref:System.Data.DataSet> . Bu sınıf, zaman uyumsuz olarak işini gerçekleştirir. <xref:System.Activities.AsyncCodeActivity> < `TResult`> türetilir ve zaman uyumsuz yeteneklerini kullanır.

Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .

Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.

Yürütüldükten sonra, `DbQueryDataSet` `DataSet` `Result out` bağımsız değişkende ( `TResult` temel sınıfta tanımlanan türünde <xref:System.Activities.AsyncCodeActivity%601> ) döndürülür.

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

|Bağımsız Değişken|Description|
|-|-|
|Adı|ADO.NET sağlayıcısı sabit adı. Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.|
|Dizisi|Veritabanına bağlanmak için bağlantı dizesi. Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.|
|ConfigName|Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı. Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.|
|CommandType|Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .|
|Sql|Yürütülecek SQL komutu.|
|Parametreler|SQL sorgusunun parametrelerinin koleksiyonu.|
|Sonuç|<xref:System.Data.DataSet> Sorgu yürütüldükten sonra elde edilen.|

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

- `ConfigName`: Bağlantı bilgilerini içeren yapılandırma bölümünün adını ayarlayın.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
