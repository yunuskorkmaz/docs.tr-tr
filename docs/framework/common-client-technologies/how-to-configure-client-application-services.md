---
title: 'Nasıl Yapılır: İstemci Uygulama Hizmetlerini Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
ms.openlocfilehash: a65c216397f240b77eb81f88d8f2a2da122e1ccf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861630"
---
# <a name="how-to-configure-client-application-services"></a>Nasıl Yapılır: İstemci Uygulama Hizmetlerini Yapılandırma
Bu konu Visual Studio'nun nasıl kullanılacağını açıklar **Proje Tasarımcısı** etkinleştirmek ve istemci uygulama hizmetleri yapılandırmak için. İstemci uygulama Hizmetleri kullanıcıları doğrulamak ve mevcut bir kullanıcı rolleri ve ayarlarını almak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama hizmeti. Yapılandırmadan sonra etkin hizmetler uygulama kodunuzda açıklandığı erişebileceğiniz [istemci uygulama servislerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama hizmetleri [ASP.NET uygulama hizmetlerine genel bakış](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Etkinleştirme ve istemci uygulama servislerini yapılandırma **Hizmetleri** sayfasının **Proje Tasarımcısı**. **Hizmetleri** sayfasına projenizin App.config dosyasında değerlerini güncelleştirir. Erişim için **Proje Tasarımcısı**, kullanın **özellikleri** komutunu **proje** menüsü. Hakkında daha fazla bilgi için **Hizmetleri** sayfasında, bkz: [Hizmetler Sayfası, Proje Tasarımcısı](https://msdn.microsoft.com/library/bb398109).  
  
 Aşağıdaki yordam, istemci uygulama hizmetleri için temel yapılandırmayı gerçekleştirmek açıklar. Gelişmiş yapılandırma seçenekleri, sonraki bölümlerde açıklanmıştır.  
  
### <a name="to-configure-client-application-services"></a>İstemci uygulama hizmetleri yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, bir proje düğümü seçin ve ardından **proje** menüsünde tıklatın **özellikleri**.  
  
     **Proje Tasarımcısı** görünür.  
  
