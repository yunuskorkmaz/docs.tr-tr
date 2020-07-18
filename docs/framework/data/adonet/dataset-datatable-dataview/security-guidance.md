---
title: Veri kümesi ve DataTable Güvenlik Kılavuzu
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 2fbac625ae0049fc4c363977dc1d3fbcfb376025
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416199"
---
# <a name="dataset-and-datatable-security-guidance"></a>Veri kümesi ve DataTable Güvenlik Kılavuzu

Bu makale için geçerlidir:

* .NET Framework (tüm sürümler)
* .NET Core ve üzeri
* .NET 5,0 ve üzeri

[DataSet](/dotnet/api/system.data.dataset) ve [DataTable](/dotnet/api/system.data.datatable) türleri, veri kümelerinin yönetilen nesneler olarak belirtilmesine izin veren eski .net bileşenleridir. Bu bileşenler, .NET 1,0 ' de özgün [ADO.NET altyapısının](/dotnet/framework/data/adonet/dataset-datatable-dataview/)bir parçası olarak sunulmuştur. Bu kullanıcıların, ilişkisel veri kümesi üzerinde yönetilen bir görünüm sağlaması, verilerin temel kaynağının XML, SQL veya başka bir teknoloji olması durumunda olup olmadığını soyutlıyoruz.

ADO.NET hakkında daha fazla bilgi için, bkz. [ADO.net belgeleri](/dotnet/framework/data/adonet/).

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>XML 'den bir veri kümesi veya DataTable serisi kaldırılırken varsayılan kısıtlamalar

.NET Framework, .NET Core ve .NET ' in tüm desteklenen sürümlerinde, `DataSet` `DataTable` Serisi kaldırılan verilerde bulunabilecek nesne türleri için aşağıdaki kısıtlamaları yerleştirin. Varsayılan olarak, bu liste şu şekilde kısıtlanır:

