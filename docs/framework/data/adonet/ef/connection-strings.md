---
title: "Bağlantı dizeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b141f7bb31374c403f8d802a5df2ff1329b1e079
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="connection-strings"></a>Bağlantı dizeleri
Bir bağlantı dizesi, parametre olarak bir veri kaynağına veri sağlayıcıdan geçen başlatma bilgileri içerir. Sözdizimi veri sağlayıcısına bağlıdır ve bağlantı dizesini bir bağlantı açmak için girişimi sırasında ayrıştırılır. Entity Framework tarafından kullanılan bağlantı dizeleri Entity Framework destekleyen temel ADO.NET veri sağlayıcısına bağlanmak için kullanılan bilgileri içerir. Ayrıca gerekli modeli ve eşleme dosyaları hakkındaki bilgileri içerir.  
  
 Bağlantı dizesi modeli ve eşleme meta veri erişirken EntityClient sağlayıcı tarafından kullanılır ve veri kaynağına bağlanma. Bağlantı dizesi erişilen veya aracılığıyla ayarlanabilir <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> özelliği <xref:System.Data.EntityClient.EntityConnection>. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Sınıfı, programlı olarak oluşturmanıza veya bağlantı dizesi parametrelerinde erişmek için kullanılabilir. Daha fazla bilgi için bkz: [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
 [Varlık veri modeli Araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) uygulamanın yapılandırma dosyasında depolanan bağlantı dizesi oluşturun. <xref:System.Data.Objects.ObjectContext>Bu bağlantı bilgisini nesne sorgular oluştururken otomatik olarak alır. <xref:System.Data.EntityClient.EntityConnection> Tarafından kullanılan bir <xref:System.Data.Objects.ObjectContext> örneği erişilebilir gelen <xref:System.Data.Objects.ObjectContext.Connection%2A> özelliği. Daha fazla bilgi için bkz: [bağlantıları yönetme ve işlemleri](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="connection-string-parameters"></a>Bağlantı dizesi parametreleri  
 Bir bağlantı dizesi biçimi anahtar/değer parametresi çifti noktalı virgülle ayrılmış bir listesi verilmiştir:  
  
 `keyword1=value; keyword2=value;`  
  
 Her anahtar sözcüğü ve değerine eşittir (=) bağlanır. Anahtar sözcükler büyük küçük harfe duyarlı değildir ve anahtar/değer çiftleri arasındaki boşluklar yok sayılır. Ancak, değerler büyük veri kaynağı bağlı olarak küçük harf duyarlı, olabilir. Noktalı virgül, tek tırnak işareti veya çift tırnak işaretleri içeren herhangi bir değeri çift tırnak içine alınmalıdır. Geçerli adlar anahtar sözcüğü değerleri aşağıdaki tabloda listelenmektedir <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`Provider`|Gerekli olursa `Name` anahtar sözcüğü belirtilmedi. Almak için kullanılan sağlayıcı adı <xref:System.Data.Common.DbProviderFactory> temel alınan sağlayıcı nesnesi. Bu değer sabittir.<br /><br /> Zaman `Name` anahtar sözcüğü dahil değil bir varlık bağlantı dizesi için bir boş değer `Provider` anahtar sözcüğü gereklidir. Bu anahtar sözcüğü ile birbirini dışlayan `Name` anahtar sözcüğü.|  
|`Provider Connection String`|İsteğe bağlı. Temel alınan veri kaynaklarına geçirilen sağlayıcıya özgü bağlantı dizesini belirtir. Bu bağlantı dizesi geçerli bir anahtar/değer çiftleri için veri sağlayıcısı kullanarak ifade edilir. Geçersiz bir `Provider Connection String` veri kaynağı tarafından değerlendirildiğinde bir çalışma zamanı hatası neden olur.<br /><br /> Bu anahtar sözcüğü ile birbirini dışlayan `Name` anahtar sözcüğü.<br /><br /> Değeri `Provider Connection String` tırnak içine alınmalıdır. Bir örnek verilmiştir:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`<br /><br /> Aşağıdaki örnek iş gonna:<br /><br /> `Provider Connection String =Server=serverName; User ID = userID`|  
|`Metadata`|Gerekli olursa `Name` anahtar sözcüğü belirtilmedi. Dizinleri, dosyaları ve ilgili meta verileri ve eşleme bilgilerini aramak üzere kaynak konumları kanal ayrılmış listesi. Bir örnek verilmiştir:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Kanal ayırıcı her iki tarafında boş alanları göz ardı edilir.<br /><br /> Bu anahtar sözcüğü ile birbirini dışlayan `Name` anahtar sözcüğü.|  
|`Name`|Uygulama, isteğe bağlı olarak gerekli anahtar/değer bağlantı dizesi değerleri sağlayan bir uygulama yapılandırma dosyasında bağlantı adı belirtebilirsiniz. Bu durumda, bunları doğrudan bağlantı dizesinde sağlayamazsınız. `Name` Anahtar sözcüğü bir yapılandırma dosyasında izin verilmez.<br /><br /> Zaman `Name` bağlantı dizesinde anahtar sözcüğü dahil değildir, sağlayıcı anahtar sözcüğü gereklidir boş olmayan değerler.<br /><br /> Bu anahtar sözcük tüm diğer bağlantı dizesi anahtar ile karşılıklı olarak birbirini dışlar.|  
  
 Bir bağlantı dizesi örneği verilmiştir [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) uygulama yapılandırma dosyasında depolanır:  
  
  
  
## <a name="model-and-mapping-file-locations"></a>Model ve dosya konumları eşleme  
 `Metadata` Parametresi için konumların bir listesini içeren `EntityClient` modeli ve eşleme dosyaları aramak için sağlayıcı. Model ve eşleme dosyaları çoğunlukla uygulama yürütülebilir dosyası ile aynı dizinde dağıtılır. Bu dosyalar da belirli bir konumda dağıtılan veya uygulamada katıştırılmış bir kaynağı olarak eklenecek.  
  
 Gömülü kaynaklar gibi belirtilir:  
  
```  
Metadata=res://<assemblyFullName>/<resourceName>.   
```  
  
 Katıştırılmış bir kaynağı konumunu tanımlamak için aşağıdaki seçenekler kullanılabilir:  
  
|Seçenek|Açıklama|  
|-|-|  
|`assemblyFullName`|Katıştırılmış kaynak ile bir derlemeyi tam adı. Adı gibi basit bir ad, sürüm adı, desteklenen bir kültür ve ortak anahtarı içerir:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Kaynaklar uygulama tarafından erişilebilen herhangi bir derlemede katıştırılabilir.<br /><br /> Joker karakter belirtirseniz (\*) için `assemblyFullName`, Entity Framework çalışma zamanı kaynakların bu sırada aşağıdaki konumlarda arar:<br /><br /> 1.  Çağrıyı yapan derlemeyi.<br />2.  Başvurulan derlemeler.<br />3.  Bir uygulamanın bin dizinindeki derlemeler.<br /><br /> Dosyaları aşağıdaki konumlardan birinde değilse, bir özel durum. **Not:** joker karakter (*) kullandığınızda, doğru ada sahip kaynaklar için tüm derlemeler üzerinden aramak Entity Framework sahiptir. Performansı artırmak için joker karakter yerine derleme adı belirtin.|  
|`resourceName`|AdvendtureWorksModel.csdl gibi birlikte kaynağın adı. Meta Veri Hizmetleri yalnızca dosyaları ve kaynakları aşağıdaki uzantılardan birine sahip arar: .csdl, .ssdl veya .msl. Varsa `resourceName` belirtilmezse, tüm meta veri kaynakları yüklenecek. Kaynakları bir derlemeyi içinde benzersiz adlara sahip olmalıdır. Aynı ada sahip birden fazla dosya derleme farklı dizinlerde tanımlanmışsa, `resourceName` kaynağının adını, örneğin FolderName.FileName.csdl önce klasör yapısı eklemeniz gerekir.<br /><br /> `resourceName`joker karakter (*) belirttiğinizde için gerekli değildir `assemblyFullName`.|  
  
> [!NOTE]
>  Performansı artırmak için çağrıyı yapan derlemeyi kaynaklarında dışında Web olmayan senaryolarda katıştırmak hiçbir başvurusu çağrıyı yapan derlemeyi temel eşleme ve meta veri dosyalarında olduğu.  
  
 Aşağıdaki örnek, modeli ve çağrıyı yapan derlemeyi, başvurulan derlemeler ve bir uygulamanın bin dizinindeki diğer derlemelerden eşleme dosyaları yükler.  
  
```  
Metadata=res://*/  
```  
  
 Aşağıdaki örnek, AdventureWorks derlemesinden model.csdl dosyasını yükler ve çalışan uygulama varsayılan dizinden model.ssdl ve model.msl dosyalarını yükler.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl  
```  
  
 Aşağıdaki örnekte, üç belirtilen kaynaklar belirli derlemeden yükler.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|   
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|   
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl  
```  
  
 Aşağıdaki örnekte tüm katıştırılmış kaynakları uzantıları .csdl, .msl ve .ssdl derlemeden yükler.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/  
```  
  
 Aşağıdaki örnek artı göreli dosya yolu tüm kaynakları yükler "datadir\metadata\\" yüklenen derleme konumdan.  
  
```  
Metadata=datadir\metadata\  
```  
  
 Aşağıdaki örnek yüklenen derleme konumundan göreli dosya yolu tüm kaynakları yükler.  
  
```  
Metadata=.\  
```  
  
## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Desteği &#124; DataDirectory &#124; Değiştirme dizesi ve Web uygulaması kök işleci (~)  
 `DataDirectory`ve ~ işleci kullanıldığı <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> parçası olarak `Metadata` ve `Provider Connection String` anahtar sözcükler. <xref:System.Data.EntityClient.EntityConnection> İletir `DataDirectory` ve ~ işleci <xref:System.Data.Metadata.Edm.MetadataWorkspace> ve depo sağlayıcısı sırasıyla.  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`&#124;DataDirectory&#124;`|Bir eşleme ve meta veri dosyaları için göreli bir yol çözümler. Bu aracılığıyla ayarlanan değerdir `AppDomain.SetData("DataDirectory", objValue)` yöntemi. `DataDirectory` Kanal karakterleriyle değiştirme dizesi çevrelenen ve adını ve kanal karakter arasında bir boşluk olamaz. `DataDirectory` Adı büyük küçük harfe duyarlı değil.<br /><br /> Boşluk gereken yan ya da iki tarafı da adı, örneğin "DataDirectory" adlı bir fiziksel dizini meta verileri yollar listesi bir üyesi olarak geçirilecek varsa, ekleyebilir: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Bir ASP.NET uygulaması çözümler &#124; DataDirectory &#124; için "\<uygulama kökü > / app_data" klasörü.|  
|~|Web uygulaması kök çözümler. ~ Geçerli bir yerel alt gösterebilir rağmen başında konumunda karakter Web uygulaması kök işleci (~) her zaman yorumlanır. İçin yerel alt başvurmak için kullanıcı açıkça geçirmelisiniz `./~`.|  
  
 `DataDirectory`ve ~ işleci yalnızca bir yol başında belirtilmelidir, bunlar başka bir konumda çözümlenmeyen. Entity Framework çözümlemeye çalışır `~/data`, ancak kabul eder `/data/~` fiziksel bir yol olarak.  
  
 İle başlayan bir yol `DataDirectory` veya ~ işleci dalı dışında fiziksel bir yola çözmek olamaz `DataDirectory` ve ~ işleci. Örneğin, aşağıdaki yollardan çözer: `~` , `~/data` , `~/bin/Model/SqlServer`. Aşağıdaki yolları çözümlemek başarısız olur: `~/..`, `~/../other`.  
  
 `DataDirectory`ve ~ işleci uzatabilirsiniz. alt dizinlerde, aşağıdaki gibi eklemek için: `|DataDirectory|\Model`,`~/bin/Model`  
  
 Çözünürlüğünü `DataDirectory` değiştirme dizesi ve ~ özyinelemeli olmayan işlecidir. Örneğin, `DataDirectory` içeren `~` karakter, bir özel durum meydana gelir. Sonsuz özyineleme engeller.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri sağlayıcıları ile çalışma](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)  
 [Dağıtım konuları](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Bağlantılarını yönetme ve işlemler](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [Bağlantı dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)