2.  Tıklayın **Hizmetleri** sekmesi. **Hizmetleri** sayfası görüntülenirse, aşağıdaki çizimde gösterildiği gibi.  
  
     ![Proje Tasarımcısı'nda Hizmetler sekmesinde](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Üzerinde **Hizmetleri** sayfasında **istemci uygulama hizmetlerini etkinleştirmek**.  
  
    > [!NOTE]
    >  İstemci uygulama hizmetleri, .NET Framework'ün tam sürümünü gerektirir ve .NET Framework istemci profili içinde desteklenmez. Varsa **istemci uygulama hizmetlerini etkinleştirmek** onay kutusunu devre dışı bırakıldı, doğrulayın **hedef Framework'ü** .NET Framework 3.5 veya sonraki bir sürüme ayarlayın. Görüntülenecek **hedef Framework'ü** C# ' de ayarı, Proje Tasarımcısı'nı açın ve ardından **uygulama** sayfası. Görüntülenecek **hedef Framework'ü** Visual Basic'te ayarlama, Proje Tasarımcısı'nı açın, **derleme** sayfasında ve ardından **Gelişmiş derleme seçenekleri**.  
  
4.  Seçin **formlar kimlik doğrulaması** kendi oturum açma denetimleri veya iletişim kutusu girin veya seçin planlıyorsanız **kullanan Windows kimlik doğrulaması** işletim sistemi tarafından sağlanan bir kimlik kullanacak şekilde. Daha fazla bilgi için [istemci uygulama servislerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  Seçerseniz **kullanan Windows kimlik doğrulaması**, istemci uygulama hizmetleri otomatik olarak bir SQL Server Compact veritabanını kullanacak şekilde yapılandırılacak. Bu belirtilen **hizmetler için Gelişmiş ayarları** sonraki bölümde açıklandığı gibi iletişim kutusu. Ardından seçerseniz **formlar kimlik doğrulama**, **özel bağlantı dizesini kullanmak** ayarı değil işaretinin kaldırılması otomatik olarak. Bu hatalar sonuçlanabilir [!INCLUDE[ssEW](../../../includes/ssew-md.md)] veritabanı zaten oluşturuldu Windows kimlik doğrulaması ile kullanılacak. Bu hataları gidermek için temizleyin **özel bağlantı dizesini kullanmak** ayarı **hizmetler için Gelişmiş ayarları** iletişim kutusu.  
  
5.  Seçtiyseniz **formlar kimlik doğrulama**, **kimlik doğrulama hizmet konumu** kutusuna, dosya adı dahil değil, bir hizmet konağı URL'sini belirtin. Değeri yapılandırma dosyasına yazarken Tasarımcı standart dosya adı (Authentication_JSON_AppService.axd) otomatik olarak eklenir.  
  
6.  İsteğe bağlı olarak, seçtiyseniz **formlar kimlik doğrulama**, bir değer belirtebilirsiniz **kimlik bilgileri sağlayıcısı** kutusu. Kimlik bilgileri sağlayıcısı uygulamalıdır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi. Bir kimlik sağlayıcısı kullanarak oturum açma kullanıcı arabiriminiz diğer uygulama kodunuzdan ayırabilirsiniz. Bu, birden çok uygulamada kullanmak için bir çoklu oturum açma iletişim kutusu oluşturmanıza olanak sağlar. Daha fazla bilgi için [nasıl yapılır: istemci uygulama hizmetleri ile kullanıcı oturumu uygulama](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Bir kimlik sağlayıcısı belirtirseniz, bir derleme nitelikli tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> ve [derleme adları](../../../docs/framework/app-domains/assembly-names.md). En basit şekliyle, bir derleme nitelikli tür adı, aşağıdaki örneğe benzer:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  İçinde **rolleri hizmet konumu** ve **hizmet konumu Web ayarları** metin kutuları, dosya adı dahil değil, her hizmet için hizmet konumu belirtin. Tasarımcı (Role_JSON_AppService.axd ve Profile_JSON_AppService.axd) standart dosya adları otomatik olarak ekler yapılandırma dosyasına değeri yazdığında.  
  
8.  İsteğe bağlı olarak, tıklayın **Gelişmiş** yerel önbelleğe alma davranışını gibi gelişmiş ayarları değiştirmek için. Daha fazla bilgi için sonraki yordama bakın.  
  
## <a name="advanced-configuration"></a>Gelişmiş Yapılandırma  
 Aşağıdaki yordamlarda, daha az yaygın senaryolar için istemci uygulama servislerini yapılandırma açıklanır. Örneğin, ortak bir konumda veya yerel veri önbelleği olarak şifrelenmiş bir SQL Server Compact veritabanı kullanmak için dağıtılan uygulamalar için bu yapılandırma seçenekleri kullanabilirsiniz.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Gelişmiş istemci uygulama hizmetleri için ayarları yapılandırmak için  
  
1.  Üzerinde **Hizmetleri** sayfasının **Proje Tasarımcısı**, tıklayın **Gelişmiş**.  
  
     **Hizmetler için Gelişmiş ayarları** iletişim kutusu görüntülenirse, aşağıdaki çizimde gösterildiği gibi. Bu iletişim kutusu hakkında daha fazla bilgi için bkz. [Hizmetleri iletişim kutusu için Gelişmiş ayarları](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Hizmetleri iletişim kutusu için Gelişmiş ayarları](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Seçin veya temizleyin **çevrimdışı oturum açma yerel olarak etkinleştirmek için parola karması Kaydet**. Bu seçeneği belirlediğinizde, bir kullanıcının parolasını şifrelenmiş yerel olarak önbelleğe alınır. Uygulamanız için çevrimdışı moda uygularsanız, bu yararlıdır. Bu seçenek belirtilmişse, kullanıcıları doğrulamak bile <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> özelliği sınıflandırmalara ayarlandığı `true`.  
  
3.  Seçin veya temizleyin **sunucu tanımlama bilgisi süresi her yeniden oturum açmasını gerektiren**. Kimlik doğrulama tanımlama uzak hizmeti üzerinde yapılandırılmış ve bir kullanıcı oturumunun ne kadar süreyle etkin kalacak gösterir. Tanımlama bilgisi yapılandırma hakkında daha fazla bilgi için bkz. `timeout` özniteliğini [öğesi form kimlik doğrulamasını (ASP.NET Settings Schema) için](https://msdn.microsoft.com/library/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Bu seçenek, uzaktan rolleri erişmeye seçerse ya da kimlik doğrulama tanımlama süresi dolduktan sonra Web ayarları Hizmetleri oluşturur bir <xref:System.Net.WebException>. Bu özel durumu işlemek ve bir oturum açma iletişim kutusu, kullanıcıların düzeltin. Bu davranış bir örnek için bkz [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Bu seçenek, kullanım kalmaz sonra uygulamasını çalışır durumda bırakın kullanıcılar süresiz olarak kimliğinin emin olmak genel konumda dağıtılan uygulamalar için yararlıdır.  
  
     Bu seçenek ve kimlik doğrulama tanımlama süresi dolduktan sonra uzak Hizmetleri erişmeye çalışırken işaretini kaldırırsanız, kullanıcıların otomatik olarak yeniden doğrulanır.  
  
4.  İçin bir değer belirtin **rol hizmeti önbellek zaman aşımı**. Rolleri seyrek güncelleştirildiğinde rolleri sık veya daha büyük bir değere güncelleştirildiğinde bu zaman aralığı için küçük bir değere ayarlayın. Çevrimdışı modda uygularsanız, zaman aralığını uygulamayı çevrimdışı durumdayken rol bilgilerinin süresinin dolmasını önlemek için büyük bir değere ayarlayın.  
  
     Çağırdığınızda, önbelleğe alınmış rol değerlerinin veya rol hizmeti rol sağlayıcısı erişen <xref:System.Web.Security.RolePrincipal.IsInRole%2A> yöntemi. Program aracılığıyla önbelleği sıfırlamak ve uzak hizmete erişmek için bu yöntem zorlamak için çağrı <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> yöntemi.  
  
5.  Seçin veya temizleyin **özel bağlantı dizesini kullanmak**. Daha fazla bilgi için sonraki yordama bakın.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>İstemci uygulama hizmetleri için yerel önbellek bir veritabanını kullanacak şekilde yapılandırmak için  
  
1.  Üzerinde **Hizmetleri** sayfasının **Proje Tasarımcısı**, tıklayın **Gelişmiş**.  
  
     **Hizmetler için Gelişmiş ayarları** iletişim kutusu görüntülenir.  
  
2.  Seçin **özel bağlantı dizesini kullanmak**.  
  
     Varsayılan değer olan `Data Source = |SQL/CE|` metin kutusunda görüntülenir.  
  
3.  Oluşturma ve SQL Server Compact veritabanı kullanmak için varsayılan bağlantı dizesi değeri tutun. Visual Studio veritabanı dosyası oluştur ve tarafından belirtilen dizine yerleştirin <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> özelliği.  
  
4.  Oluştur ve şifrelenmiş bir [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ekleyin, veritabanı `password` ve `encrypt database` bağlantı dizesine aşağıdaki örnekte gösterildiği gibi değerleri.  
  
    > [!NOTE]
    >  Güçlü bir parola belirttiğinizden emin olun. Veritabanı oluşturulduktan sonra parolayı değiştiremez.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Kendi SQL Server veritabanını kullanmak için kendi bağlantı dizesini belirtin. Geçerli bağlantı dizesi biçimleri hakkında daha fazla bilgi için SQL Server belgelerine bakın. Bu veritabanı otomatik olarak oluşturulmaz. Bağlantı dizesi aşağıdaki SQL deyimlerini kullanarak oluşturabilirsiniz. Varolan bir veritabanına işaret etmelidir.  
  
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
 Varsayılan olarak, istemci uygulama hizmetleri özelliği sağlayıcıları kullanan <xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> ad alanı. Kullanarak uygulamanızı yapılandırırken **Hizmetleri** sayfasının **Proje Tasarımcısı**, bu sağlayıcıları başvurularını, App.config dosyanıza eklenir. Bu varsayılan sağlayıcı sunucuda karşılık gelen sağlayıcıları erişin. Web Hizmetleri sağlayıcıları gibi kullanıcı verilerine erişmek için genellikle yapılandırılır <xref:System.Web.Security.SqlMembershipProvider> ve <xref:System.Web.Security.SqlRoleProvider>.  
  
 Özel hizmet sağlayıcıları kullanmak istiyorsanız, bunlar sunucuya erişen tüm istemci uygulamaları etkilememesi sunucu tarafında sağlayıcıları genellikle değiştirmek. Ancak, istemci tarafında varsayılan olmayan sağlayıcıları kullanma seçeneğiniz vardır. Aşağıdaki yordamda gösterildiği gibi özel kimlik doğrulama veya rol sağlayıcısı projenizin App.config dosyasında belirtebilirsiniz. Özel kimlik doğrulama ve rol sağlayıcıları oluşturma hakkında daha fazla bilgi için bkz: [üyelik sağlayıcıyı uygulama](https://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) ve [rol sağlayıcıyı uygulama](https://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Projenizin değiştirerek bir özel ayar sağlayıcısı kullanabilirsiniz `Settings` sınıfı (erişilebilir `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te). Daha fazla bilgi için [uygulama ayarları mimarisi](../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>İstemci uygulama hizmetleri varsayılan olmayan sağlayıcılarını kullanacak şekilde yapılandırmak için  
  
1.  Varsayılan olmayan kimlik doğrulaması ya da rolleri hizmet sağlayıcısı kullanmak için önce tüm yapılandırma ayarlarını kullanarak tamamlayın **Hizmetleri** sayfası.  
  
2.  Kapat **Proje Tasarımcısı**. Bu gereklidir çünkü **Hizmetleri** sayfası otomatik olarak güncelleştirilir, App.config dosyanızı bile herhangi bir ayarı değiştirmeyin. App.config dosyanız bu yordamda açıklandığı şekilde el ile değiştirmeniz ve sonra geri dönüp, **Hizmetleri** sayfasında, değişiklikleriniz sıfırlayın.  
  
3.  İçinde **Çözüm Gezgini**, App.config çift tıklayın.  
  
     Uygulama yapılandırma dosyası metin düzenleyicisinde açılır.  
  
4.  Bulma `<providers>` öğesiyle `<membership>` veya `<roleManager>` öğesi. Bu öğeleri alt öğeleri olan `<system.web>` öğesi. `<membership>` Öğesi kimlik doğrulama sağlayıcıları belirtmek için kullanılır ve `<roleManager>` öğesi rol sağlayıcıları belirtmek için kullanılır.  
  
5.  Ekleme bir `<add>` öğesi alt öğesi olarak `<providers>` öğesi. Belirtmelisiniz `name` ve `type` aşağıdaki örnekte gösterildiği gibi öznitelikleri. `type` Öznitelik değeri bir derleme nitelikli tür adı olmalıdır. Daha fazla bilgi için <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> ve [derleme adları](../../../docs/framework/app-domains/assembly-names.md).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Değiştirme `defaultProvider` özniteliği `<membership>` veya `<roleManager>` adı değerini belirtmek için öğe `<add>` önceki adımda eklediğiniz öğesi.  
  
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
 [Üyelik sağlayıcıyı uygulama](https://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [Bir rol sağlayıcıyı uygulama](https://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [Uygulama Ayarları Mimarisi](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Oluşturma ve uygulama hizmetleri veritabanına SQL Server için yapılandırma](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
