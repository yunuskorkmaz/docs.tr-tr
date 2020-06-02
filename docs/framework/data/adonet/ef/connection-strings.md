---
title: ADO.NET Entity Framework bağlantı dizeleri
description: ADO.NET veri sağlayıcısına bağlanmak ve model ve eşleme dosyaları hakkında bilgi içeren Entity Framework bağlantı dizeleri hakkında bilgi edinin.
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 2ae25f5881c033a84d65f5b0b4ed14b4866dbcb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286876"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>ADO.NET Entity Framework bağlantı dizeleri

Bir bağlantı dizesi, veri sağlayıcısından bir veri kaynağına parametre olarak geçirilen başlatma bilgilerini içerir. Söz dizimi veri sağlayıcısına bağlıdır ve bağlantı dizesi bir bağlantıyı açma denemesi sırasında ayrıştırılır. Entity Framework tarafından kullanılan bağlantı dizeleri, Entity Framework destekleyen temel alınan ADO.NET veri sağlayıcısına bağlanmak için kullanılan bilgileri içerir. Ayrıca gerekli model ve eşleme dosyaları hakkında bilgiler içerir.

Bağlantı dizesi, model ve eşleme meta verilerine erişirken ve veri kaynağına bağlanırken EntityClient sağlayıcı tarafından kullanılır. Bağlantı dizesine erişilebilir veya özelliği aracılığıyla ayarlanabilir <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> <xref:System.Data.EntityClient.EntityConnection> . <xref:System.Data.EntityClient.EntityConnectionStringBuilder>Sınıfı, bağlantı dizesinde programlı olarak parametreler oluşturmak veya erişmek için kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](how-to-build-an-entityconnection-connection-string.md).

[Varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) , uygulamanın yapılandırma dosyasında depolanan bir bağlantı dizesi oluşturur. <xref:System.Data.Objects.ObjectContext>nesne sorguları oluştururken bu bağlantı bilgilerini otomatik olarak alır. <xref:System.Data.EntityClient.EntityConnection>Bir örnek tarafından kullanılan <xref:System.Data.Objects.ObjectContext> <xref:System.Data.Objects.ObjectContext.Connection%2A> özelliği özelliğinden erişilebilir. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi

Bağlantı dizelerine ilişkin genel söz dizimi hakkında bilgi edinmek için bkz. [bağlantı dizesi sözdizimi | ADO.NET içinde bağlantı dizeleri](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Bağlantı dizesi parametreleri

Aşağıdaki tabloda, içindeki anahtar sözcük değerleri için geçerli adlar listelenmektedir <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> .

|Sözcükle|Description|
|-------------|-----------------|
|`Provider`|`Name`Anahtar sözcüğü belirtilmemişse gereklidir. Temel sağlayıcı için nesneyi almak için kullanılan sağlayıcı adı <xref:System.Data.Common.DbProviderFactory> . Bu değer sabittir.<br /><br /> `Name`Anahtar sözcüğü bir varlık bağlantı dizesinde yer olmadığında, anahtar sözcük için boş olmayan bir değer `Provider` gerekir. Bu anahtar sözcük, anahtar sözcüğüyle birbirini dışlıyor `Name` .|
|`Provider Connection String`|İsteğe bağlı. Temel alınan veri kaynağına geçirilen sağlayıcıya özel bağlantı dizesini belirtir. Bu bağlantı dizesi, veri sağlayıcısı için geçerli anahtar sözcük/değer çiftleri içeriyor. Geçersiz bir `Provider Connection String` çalışma zamanı hatasına, veri kaynağı tarafından değerlendiriliyorsa neden olur.<br /><br /> Bu anahtar sözcük, anahtar sözcüğüyle birbirini dışlıyor `Name` .<br /><br /> [ADO.NET bağlantı dizelerinin](../connection-strings.md)genel sözdizimine göre değeri attığınızdan emin olun. Aşağıdaki bağlantı dizesini örnek olarak düşünün: `Server=serverName; User ID = userID` . Noktalı virgül içerdiğinden bunun kaçışlı olması gerekir. Çift tırnak işaretleri içermediğinden, bu, kaçış için kullanılabilir:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|`Name`Anahtar sözcüğü belirtilmemişse gereklidir. Meta veri ve eşleme bilgilerinin aranacağı Dizin, dosya ve kaynak konumlarının kanal ile ayrılmış listesi. Aşağıda bir örnek verilmiştir:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Kanal ayırıcısının her tarafında boş boşluklar yok sayılır.<br /><br /> Bu anahtar sözcük, anahtar sözcüğüyle birbirini dışlıyor `Name` .|
|`Name`|Uygulama isteğe bağlı olarak, gerekli anahtar sözcük/değer bağlantı dizesi değerlerini sağlayan bir uygulama yapılandırma dosyasında bağlantı adını belirtebilir. Bu durumda, bunları doğrudan bağlantı dizesinde sağlayamazsınız. `Name`Bir yapılandırma dosyasında anahtar sözcüğe izin verilmez.<br /><br /> `Name`Anahtar sözcüğü bağlantı dizesinde yer olmadığında, sağlayıcı anahtar sözcüğü için boş olmayan değerler gerekir.<br /><br /> Bu anahtar sözcük, diğer tüm bağlantı dizesi anahtar sözcükleriyle birbirini dışlıyor.|

Aşağıda, uygulama yapılandırma dosyasında depolanan [AdventureWorks Sales modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) için bir bağlantı dizesi örneği verilmiştir:

## <a name="model-and-mapping-file-locations"></a>Dosya konumlarını model ve eşleme

`Metadata`Parametresi, `EntityClient` sağlayıcının model ve eşleme dosyalarını aramasını sağlayan konumların bir listesini içerir. Model ve eşleme dosyaları genellikle uygulama yürütülebilir dosyasıyla aynı dizine dağıtılır. Bu dosyalar Ayrıca belirli bir konuma dağıtılabilir veya uygulamaya eklenmiş bir kaynak olarak dahil edilebilir.

Katıştırılmış kaynaklar aşağıdaki gibi belirtilir:

`Metadata=res://<assemblyFullName>/<resourceName>`

Katıştırılmış bir kaynağın konumunu tanımlamak için aşağıdaki seçenekler kullanılabilir:

|Seçenek|Description|
|-|-|
|`assemblyFullName`|Gömülü kaynağa sahip bir derlemenin tam adı. Ad, şu şekilde basit ad, sürüm adı, desteklenen kültür ve ortak anahtarı içerir:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Kaynaklar, uygulama tarafından erişilebilen herhangi bir derlemeye gömülebilir.<br /><br /> İçin bir joker karakter ( \* ) belirtirseniz `assemblyFullName` , Entity Framework çalışma zamanı aşağıdaki konumlarda bulunan kaynakları şu sırayla arar:<br /><br /> 1. çağıran derleme.<br />2. başvurulan derlemeler.<br />3. bir uygulamanın bin dizinindeki derlemeler.<br /><br /> Dosyalar bu konumlardan birinde değilse, bir özel durum oluşturulur. **Note:**  Joker karakter (*) kullandığınızda Entity Framework, doğru ada sahip kaynaklar için tüm derlemelere bakmamız gerekir. Performansı artırmak için, joker karakter yerine derleme adını belirtin.|
|`resourceName`|Dahil edilen kaynağın adı, örneğin AdventureWorksModel. csdl. Meta veri Hizmetleri yalnızca şu uzantılardan birine sahip dosyaları veya kaynakları arayacaktır:. csdl,. ssdl veya. msl. `resourceName`Belirtilmezse, tüm meta veri kaynakları yüklenir. Kaynaklar bir bütünleştirilmiş kod içinde benzersiz adlara sahip olmalıdır. Aynı ada sahip birden çok dosya derlemede farklı dizinlerde tanımlanmazsa, `resourceName` kaynak adından önce klasör yapısını içermelidir, örneğin KlasörAdı. FileName. csdl.<br /><br /> `resourceName`için bir joker karakter (*) belirttiğinizde gerekli değildir `assemblyFullName` .|

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

Aşağıdaki örnek, göreli dosya yolundaki tüm kaynakları, yüklenen derleme konumundan "datadir\metadata" ile birlikte yükler \\ .

```csharp
Metadata=datadir\metadata\
```

Aşağıdaki örnek, yüklenen derleme konumundan göreli dosya yolundaki tüm kaynakları yükler.

```csharp
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>&#124;DataDirectory&#124; değiştirme dizesi ve Web uygulaması kök Işleci (~) için destek

`DataDirectory`ve ~ işleci, <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> `Metadata` ve anahtar sözcüklerinin bir parçası olarak ' de kullanılır `Provider Connection String` . , <xref:System.Data.EntityClient.EntityConnection> `DataDirectory` Ve ~ işlecini <xref:System.Data.Metadata.Edm.MetadataWorkspace> sırasıyla ve depo sağlayıcısına iletir.

|Terim|Description|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Eşleme ve meta veri dosyaları için göreli bir yol olarak çözümleniyor. Bu, yöntemi aracılığıyla ayarlanan değerdir `AppDomain.SetData("DataDirectory", objValue)` . `DataDirectory`Değiştirme dizesi kanal karakterleriyle çevrelenmeli ve adı ile kanal karakterleri arasında boşluk olamaz. `DataDirectory`Ad, büyük/küçük harfe duyarlı değildir.<br /><br /> "DataDirectory" adlı bir fiziksel dizinin meta veri yolları listesinin bir üyesi olarak geçirilmesi gerekiyorsa, adın birine veya her ikisine de boşluk ekleyin. Örneğin: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Bir ASP.NET uygulaması, &#124;DataDirectory&#124; " \<application root> /App_Data" klasörüne çözümleniyor.|
|~|Web uygulaması kökünü çözümler. Baştaki konumdaki ~ karakteri her zaman Web uygulaması kök işleci (~) olarak yorumlanır, ancak geçerli bir yerel alt dizin temsil edebilir. Bu tür bir yerel alt dizine başvurmak için, kullanıcının açıkça geçmesi gerekir `./~` .|

`DataDirectory`~ işleci yalnızca bir yolun başlangıcında belirtilmelidir, bunlar başka bir konumda çözümlenmez. Entity Framework çözmeye çalışacaktır `~/data` , ancak `/data/~` fiziksel bir yol olarak değerlendirilir.

Or ~ işleci ile başlayan bir yol `DataDirectory` , `DataDirectory` ve ~ işlecinin dalı dışında bir fiziksel yola çözümlenemiyor. Örneğin, aşağıdaki yollar çözülecek: `~` , `~/data` , `~/bin/Model/SqlServer` . Aşağıdaki yollar çözemeyecektir: `~/..` , `~/../other` .

`DataDirectory`ve ~ işleci aşağıdaki gibi alt dizinleri içerecek şekilde `|DataDirectory|\Model` Genişletilebilir:`~/bin/Model`

`DataDirectory`Değiştirme dizesinin ve ~ işlecinin çözümlenmesi özyinelemeli değil. Örneğin, karakteri içerdiğinde `DataDirectory` `~` bir özel durum oluşur. Bu, sonsuz özyineleme yapılmasını önler.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sağlayıcılarıyla Çalışma](working-with-data-providers.md)
- [Dağıtım değerlendirmeleri](deployment-considerations.md)
- [Bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Bağlantı dizeleri](../connection-strings.md)