* Temel elemanlar ve ilkel eşdeğerleri: `bool` , `char` ,, `sbyte` `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` , `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,
* Yaygın olarak kullanılan temel olmayan: `Type` , `Uri` , ve `BigInteger` .
* Yaygın olarak kullanılan _System. Drawing_ türleri: `Color` ,,, `Point` `PointF` `Rectangle` , `RectangleF` , `Size` , ve `SizeF` .
* `Enum`türü.
* Yukarıdaki türlerin dizileri ve listeleri.

Gelen XML verileri, türü bu listede olmayan bir nesne içeriyorsa:

* Bir özel durum oluşturulur.
* Seri durumdan çıkarma işlemi başarısız olur.

XML 'i var olan bir `DataSet` veya `DataTable` örneğe yüklerken, var olan sütun tanımları da hesaba alınır. Tablo, özel bir türün sütun tanımını zaten içeriyorsa, bu tür XML serisini kaldırma işleminin süresi için izin verilenler listesine geçici olarak eklenir.

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

Nesne türü kısıtlamaları, `XmlSerializer` veya örneğinin serisini kaldırmak için kullanılırken de geçerlidir `DataSet` `DataTable` . Ancak, `BinaryFormatter` veya örneğinin serisini kaldırmak için kullanılırken uygulanamazlar `DataSet` `DataTable` .

`DataAdapter.Fill`Bir `DataTable` ÖRNEĞIN, xml serisini kaldırma API 'leri kullanılmadan doğrudan bir veritabanından doldurulduğu gibi, nesne türü kısıtlamaları kullanırken uygulanmaz.

### <a name="extend-the-list-of-allowed-types"></a>İzin verilen türlerin listesini genişletme

Bir uygulama, yukarıda listelenen yerleşik türlere ek olarak, izin verilen türler listesini özel türleri içerecek şekilde genişletebilir. İzin verilen türler listesini genişlediğinde, değişiklik uygulamadaki _Tüm_ `DataSet` ve `DataTable` örnekleri etkiler. Türler, yerleşik izin verilen türler listesinden kaldırılamaz.

#### <a name="extend-through-configuration-net-framework-40---48"></a>Yapılandırma ile genişletme (.NET Framework 4,0-4,8)

_App.config_ , izin verilen türler listesini genişletmek için kullanılabilir. İzin verilen türler listesini genişletmek için:

* `<configSections>` _System. Data_ yapılandırma bölümüne bir başvuru eklemek için öğesini kullanın.
* `<system.data.dataset.serialization>` / `<allowedTypes>` Ek türleri belirtmek için kullanın.

Her `<add>` öğe, kendi derleme nitelikli tür adını kullanarak yalnızca bir tür belirtmelidir. İzin verilen türler listesine ek türler eklemek için, birden çok `<add>` öğe kullanın.

Aşağıdaki örnek, özel tür ekleyerek izin verilen türlerin listesini genişletmeyi gösterir `Fabrikam.CustomType` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Bir türün derleme nitelikli adını almak için, aşağıdaki kodda gösterildiği gibi [Type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) özelliğini kullanın.

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>Yapılandırma ile genişletme (.NET Framework 2,0-3,5)

Uygulamanız 2,0 veya 3,5 .NET Framework hedefliyorsa, izin verilen türler listesini genişletmek için yukarıdaki _App.config_ mekanizmasını kullanmaya devam edebilirsiniz. Ancak, `<configSections>` aşağıdaki kodda gösterildiği gibi, öğesi biraz farklı görünecektir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>Programlı olarak genişlet (.NET Framework, .NET Core, .NET 5.0 +)

İzin verilen türlerin listesi Ayrıca, aşağıdaki kodda gösterildiği gibi, iyi bilinen Key _System. Data. Datasetdefaultallodilimlerin Types_ile [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) kullanılarak programlı bir şekilde genişletilebilir.

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

Uzantı mekanizması kullanılıyorsa, Key _System. Data. Datasetdefaultallodilimlerin Types_ ile ilişkili değer türünde olmalıdır `Type[]` .

.NET Framework, izin verilen türlerin listesi hem _App.config_ hem de ile genişletilebilir `AppDomain.SetData` . Bu durumda, `DataSet` `DataTable` türü her iki listede de varsa, bir nesnenin veri parçası olarak seri durumdan çıkmasına izin verir.

### <a name="run-an-app-in-audit-mode-net-framework"></a>Bir uygulamayı denetim modunda çalıştırma (.NET Framework)

.NET Framework ' de `DataSet` `DataTable` bir denetim modu özelliği sağlayın. Denetim modu etkin olduğunda `DataSet` ve `DataTable` gelen nesne türlerini izin verilen türler listesiyle karşılaştırırın. Ancak, türüne izin verilmeyen bir nesne görüldüğünde, bir özel **durum oluşturulmaz.** Bunun yerine `DataSet` , `DataTable` `TraceListener` şüpheli bir türün mevcut olduğu tüm ekli örneklere bildirimde bulunur ve `TraceListener` Bu bilgileri günlüğe kaydetmek için izin verir. Hiçbir özel durum oluşturulmaz ve seri durumundan çıkarma işlemi devam eder.

> [!WARNING]
> "Denetim modunda" bir uygulamanın çalıştırılması yalnızca test için kullanılan geçici bir ölçü olmalıdır. Denetim modu etkinleştirildiğinde `DataSet` ve `DataTable` uygulamanızın içinde bir güvenlik deliği ortaya çıkaracak tür kısıtlamalarını zorunlu kılmaz. Daha fazla bilgi için, [Güvenilmeyen girişle ilgili](#swr)olarak [tüm tür kısıtlamalarını](#ratr) ve güvenliği kaldırma başlıklı bölümlere bakın.

Denetim modu, _App.config_aracılığıyla etkinleştirilebilir:

* Öğe için konacak doğru değer hakkında bilgi için bu belgedeki [yapılandırma Ile genişletme](#etc) bölümüne bakın `<configSections>` .
* `<allowedTypes auditOnly="true">`Aşağıdaki biçimlendirmede gösterildiği gibi denetleme modunu etkinleştirmek için kullanın.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

Denetim modu etkinleştirildikten sonra, tercih ettiğiniz yerleşik _App.config_ `TraceListener` `DataSet` `TraceSource.` Izleme kaynağının adı _System. Data. DataSet_olan yerleşik bir bağlantı kurmak içinApp.configkullanabilirsiniz. Aşağıdaki örnek, izleme olaylarını konsola _ve_ diskteki bir günlük dosyasına yazmayı gösterir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

Ve hakkında daha fazla bilgi için `TraceSource` `TraceListener` bkz. [nasıl yapılır: Izleme dinleyicileri Ile TraceSource ve filtreler kullanma](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).

> [!NOTE]
> Bir uygulamayı denetim modunda çalıştırmak .NET Core veya .NET 5,0 ve üzeri sürümlerde kullanılamaz.

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>Tüm tür kısıtlamalarını kaldır

Bir uygulamanın tüm tür sınırlaması kısıtlamalarını ve ' den kaldırması `DataSet` gerekiyorsa `DataTable` :

* Tür sınırlandırma kısıtlamalarını bastırmak için çeşitli seçenekler vardır.
* Kullanılabilir seçenekler, uygulamanın hedeflediği çerçeveye bağlıdır.

> [!WARNING]
> Tüm tür kısıtlamalarını kaldırmak, uygulamanın içinde bir güvenlik deliği ortaya çıkarabilir. Bu mekanizmayı kullanırken, uygulamanın **not** `DataSet` `DataTable` Güvenilmeyen girişi okuyabilmesi ya da okumadığından emin olun. Daha fazla bilgi için bkz. [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) ve [güvenilir olmayan girişle ilgili olarak güvenlik](#swr)başlıklı aşağıdaki bölüm.

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>AppContext yapılandırması aracılığıyla (.NET Framework 4,6-4,8, .NET Core 2,1 ve üzeri, .NET 5,0 ve üzeri)

, `AppContext` , Olarak `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` ayarlandığında, ve ' `true` dan tüm tür sınırlandırma kısıtlamalarını kaldırır `DataSet` `DataTable` .

.NET Framework, bu anahtar aşağıdaki yapılandırmada gösterildiği gibi _App.config_aracılığıyla etkinleştirilebilir:

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

ASP.NET içinde, `<AppContextSwitchOverrides>` öğesi kullanılabilir değil. Bunun yerine, aşağıdaki yapılandırmada gösterildiği gibi, anahtar _Web.config_aracılığıyla etkinleştirilebilir:

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

Daha fazla bilgi için, bkz [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) . öğesi.

.NET Core, .NET 5 ve ASP.NET Core, bu ayar, aşağıdaki JSON 'da gösterildiği gibi, _runtimeconfig.js_tarafından denetlenir:

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

Daha fazla bilgi için bkz. [".NET Core çalışma zamanı yapılandırma ayarları"](/dotnet/core/run-time-config/).

`AllowArbitraryDataSetTypeInstantiation`, aşağıdaki kodda gösterildiği gibi, bir yapılandırma dosyası kullanmak yerine [AppContext. SetSwitch](/dotnet/api/system.appcontext.setswitch) aracılığıyla program aracılığıyla da ayarlanabilir:

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 Önceki programlı yaklaşımı seçerseniz, çağrısı `AppContext.SetSwitch` uygulamalar başlangıcında erken gerçekleşmelidir.

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>Makine genelindeki kayıt defteri aracılığıyla (.NET Framework 2,0-4,8)

`AppContext`Kullanılabilir değilse, tür sınırlandırma denetimleri Windows kayıt defteriyle devre dışı bırakılabilir:

* Bir yöneticinin kayıt defterini yapılandırması gerekir.
* Kayıt defterinin kullanılması makine genelinde bir değişiklik olduğundan makinede çalışan _Tüm_ uygulamaları etkiler.

| Tür  |  Değer |
|---|---|
| **Kayıt defteri anahtarı** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **Değer adı** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **Değer türü** | `REG_SZ` |
| **Değer verisi** | `true` |

64 bitlik bir işletim sisteminde bu değerin hem 64 bit anahtar (yukarıda gösterilen) hem de 32-bit anahtarı için eklenmesi gerekir. 32 bit anahtarı konumunda bulunur `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .

