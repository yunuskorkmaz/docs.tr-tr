---
title: ADO.NET Entity Framework bağlantı dizeleri
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 392e51022dc0f98b9fad656b9f950cd25588f31a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040340"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>ADO.NET Entity Framework bağlantı dizeleri

Bir bağlantı dizesi, veri sağlayıcısından bir veri kaynağına parametre olarak geçirilen başlatma bilgilerini içerir. Söz dizimi veri sağlayıcısına bağlıdır ve bağlantı dizesi bir bağlantıyı açma denemesi sırasında ayrıştırılır. Entity Framework tarafından kullanılan bağlantı dizeleri, Entity Framework destekleyen temel alınan ADO.NET veri sağlayıcısına bağlanmak için kullanılan bilgileri içerir. Ayrıca gerekli model ve eşleme dosyaları hakkında bilgiler içerir.

Bağlantı dizesi, model ve eşleme meta verilerine erişirken ve veri kaynağına bağlanırken EntityClient sağlayıcı tarafından kullanılır. Bağlantı dizesine erişilebilir veya <xref:System.Data.EntityClient.EntityConnection><xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> özelliği aracılığıyla ayarlanabilir. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> sınıfı bağlantı dizesinde programlı olarak parametreler oluşturmak veya erişmek için kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](how-to-build-an-entityconnection-connection-string.md).

[Varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) , uygulamanın yapılandırma dosyasında depolanan bir bağlantı dizesi oluşturur. <xref:System.Data.Objects.ObjectContext>, nesne sorguları oluştururken bu bağlantı bilgilerini otomatik olarak alır. Bir <xref:System.Data.Objects.ObjectContext> örneği tarafından kullanılan <xref:System.Data.EntityClient.EntityConnection> <xref:System.Data.Objects.ObjectContext.Connection%2A> özelliğinden erişilebilir. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi

Bağlantı dizelerine ilişkin genel söz dizimi hakkında bilgi edinmek için bkz. [bağlantı dizesi sözdizimi | ADO.NET içinde bağlantı dizeleri](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Bağlantı dizesi parametreleri

Aşağıdaki tabloda <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>anahtar sözcük değerleri için geçerli adlar listelenmektedir.

|Sözcükle|Açıklama|
|-------------|-----------------|
|`Provider`|`Name` anahtar sözcüğü belirtilmemişse gereklidir. Temel sağlayıcı için <xref:System.Data.Common.DbProviderFactory> nesnesini almak üzere kullanılan sağlayıcı adı. Bu değer sabittir.<br /><br /> `Name` anahtar sözcüğü bir varlık bağlantı dizesinde yer olmadığında, `Provider` anahtar sözcüğü için boş olmayan bir değer gerekir. Bu anahtar sözcük, `Name` anahtar sözcüğüyle birbirini dışlıyor.|
|`Provider Connection String`|İsteğe bağlı. Temel alınan veri kaynağına geçirilen sağlayıcıya özel bağlantı dizesini belirtir. Bu bağlantı dizesi, veri sağlayıcısı için geçerli anahtar sözcük/değer çiftleri içeriyor. Geçersiz `Provider Connection String`, veri kaynağı tarafından değerlendirildiğinde çalışma zamanı hatasına neden olur.<br /><br /> Bu anahtar sözcük, `Name` anahtar sözcüğüyle birbirini dışlıyor.<br /><br /> [ADO.NET bağlantı dizelerinin](../connection-strings.md)genel sözdizimine göre değeri attığınızdan emin olun. Örneğin, aşağıdaki bağlantı dizesini göz önünde bulundurun: `Server=serverName; User ID = userID`. Noktalı virgül içerdiğinden bunun kaçışlı olması gerekir. Çift tırnak işaretleri içermediğinden, bu, kaçış için kullanılabilir:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|`Name` anahtar sözcüğü belirtilmemişse gereklidir. Meta veri ve eşleme bilgilerinin aranacağı Dizin, dosya ve kaynak konumlarının kanal ile ayrılmış listesi. Aşağıda bir örnek verilmiştir:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Kanal ayırıcısının her tarafında boş boşluklar yok sayılır.<br /><br /> Bu anahtar sözcük, `Name` anahtar sözcüğüyle birbirini dışlıyor.|
|`Name`|Uygulama isteğe bağlı olarak, gerekli anahtar sözcük/değer bağlantı dizesi değerlerini sağlayan bir uygulama yapılandırma dosyasında bağlantı adını belirtebilir. Bu durumda, bunları doğrudan bağlantı dizesinde sağlayamazsınız. Yapılandırma dosyasında `Name` anahtar sözcüğüne izin verilmez.<br /><br /> `Name` anahtar sözcüğü bağlantı dizesinde yer olmadığında, Provider anahtar sözcüğü için boş olmayan değerler gerekir.<br /><br /> Bu anahtar sözcük, diğer tüm bağlantı dizesi anahtar sözcükleriyle birbirini dışlıyor.|

Aşağıda, uygulama yapılandırma dosyasında depolanan [AdventureWorks Sales modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) için bir bağlantı dizesi örneği verilmiştir:

## <a name="model-and-mapping-file-locations"></a>Dosya konumlarını model ve eşleme

`Metadata` parametresi, `EntityClient` sağlayıcının model ve eşleme dosyalarını aramasını sağlayan konumların bir listesini içerir. Model ve eşleme dosyaları genellikle uygulama yürütülebilir dosyasıyla aynı dizine dağıtılır. Bu dosyalar Ayrıca belirli bir konuma dağıtılabilir veya uygulamaya eklenmiş bir kaynak olarak dahil edilebilir.

Katıştırılmış kaynaklar aşağıdaki gibi belirtilir:

`Metadata=res://<assemblyFullName>/<resourceName>`

Katıştırılmış bir kaynağın konumunu tanımlamak için aşağıdaki seçenekler kullanılabilir:

|Seçenek|Açıklama|
|-|-|
|`assemblyFullName`|Gömülü kaynağa sahip bir derlemenin tam adı. Ad, şu şekilde basit ad, sürüm adı, desteklenen kültür ve ortak anahtarı içerir:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Kaynaklar, uygulama tarafından erişilebilen herhangi bir derlemeye gömülebilir.<br /><br /> `assemblyFullName`için bir joker karakter (\*) belirtirseniz, Entity Framework çalışma zamanı aşağıdaki konumlarda yer alacak kaynakları şu sırayla arar:<br /><br /> 1. çağıran derleme.<br />2. başvurulan derlemeler.<br />3. bir uygulamanın bin dizinindeki derlemeler.<br /><br /> Dosyalar bu konumlardan birinde değilse, bir özel durum oluşturulur. **Note:**  Joker karakter (*) kullandığınızda Entity Framework, doğru ada sahip kaynaklar için tüm derlemelere bakmamız gerekir. Performansı artırmak için, joker karakter yerine derleme adını belirtin.|
|`resourceName`|Dahil edilen kaynağın adı, örneğin AdventureWorksModel. csdl. Meta veri Hizmetleri yalnızca şu uzantılardan birine sahip dosyaları veya kaynakları arayacaktır:. csdl,. ssdl veya. msl. `resourceName` belirtilmemişse, tüm meta veri kaynakları yüklenir. Kaynaklar bir bütünleştirilmiş kod içinde benzersiz adlara sahip olmalıdır. Derlemedeki farklı dizinlerde aynı ada sahip birden çok dosya tanımlanırsa `resourceName`, kaynak adından önce klasör yapısını içermelidir, örneğin KlasörAdı. FileName. csdl.<br /><br /> `assemblyFullName`için bir joker karakter (*) belirttiğinizde `resourceName` gerekli değildir.|

> [!NOTE]
> Performansı artırmak için, çağıran derlemede temel eşleme ve meta veri dosyalarına başvuru olmayan Web dışındaki senaryolar dışında, çağırma derlemesine kaynakları ekleyin.

Aşağıdaki örnek, bir uygulamanın bin dizinindeki çağıran derlemede, başvurulan derlemelerde ve diğer derlemelerde bulunan tüm model ve eşleme dosyalarını yükler.

```csharp
Metadata=res://*/
```

Aşağıdaki örnek, AdventureWorks derlemesinden model. csdl dosyasını yükler ve model. ssdl ve model. MSL dosyalarını çalışan uygulamanın varsayılan dizininden yükler.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

Aşağıdaki örnek, belirli bir derlemeden belirtilen üç kaynağı yükler.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

Aşağıdaki örnek, derleme içindeki. csdl,. msl ve. SSDL uzantılı tüm eklenmiş kaynakları yükler.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

Aşağıdaki örnek, göreli dosya yolundaki tüm kaynakları ve yüklenen derleme konumundan "datadir\metadata\\" yükler.

```csharp
Metadata=datadir\metadata\
```

Aşağıdaki örnek, yüklenen derleme konumundan göreli dosya yolundaki tüm kaynakları yükler.

```csharp
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>&#124;DataDirectory&#124; değiştirme dizesi ve Web uygulaması kök işleci (~) için destek

`DataDirectory` ve ~ işleci, `Metadata` ve `Provider Connection String` anahtar sözcüklerinin bir parçası olarak <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> kullanılır. <xref:System.Data.EntityClient.EntityConnection>, `DataDirectory` ve ~ işlecini sırasıyla <xref:System.Data.Metadata.Edm.MetadataWorkspace> ve mağaza sağlayıcısına iletir.

|Terim|Açıklama|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Eşleme ve meta veri dosyaları için göreli bir yol olarak çözümleniyor. Bu, `AppDomain.SetData("DataDirectory", objValue)` yöntemiyle ayarlanan değerdir. `DataDirectory` değiştirme dizesi kanal karakterleriyle çevrelenmeli ve adı ile kanal karakterleri arasında boşluk olamaz. `DataDirectory` adı büyük/küçük harfe duyarlı değildir.<br /><br /> "DataDirectory" adlı bir fiziksel dizinin meta veri yolları listesinin bir üyesi olarak geçirilmesi gerekiyorsa, adın birine veya her ikisine de boşluk ekleyin. Örneğin: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Bir ASP.NET uygulaması, &#124;veri dizinini&#124; "\<Application Root >/App_Data" klasörüne çözümler.|
|~|Web uygulaması kökünü çözümler. Baştaki konumdaki ~ karakteri her zaman Web uygulaması kök işleci (~) olarak yorumlanır, ancak geçerli bir yerel alt dizin temsil edebilir. Bu tür bir yerel alt dizine başvurmak için, kullanıcının `./~`açıkça geçmesi gerekir.|

`DataDirectory` ve ~ işleci yalnızca bir yolun başında belirtilmelidir, diğer herhangi bir konumda çözümlenmez. Entity Framework `~/data`çözmeye çalışacaktır, ancak `/data/~` fiziksel bir yol olarak değerlendirilir.

`DataDirectory` veya ~ işleci ile başlayan bir yol, `DataDirectory` dalı dışındaki bir fiziksel yola çözümlenemiyor ve ~ işleci. Örneğin, şu yollar çözülecek: `~`, `~/data`, `~/bin/Model/SqlServer`. Aşağıdaki yollar çözümlenmeyecektir: `~/..`, `~/../other`.

`DataDirectory` ve ~ işleci aşağıdaki gibi alt dizinleri içerecek şekilde genişletilebilir: `|DataDirectory|\Model`, `~/bin/Model`

`DataDirectory` değiştirme dizesinin ve ~ işlecinin çözümlenmesi özyinelemeli değil. Örneğin, `DataDirectory` `~` karakteri içerdiğinde bir özel durum oluşur. Bu, sonsuz özyineleme yapılmasını önler.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sağlayıcılarıyla Çalışma](working-with-data-providers.md)
- [Dağıtım Konuları](deployment-considerations.md)
- [Bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Bağlantı Dizeleri](../connection-strings.md)
