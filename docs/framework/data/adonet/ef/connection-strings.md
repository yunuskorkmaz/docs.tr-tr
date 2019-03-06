---
title: Bağlantı dizeleri ADO.NET varlık çerçevesi
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 55097e4977111c56cb06c590e305e31ed681fd31
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365041"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>Bağlantı dizeleri ADO.NET varlık çerçevesi

Bir bağlantı dizesi, bir veri kaynağı için veri sağlayıcısı'ndan bir parametre olarak geçen başlatma bilgileri içerir. Veri sağlayıcısında söz dizimi bağlıdır ve bağlantı dizesini bağlantı denemesi sırasında ayrıştırılır. Entity Framework tarafından kullanılan bağlantı dizeleri, Entity Framework'ü destekleyen temel alınan ADO.NET veri sağlayıcısına bağlanmak için kullanılan bilgileri içerir. Ayrıca gerekli model ve eşleme dosyaları hakkındaki bilgileri içerirler.

Bağlantı dizesi model ve eşleme meta veri erişirken EntityClient sağlayıcı tarafından kullanılır ve veri kaynağına bağlanma. Bağlantı dizesi erişilen veya aracılığıyla ayarlanan <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> özelliği <xref:System.Data.EntityClient.EntityConnection>. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Sınıfı, program aracılığıyla oluşturmak veya bağlantı dizesindeki parametreleri erişmek için kullanılabilir. Daha fazla bilgi için [nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).