Yapılandırmak için kayıt defterini kullanma hakkında daha fazla bilgi için `AppContext` , bkz. ["kitaplık tüketicileri Için AppContext"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>Güvenilmeyen girişle ilgili güvenlik

Ancak `DataSet` `DataTable` , XML yüklerini seri durumdan çıkarma sırasında bulunmasına izin verilen türlerin varsayılan sınırlamalarını uygular __ `DataSet` ve `DataTable` Güvenilmeyen girişle doldurulurken genel olarak güvenli değildir.__ Aşağıda, bir `DataSet` veya `DataTable` örneğinin güvenilmeyen girişi okuyabilme yöntemlerinin ayrıntılı olmayan bir listesi verilmiştir.

* Bir `DataAdapter` veritabanına başvurur ve `DataAdapter.Fill` yöntemi bir `DataSet` veritabanı sorgusunun içeriğiyle doldurmak için kullanılır.
* `DataSet.ReadXml`Or `DataTable.ReadXml` yöntemi, sütun ve satır bilgilerini IÇEREN bir XML dosyasını okumak için kullanılır.
* Bir `DataSet` veya `DataTable` örneği, bir ASP.net (SOAP) Web HIZMETLERININ veya WCF uç noktasının bir parçası olarak serileştirilir.
* Bir seri hale getirici `XmlSerializer` , BIR `DataSet` XML akışından bir veya örneğinin serisini kaldırmak için kullanılır `DataTable` .
* Bir seri hale getirici `JsonConvert` , BIR `DataSet` JSON akışından bir veya örneğinin serisini kaldırmak için kullanılır `DataTable` . `JsonConvert`, kitaplığındaki popüler üçüncü taraf [Newtonsoft.Js](https://www.newtonsoft.com/json) bir yöntemdir.
* Bir seri hale getirici `BinaryFormatter` , `DataSet` ham bayt akışından bir veya örneğinin serisini kaldırmak için kullanılır `DataTable` .

Bu belgede, yukarıdaki senaryolara yönelik güvenlik konuları ele alınmaktadır.

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>`DataAdapter.Fill` `DataSet` Güvenilmeyen bir veri kaynağından doldurmak için kullanın

`DataSet` `DataAdapter` Aşağıdaki örnekte gösterildiği gibi, bir örnek, [ `DataAdapter.Fill` yöntemi](/dotnet/api/system.data.common.dataadapter.fill)kullanılarak bir öğesinden doldurulabilir.

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

(Yukarıdaki kod örneği, [DataAdapter nesnesinden bir veri kümesini doldururken](../populating-a-dataset-from-a-dataadapter.md)bulunan daha büyük bir örneğin bir parçasıdır.)

> Çoğu uygulama basitleşebilir ve veritabanı katmanının güvenilir olduğunu varsayabilir. Bununla birlikte, uygulamalarınızın iş [modellemesinin](https://www.microsoft.com/securityengineering/sdl/threatmodeling) bir habiti varsa, tehdit modeliniz uygulama (istemci) ile veritabanı katmanı (sunucu) arasında bir güven sınırı olduğunu göz önünde bulundurmayabilir. İstemci ve sunucu arasında [karşılıklı kimlik doğrulama](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) veya [AAD kimlik doğrulaması](/azure/azure-sql/database/authentication-aad-overview) kullanmak, bununla ilişkili riskleri karşılamak için bir yoldur. Bu bölümün geri kalanında güvenilmeyen sunucuya bağlanan istemcinin olası sonucu ele alınmaktadır.

`DataAdapter`Güvenilir olmayan bir veri kaynağına işaret eden sonuçlar kendisinin uygulamasına bağlıdır `DataAdapter` .

### <a name="sqldataadapter"></a>SqlDataAdapter

Yerleşik tür [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)için, güvenilmeyen bir veri kaynağına başvurmak, hizmet reddi (DOS) saldırısının oluşmasına neden olabilir. DoS saldırısı, uygulamanın yanıt vermemesine veya kilitlenmelerine neden olabilir. Bir saldırgan uygulama ile birlikte bir DLL 'yi kurtabiliyor ise, yerel kod yürütmeye de ulaşabiliyor olabilir.

### <a name="other-dataadapter-types"></a>Diğer DataAdapter türleri

Üçüncü taraf `DataAdapter` uygulamaları, güvenilmeyen girişler karşısında sağladıkları güvenlik garantisi hakkında kendi değerlendirmelerini sağlamalıdır. .NET, bu uygulamalarla ilgili herhangi bir güvenlik garantisi yapamaz.

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>DataSet. ReadXml ve DataTable. ReadXml

`DataSet.ReadXml`Ve `DataTable.ReadXml` yöntemleri güvenilmeyen girişle kullanıldığında güvenli değildir. Bunun yerine, bu belgede daha sonra özetlenen alternatifden birini kullanmayı düşünmemiz önerilir.

`DataSet.ReadXml`Ve uygulamaları `DataTable.ReadXml` serileştirme güvenlik açıklarına göre ilk başta oluşturulmuştur. Sonuç olarak, kod geçerli en iyi güvenlik uygulamalarını izlemez. Bu API 'Ler, saldırganların Web uygulamalarına yönelik DoS saldırıları gerçekleştirmesine yönelik vektörler olarak kullanılabilir. Bu saldırılar, Web hizmetini yanıt vermemeye veya beklenmeyen işlem sonlandırmasına neden olarak işleyebilir. Framework bu saldırı kategorilerine yönelik azaltmaları sağlamaz ve .NET bu davranışı "tasarıma göre" kabul eder.

.NET, ve ' de bilgi açığa çıkması veya uzaktan kod yürütme gibi bazı sorunları azaltmak için güvenlik güncelleştirmeleri yayımlamıştır `DataSet.ReadXml` `DataTable.ReadXml` . .NET güvenlik güncelleştirmeleri, bu tehdit kategorilerine karşı tamamen koruma sağlayamayabilir. Tüketiciler, bağımsız senaryolarını değerlendirmeli ve bu risklerle ilgili olası pozlandırmayı göz önünde bulundurmalıdır.

Tüketiciler, bu API 'lere yönelik güvenlik güncelleştirmelerinin bazı durumlarda uygulama uyumluluğunu etkileyebileceğini unutmayın. Ayrıca, bu API 'lerde bir nobir güvenlik açığı bulduğundan, .NET 'in bir güvenlik güncelleştirmesini yayımlayabileceği bir olasılık vardır.

Bu API 'lerin tüketicilerinin şunları yapmanızı öneririz:

* Bu belgede daha sonra özetlenen alternatifden birini kullanmayı düşünün.
* Uygulamalarda bireysel risk değerlendirmeleri gerçekleştirin.

Bu API 'Lerin kullanılıp kullanılmayacağını belirleme tüketicinin tek sorumluluğudur. Tüketiciler, bu API 'Leri kullanarak eşlik eden, yasal gereksinimleri de içeren tüm güvenlik, teknik ve yasal riskleri değerlendirmelidir.

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>ASP.NET Web Hizmetleri veya WCF aracılığıyla veri kümesi ve DataTable

`DataSet` `DataTable` Aşağıdaki kodda gösterildiği gibi, bir ASP.net (SOAP) Web hizmetinde bir veya örneği kabul etmek mümkündür:

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

Bu bir varyasyon, `DataSet` `DataTable` bir parametre olarak kabul edilmez veya doğrudan, aşağıdaki kodda gösterildiği gıbı Genel SOAP serileştirilmiş nesne grafiğinin bir parçası olarak kabul edilmez:

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Ya da ASP.NET Web Hizmetleri yerine WCF kullanma:

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Bu durumların tümünde, tehdit modeli ve güvenlik garantisi, [DataSet. ReadXml ve DataTable. ReadXml bölümü](#dsrdtr)ile aynıdır.

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>XmlSerializer aracılığıyla bir veri kümesi veya DataTable serisini kaldırma

Geliştiriciler `XmlSerializer` `DataSet` `DataTable` , aşağıdaki kodda gösterildiği gibi, serisini kaldırmak ve örnekleri için kullanılabilir:

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Bu durumlarda, tehdit modeli ve güvenlik garantisi, [DataSet. ReadXml ve DataTable. ReadXml bölümüyle](#dsrdtr) aynıdır

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>JsonConvert aracılığıyla bir veri kümesi veya DataTable serisini kaldırma

Popüler üçüncü taraf Newtonsoft Library [JSON.net](https://www.newtonsoft.com/json) `DataSet` `DataTable` , aşağıdaki kodda gösterildiği gibi seri durumdan çıkarılacak ve örnekleri için kullanılabilir:

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

Güvenilmeyen bir `DataSet` `DataTable` JSON blobundan bu şekilde veya bu şekilde seri durumdan çıkarmak güvenli değildir. Bu model, hizmet reddi saldırılarına karşı savunmasızdır. Bu tür bir saldırı, uygulamayı kilitlerler veya yanıt vermemeye işleyebilir.

> [!NOTE]
> Microsoft, _Newtonsoft.Js_gibi üçüncü taraf kitaplıkların uygulanmasını garanti etmez veya desteklemez. Bu bilgiler, tamamlanma zamanı için sağlanır ve bu yazma zamanından itibaren doğru olur.

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>BinaryFormatter aracılığıyla DataSet veya DataTable serisini kaldırma

Geliştiricilerin `BinaryFormatter` `NetDataContractSerializer` `SoapFormatter` Güvenilmeyen bir yükün veya örneğinin serisini kaldırmak için hiçbir şekilde,, veya ilgili ***güvenli olmayan*** biçimleri kullanması gerekir `DataSet` `DataTable` :

* Bu, tam bir uzaktan kod yürütme saldırısından etkilenir.
* `SerializationBinder`Bu tür bir saldırıyı engellemek için özel kullanımı yeterli değildir.

## <a name="safe-replacements"></a>Güvenli değişiklikler

Şu iki uygulama için:

* `DataSet` `DataTable` . Asmx SOAP uç noktasını veya WCF uç noktasını kabul edin.
* Güvenilmeyen verileri veya örneğine serisini kaldırma `DataSet` `DataTable` .

Nesne modelini [Entity Framework](/ef)kullanacak şekilde değiştirmeyi düşünün. Entity Framework:

* , İlişkisel verileri temsil eden zengin, modern, nesne odaklı bir çerçevedir.
* Veritabanı sorgularının Entity Framework nesne modelleriniz aracılığıyla proje veritabanını kolayca sunmayı kolaylaştırmak için, veritabanı sağlayıcılarının [farklı bir ekosistemini](/ef/core/providers/) getirir.
* Güvenilmeyen kaynaklardan veri serisini kaldırırken yerleşik korumalar sunar.

`.aspx`SOAP uç noktaları kullanan uygulamalar için, bu uç noktaları [WCF](/dotnet/framework/wcf/)kullanacak şekilde değiştirmeyi göz önünde bulundurun. WCF, Web Hizmetleri için daha tam özellikli bir değiştirme işlemi `.asmx` . WCF uç noktaları, mevcut çağıranlar ile uyumluluk için [SOAP aracılığıyla gösterilebilir](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) .
