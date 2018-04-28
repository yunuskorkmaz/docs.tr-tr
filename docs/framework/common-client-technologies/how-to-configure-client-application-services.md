---
title: 'Nasıl Yapılır: İstemci Uygulama Hizmetlerini Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8a6c6be6874c1a90c9e40b5b82d833aeaa9b63a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-client-application-services"></a>Nasıl Yapılır: İstemci Uygulama Hizmetlerini Yapılandırma
Bu konu, Visual Studio kullanmayı açıklar **Proje Tasarımcısı** etkinleştirmek ve istemci uygulama hizmetleri yapılandırmak için. İstemci uygulama Hizmetleri kullanıcıları doğrulamak ve mevcut bir kullanıcı rolleri ve ayarları almak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama hizmeti. Yapılandırmadan sonra etkin hizmetleri, uygulama kodunuzda açıklandığı gibi erişebilirsiniz [istemci uygulama hizmetlerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama bkz [ASP.NET uygulama hizmetleri genel bakış](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Etkinleştirme ve istemci uygulama Hizmetleri yapılandırmasına **Hizmetleri** sayfasında **Proje Tasarımcısı**. **Hizmetleri** sayfa projenizin App.config dosyasında değerlerini güncelleştirir. Erişim için **Proje Tasarımcısı**, kullanın **özellikleri** komutunu **proje** menüsü. Hakkında daha fazla bilgi için **Hizmetleri** sayfasında, bkz: [Hizmetler Sayfası, Proje Tasarımcısı](https://msdn.microsoft.com/library/bb398109).  
  
 Aşağıdaki yordam, istemci uygulama hizmetleri için temel yapılandırmayı gerçekleştirmek açıklar. Gelişmiş yapılandırma seçenekleri, sonraki bölümlerde açıklanmıştır.  
  
### <a name="to-configure-client-application-services"></a>İstemci uygulama hizmetleri yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından **proje** menüsünde tıklatın **özellikleri**.  
  
     **Proje Tasarımcısı** görüntülenir.  
  
2.  Tıklatın **Hizmetleri** sekmesi. **Hizmetleri** sayfası görüntülenirse, aşağıdaki çizimde gösterildiği gibi.  
  
     ![Proje Tasarımcısı'nda Hizmetler sekmesini](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Üzerinde **Hizmetleri** sayfasında, **etkinleştirmek istemci uygulama hizmetleri**.  
  
    > [!NOTE]
    >  İstemci uygulama hizmetleri .NET Framework'ün tam sürümünü gerektirir ve .NET Framework istemci profili desteklenmez. Varsa **etkinleştirmek istemci uygulama hizmetleri** onay kutusu devre dışıysa, doğrulayın **hedef framework** .NET Framework 3.5 veya daha üstüne ayarlanmalıdır. Görüntülemek için **hedef framework** C# ' ta ayarlama, Proje Tasarımcısı'nı açın ve ardından **uygulama** sayfası. Görüntülemek için **hedef framework** Visual Basic'te ayarlama, Proje Tasarımcısı açın, **derleme** sayfasında ve ardından **Gelişmiş derleme seçenekleri**.  
  
4.  Seçin **formlar kimlik doğrulaması** kendi oturum açma denetimleri veya iletişim kutusuna girin veya seçin planlıyorsanız **kullanan Windows kimlik doğrulaması** işletim sistemi tarafından sağlanan kimlik kullanmak üzere. Daha fazla bilgi için bkz: [istemci uygulama hizmetlerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  Seçerseniz **kullanan Windows kimlik doğrulaması**, istemci uygulama hizmetleri otomatik olarak yapılandırılacak bir SQL Server Compact veritabanını kullanmak için. Bu belirtilen **hizmetler için Gelişmiş ayarları** sonraki bölümde açıklandığı gibi iletişim kutusu. Ardından seçerseniz **formlar kimlik doğrulaması**, **özel bağlantı dizesini kullan** ayarı Temizlenmemiş otomatik olarak. Bu hatalar sonuçlanabilir [!INCLUDE[ssEW](../../../includes/ssew-md.md)] veritabanı zaten oluşturuldu Windows kimlik doğrulaması ile kullanım için. Bu hataları gidermek için temizleyin **özel bağlantı dizesini kullan** ayarı **hizmetler için Gelişmiş ayarları** iletişim kutusu.  
  
5.  Seçtiyseniz **formlar kimlik doğrulaması**, **kimlik doğrulama hizmeti konumu** kutusunda, dosya adı dahil değil hizmet ana bilgisayarı URL'sini belirtin. Değer yapılandırma dosyasına yazarken Tasarımcı standart dosya adı (Authentication_JSON_AppService.axd) otomatik olarak eklenir.  
  
6.  İsteğe bağlı olarak, seçtiyseniz **formlar kimlik doğrulaması**, bir değer belirtebilirsiniz **kimlik bilgileri sağlayıcısı** kutusu. Kimlik bilgileri sağlayıcısı uygulamalıdır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi. Bir kimlik sağlayıcısı kullanarak, oturum açma kullanıcı arabiriminizi diğer uygulama kodunuzdan ayırabilirsiniz. Bu bir tek oturum açma iletişim kutusu kullanım için birden çok uygulamalarda oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri ile uygulama kullanıcı oturum açma](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Bir kimlik sağlayıcısı belirtirseniz, bir bütünleştirilmiş kod tam tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için bkz: <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> ve [derleme adları](../../../docs/framework/app-domains/assembly-names.md). En basit biçimiyle bir bütünleştirilmiş kod tam tür adı aşağıdaki örneğe benzer:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  İçinde **rolleri hizmet konumu** ve **hizmet konumu Web ayarları** metin kutularında, dosya adı dahil değil, her hizmet için hizmet konumu belirtin. Tasarımcı standart dosya adları (Role_JSON_AppService.axd ve Profile_JSON_AppService.axd) otomatik olarak eklenir yapılandırma dosyasına değeri yazdığında.  
  
8.  İsteğe bağlı olarak, tıklayın **Gelişmiş** yerel önbelleğe alma davranışını gibi gelişmiş ayarları değiştirmek için. Daha fazla bilgi için sonraki yordama bakın.  
  
## <a name="advanced-configuration"></a>Gelişmiş Yapılandırma  
 Aşağıdaki yordamlar, daha az yaygın senaryolar için istemci uygulama hizmetlerini yapılandırma açıklanmaktadır. Örneğin, ortak konumlarda veya yerel veri önbelleği olarak şifrelenmiş bir SQL Server Compact veritabanı kullanmak için dağıtılan uygulamalar için bu yapılandırma seçeneklerini kullanabilirsiniz.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Gelişmiş istemci uygulama hizmetleri ayarlarını yapılandırmak için  
  
1.  Üzerinde **Hizmetleri** sayfasında **Proje Tasarımcısı**, tıklatın **Gelişmiş**.  
  
     **Hizmetler için Gelişmiş ayarları** iletişim kutusu görüntülenirse, aşağıdaki çizimde gösterildiği gibi. Bu iletişim kutusu hakkında daha fazla bilgi için bkz: [Hizmetleri iletişim kutusu için Gelişmiş ayarları](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Hizmetleri iletişim kutusu için Gelişmiş ayarları](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Seçin veya temizleyin **yerel olarak çevrimdışı oturum açma etkinleştirmek için parola karması kaydetmek**. Bu seçeneği belirlediğinizde, kullanıcının parolasının şifrelenmiş biçimde yerel olarak önbelleğe alınır. Bu, uygulamanız için çevrimdışı modda uygularsanız yararlı olur. Bu seçenek ile kullanıcılar doğrulamak için bile <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> özelliği ayarlanmış `true`.  
  
3.  Seçin veya temizleyin **sunucu tanımlama bilgisinin süresinin her tekrar oturum açmasını gerektiren**. Kimlik doğrulama tanımlama bilgisi uzak hizmet üzerindeki yapılandırılmış ve bir kullanıcı oturumunun ne kadar süreyle etkin kalacak gösterir. Tanımlama bilgisinin yapılandırma hakkında daha fazla bilgi için bkz: `timeout` özniteliğini [öğesi form kimlik doğrulamasını (ASP.NET Ayarlar Şeması) için](http://msdn.microsoft.com/library/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Uzak rolleri erişmeye çalışan bu seçeneği seçin ya da kimlik doğrulama tanımlama bilgisini dolan Web ayarları Hizmetleri oluşturur bir <xref:System.Net.WebException>. Bu özel durumu işlemek ve kullanıcıların düzeltin için bir oturum açma iletişim kutusu görüntüler. Bu davranış bir örnek için bkz: [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Bu seçenek, kullanım kalmaz sonra uygulama çalışır durumda bırakın kullanıcılar süresiz olarak authenticated emin olmak genel konumda dağıtılan uygulamalar için yararlıdır.  
  
     Bu seçenek ve kimlik doğrulama tanımlama bilgisini dolan uzak Hizmetleri erişmeye çalışırken işaretini kaldırırsanız, kullanıcıların otomatik olarak yeniden doğrulanır.  
  
4.  İçin bir değer belirtin **rol hizmeti önbellek zaman aşımı**. Rolleri sık güncelleştirildiği rolleri sık veya daha büyük bir değere güncelleştirildiğinde bu zaman aralığı düşük bir değere ayarlayın. Çevrimdışı modda uygularsanız, zaman aralığını uygulama çevrimdışı durumdayken rol bilgilerinin süresinin dolmasını önlemek için büyük bir değere ayarlayın.  
  
     Çağırdığınızda önbelleğe alınan rol değerleri veya rol hizmeti rol sağlayıcısı erişen <xref:System.Web.Security.RolePrincipal.IsInRole%2A> yöntemi. Program aracılığıyla önbelleğini sıfırlamak ve uzak hizmete erişmek için bu yöntem zorlamak üzere çağrı <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> yöntemi.  
  
5.  Seçin veya temizleyin **özel bağlantı dizesini kullan**. Daha fazla bilgi için sonraki yordama bakın.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>İstemci uygulama hizmetleri için yerel önbelleği bir veritabanını kullanmak üzere yapılandırmak için  
  
1.  Üzerinde **Hizmetleri** sayfasında **Proje Tasarımcısı**, tıklatın **Gelişmiş**.  
  
     **Hizmetler için Gelişmiş ayarları** iletişim kutusu görüntülenir.  
  
2.  Seçin **özel bağlantı dizesini kullan**.  
  
     Varsayılan değer olan `Data Source = |SQL/CE|` metin kutusunda görüntülenir.  
  
3.  Oluştur ve SQL Server Compact veritabanını kullanmak için varsayılan bağlantı dizesi değeri koruyun. Visual Studio veritabanı dosyası oluşturun ve tarafından belirtilen dizinde koymak <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> özelliği.  
  
4.  Oluştur ve şifreli bir kullanmak için [!INCLUDE[ssEW](../../../includes/ssew-md.md)] veritabanı, ekleme `password` ve `encrypt database` aşağıdaki örnekte gösterildiği gibi bağlantı dizesi değerleri.  
  
    > [!NOTE]
    >  Güçlü bir parola belirttiğinizden emin olun. Veritabanı oluşturulduktan sonra parolayı değiştiremez.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Kendi SQL Server veritabanını kullanmak için bağlantı dizenizi belirtin. Geçerli bir bağlantı dizesi biçimleri hakkında daha fazla bilgi için SQL Server belgelerine bakın. Bu veritabanını otomatik olarak oluşturulmaz. Bağlantı dizesi, aşağıdaki SQL deyimlerini kullanarak oluşturduğunuz varolan bir veritabanına başvurmalıdır.  
  
    ```  
    CREATE TABLE ApplicationProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE UserProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE Roles (UserName nvarchar(256),   
        RoleName nvarchar(256))  
    CREATE TABLE Settings (PropertyName nvarchar(256),   
        PropertyStoredAs nvarchar(1), PropertyValue nvarchar(2048))  
    ```  
  
## <a name="using-custom-providers"></a>Özel sağlayıcılar kullanma  
 Varsayılan olarak, istemci uygulama hizmetleri özelliği sağlayıcıları kullanır <xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> ad alanı. Kullanarak uygulamanızı yapılandırırken **Hizmetleri** sayfasında **Proje Tasarımcısı**, bu sağlayıcıları başvurular App.config dosyasına eklendi. Bu varsayılan sağlayıcı sunucuda karşılık gelen sağlayıcılar erişin. Web Hizmetleri gibi kullanıcı veri sağlayıcıları üzerinden erişim için sık sık yapılandırılır <xref:System.Web.Security.SqlMembershipProvider> ve <xref:System.Web.Security.SqlRoleProvider>.  
  
 Özel hizmet sağlayıcıları kullanmak istiyorsanız, böylece sunucunun erişen tüm istemci uygulamaları etkiler genellikle sunucu tarafında sağlayıcıları değiştirir. Ancak, istemci tarafında varsayılan olmayan sağlayıcıları kullanma seçeneğiniz vardır. Aşağıdaki yordamda gösterildiği gibi özel kimlik doğrulama veya rol sağlayıcıları projenizin App.config dosyasında belirtebilirsiniz. Özel kimlik doğrulama ve rol sağlayıcıları nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [üyelik sağlayıcısı uygulama](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) ve [rol sağlayıcısı uygulama](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Projenizin değiştirerek bir özel ayarlar sağlayıcısı kullanabilirsiniz `Settings` sınıfı (olarak erişilen `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te). Daha fazla bilgi için bkz: [uygulama ayarları mimarisi](../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>İstemci uygulama hizmetleri varsayılan olmayan sağlayıcısını kullanacak şekilde yapılandırmak için  
  
1.  Varsayılan olmayan kimlik doğrulama veya rol hizmeti sağlayıcı kullanmak için önce diğer tüm yapılandırma ayarlarını kullanarak tamamlayın **Hizmetleri** sayfası.  
  
2.  Kapat **Proje Tasarımcısı**. Bu gereklidir çünkü **Hizmetleri** sayfa otomatik olarak güncelleştirir, App.config dosyası bile herhangi bir ayarı değiştirmeyin. Bu yordamda açıklandığı gibi App.config dosyasını el ile değiştirmeniz ve sonra geri dönüp **Hizmetleri** sayfasında, değişiklikleriniz sıfırlanır.  
  
3.  İçinde **Çözüm Gezgini**, App.config çift tıklayın.  
  
     Uygulama yapılandırma dosyasına metin Düzenleyicisi'nde açar.  
  
4.  Bul `<providers>` öğesi içinde `<membership>` veya `<roleManager>` öğesi. Alt öğelerinin bu öğeler şunlardır `<system.web>` öğesi. `<membership>` Öğe kimlik doğrulama sağlayıcıları belirtmek için kullanılır ve `<roleManager>` öğe rol sağlayıcıları belirtmek için kullanılır.  
  
5.  Ekleme bir `<add>` öğesi bir alt öğesi olarak `<providers>` öğesi. Belirtmeniz gerekir `name` ve `type` özniteliklerini aşağıdaki örnekte gösterildiği gibi. `type` Öznitelik değeri bir bütünleştirilmiş kod tam tür adı olması gerekir. Daha fazla bilgi için bkz: <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> ve [derleme adları](../../../docs/framework/app-domains/assembly-names.md).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Değiştirme `defaultProvider` özniteliği `<membership>` veya `<roleManager>` adı değerini belirtmek için öğesi `<add>` önceki adımda eklediğiniz öğesi.  
  
    ```xml  
    <roleManager enabled="true" defaultProvider="MyCustomRoleProvider">  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Uygulama Servisleri](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [İstemci Uygulama Servislerine Genel Bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Hizmetler Sayfası, Proje Tasarımcısı](https://msdn.microsoft.com/library/bb398109)  
 [Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)  
 [Nasıl Yapılır: İstemci Uygulama Servisleri ile Kullanıcı Oturum Açma Adını Uygulama](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [İzlenecek Yol: İstemci Uygulama Servislerini Kullanma](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Üyelik sağlayıcıyı uygulama](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [Bir rol sağlayıcıyı uygulama](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [Uygulama Ayarları Mimarisi](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Oluşturma ve uygulama hizmetleri veritabanına SQL Server için yapılandırma](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