[Varlık veri modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) uygulamanın yapılandırma dosyasında depolanan bir bağlantı dizesi oluşturur. <xref:System.Data.Objects.ObjectContext> Bu bağlantı bilgisini nesne sorgularını oluşturulurken otomatik olarak alır. <xref:System.Data.EntityClient.EntityConnection> Tarafından kullanılan bir <xref:System.Data.Objects.ObjectContext> örneği erişilebilir <xref:System.Data.Objects.ObjectContext.Connection%2A> özelliği. Daha fazla bilgi için [bağlantılarını yönetme ve işlemleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Bağlantı dizesi söz dizimi

Bağlantı dizeleri için genel sözdizimi hakkında daha fazla bilgi edinmek için [bağlantı dizesi söz dizimi | ADO.NET bağlantı dizelerini](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Bağlantı dizesi parametreleri

Geçerli adlar için anahtar sözcüğü değerleri aşağıdaki tabloda listelenmektedir <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.

|Anahtar sözcüğü|Açıklama|
|-------------|-----------------|
|`Provider`|Gerekli if `Name` anahtar belirtilmedi. Almak için kullanılan sağlayıcı adı <xref:System.Data.Common.DbProviderFactory> alttaki sağlayıcı nesnesi. Bu değer sabittir.<br /><br /> Zaman `Name` anahtar sözcüğü boş olmayan bir değer için bir varlık bağlantı dizesine dahil değildir `Provider` anahtar sözcüğü gereklidir. Bu anahtar sözcüğü ile birbirini dışlayan `Name` anahtar sözcüğü.|
|`Provider Connection String`|İsteğe bağlı. Temel alınan veri kaynağına geçirilen sağlayıcıya özgü bağlantı dizesini belirtir. Bu bağlantı dizesi için veri sağlayıcısı geçerli anahtar/değer çiftleri içerir. Geçersiz bir `Provider Connection String` veri kaynağı tarafından değerlendirilirken bir çalışma zamanı hatasına neden olur.<br /><br /> Bu anahtar sözcüğü ile birbirini dışlayan `Name` anahtar sözcüğü.<br /><br /> Değerine göre genel sözdizimi kaçış emin [ADO.NET bağlantı dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md). Örneğin, aşağıdaki bağlantı dizesi göz önünde bulundurun: `Server=serverName; User ID = userID`. Noktalı virgül içerdiğinden kaçınılmalıdır. Çift tırnak işareti içermediğinden, kaçış için kullanılabilir:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|Gerekli if `Name` anahtar belirtilmedi. Dizinleri, dosyaları ve meta verileri ve eşleme bilgileri aramak kaynak konumlarını kanal ayrılmış listesi. Bir örnek verilmiştir:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Kanal ayırıcı her iki tarafında boşluk yoksayılır.<br /><br /> Bu anahtar sözcüğü ile birbirini dışlayan `Name` anahtar sözcüğü.|
|`Name`|Uygulama, isteğe bağlı olarak gerekli anahtar/değer bağlantı dizesi değerleri sağlayan bir uygulama yapılandırma dosyasında bağlantı adı belirtebilirsiniz. Bu durumda, bunları doğrudan bağlantı dizesinde sağlayamazsınız. `Name` Anahtar sözcüğü bir yapılandırma dosyasında izin verilmez.<br /><br /> Zaman `Name` sağlayıcı anahtar sözcüğü için boş olmayan değerler, bağlantı dizesinde anahtar sözcüğü dahil değildir.<br /><br /> Bu anahtar sözcük tüm diğer bağlantı dizesi anahtar sözcükler birbirini dışlayan.|

Bir bağlantı dizesi örneği verilmiştir [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) uygulama yapılandırma dosyasında depolanan:

## <a name="model-and-mapping-file-locations"></a>Model ve eşleme dosyası konumları

`Metadata` Parametresi için konumların bir listesini içeren `EntityClient` model ve eşleme dosyalarını aramak için sağlayıcı. Model ve eşleme dosyalarını uygulama yürütülebilir dosyasıyla aynı dizinde genellikle dağıtılır. Bu dosyalar ayrıca dağıtılan belirli bir konumda veya katıştırılmış bir kaynağı uygulama dahil.

Gömülü kaynaklar gibi belirtilir:

```
Metadata=res://<assemblyFullName>/<resourceName>.
```

Katıştırılmış bir kaynağı konumunu tanımlamak için aşağıdaki seçenekler kullanılabilir:

|Seçenek|Açıklama|
|-|-|
|`assemblyFullName`|Katıştırılmış kaynak ile bir bütünleştirilmiş kodun tam adı. Adı basit bir ad, sürüm adı, desteklenen bir kültür ve ortak anahtarı içerir. Bunlar:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Kaynakları, uygulama tarafından erişilebilen herhangi bir derleme eklenebilir.<br /><br /> Joker karakter belirtirseniz (\*) için `assemblyFullName`, Entity Framework çalışma zamanı kaynakları aşağıdaki konumlarda şu sırayla arar:<br /><br /> 1.  Çağrıyı yapan derlemeyi.<br />2.  Başvurulan bütünleştirilmiş kodları.<br />3.  Bir uygulamanın depo dizini içindeki derlemeler.<br /><br /> Dosyaların bu konumlardan birinde değilseniz, bir özel durum oluşturulur. **Not:**  Joker karakter (*) kullandığınızda, Entity Framework kaynakları doğru ada sahip tüm derlemelerde göz gerekir. Performansı artırmak için joker karakter yerine derleme adı belirtin.|
|`resourceName`|AdventureWorksModel.csdl gibi birlikte kaynağın adı. Meta Veri Hizmetleri dosyaları veya aşağıdaki uzantılara sahip kaynaklar için yalnızca görünür: .csdl, .ssdl veya .msl. Varsa `resourceName` belirtilmezse, tüm meta veri kaynakları yüklenemedi. Kaynaklar derleme içinde benzersiz adlara sahip olmalıdır. Aynı ada sahip birden çok dosyayı derleme farklı dizinlerde tanımlanmışsa `resourceName` klasör yapısını kaynak, örneğin FolderName.FileName.csdl adından önce içermelidir.<br /><br /> `resourceName` joker karakter (*) belirttiğinizde için gerekli değildir `assemblyFullName`.|

> [!NOTE]
> Performansı artırmak için çağrıyı yapan derlemeyi kaynaklarında dışındaki Web olmayan senaryolarda ekleme çağıran derlemeye temel eşleme ve meta veri dosyalarında başvuru olduğu.

Aşağıdaki örnek, tüm model ve eşleme dosyalarını çağıran derlemeye, başvurulan derlemeleri ve diğer derlemeler uygulamasının bin dizinine yükler.

```
Metadata=res://*/
```

Aşağıdaki örnekte, AdventureWorks derlemeden model.csdl dosyayı yükler ve çalışan uygulamanın varsayılan dizinden model.ssdl ve model.msl dosyalarını yükler.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

Aşağıdaki örnek, üç belirtilen kaynak belirli bütünleştirilmiş koddan yükler.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

Aşağıdaki örnek, derlemeden gömülü kaynaklar uzantıları .csdl, .msl ve .ssdl yükler.

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

Aşağıdaki örnekte tüm kaynakların göreli dosya yolu artı yükler "datadir\metadata\\" konumundan yüklenen derleme.

```
Metadata=datadir\metadata\
```

Aşağıdaki örnekte tüm kaynakların göreli dosya yolu yüklenen derleme konumundan yükler.

```
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Destek &#124;DataDirectory&#124; değiştirme dizesi ve Web uygulaması kök işleci (~)

`DataDirectory` ve ~ işleci kullanıldığı <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> parçası olarak `Metadata` ve `Provider Connection String` anahtar sözcükleri. <xref:System.Data.EntityClient.EntityConnection> İletir `DataDirectory` ve ~ işleci <xref:System.Data.Metadata.Edm.MetadataWorkspace> ve depo sağlayıcı, sırasıyla.

|Terim|Açıklama|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Bir eşleme ve meta veri dosyaları için göreli bir yola çözümler. Aracılığıyla ayarlanan değer budur `AppDomain.SetData("DataDirectory", objValue)` yöntemi. `DataDirectory` Kanal karakterlerinin değiştirme dizesi çevrelenmiş ve adını kanal karakterler arasındaki tüm boşluk olamaz. `DataDirectory` Adı büyük küçük harfe duyarlı değil.<br /><br /> Meta veri yollarının listesini bir üyesi olarak geçirilecek "DataDirectory" adlı fiziksel bir dizin varsa, ad veya her iki tarafının için boşluk ekleyin. Örneğin: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"` Bir ASP.NET uygulaması çözümler &#124;DataDirectory&#124; için "\<uygulama kökü > / app_data" klasörü.|
|~|Web uygulaması kök dizinine çözümler. ~ Lider konumda karakter her zaman Web uygulaması kök işleci yorumlanır (~), geçerli bir yerel alt gösterebilir ancak. Böyle bir yerel alt dizinine başvurmak için kullanıcıyı açıkça geçmelidir `./~`.|

`DataDirectory` ve ~ işleci yalnızca bir yol başında belirtilmelidir, bunlar başka bir konumda çözümlenmiyor. Entity Framework çözmeye `~/data`, ancak bunu değerlendirir `/data/~` fiziksel yol.

İle başlayan yol `DataDirectory` ya da ~ işleci, bir fiziksel yola dalını dışında çözümleyemiyor `DataDirectory` ve ~ işleci. Örneğin, aşağıdaki yollardan çözer: `~` , `~/data` , `~/bin/Model/SqlServer`. Aşağıdaki yolları çözümlemek başarısız olur: `~/..`, `~/../other`.

`DataDirectory` ve ~ işleci uzatabilirsiniz alt dizinleri şu şekilde eklenecek: `|DataDirectory|\Model`, `~/bin/Model`

Çözümlenmesi `DataDirectory` değiştirme dizesi ve ~ yinelemesiz işlecidir. Örneğin, `DataDirectory` içerir `~` karakter, bir özel durum oluşur. Bu, sonsuz özyineleme durumuna yol engeller.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sağlayıcılarıyla Çalışma](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
- [Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Bağlantılarını yönetme ve işlemler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)
