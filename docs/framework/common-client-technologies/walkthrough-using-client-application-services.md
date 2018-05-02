---
title: 'İzlenecek Yol: İstemci Uygulama Hizmetlerini Kullanma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e67d4297ca0fe7028380b6d862f9f86c93bcaa61
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-using-client-application-services"></a>İzlenecek Yol: İstemci Uygulama Hizmetlerini Kullanma
Bu konuda kullanıcıların kimliğini doğrulamak ve kullanıcı rolleri ve ayarları almak için istemci uygulama hizmetleri kullanan bir Windows uygulamasının nasıl oluşturulacağını açıklar.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Bir Windows Forms uygulaması oluşturma ve Visual Studio Proje Tasarımcısı etkinleştirmek ve istemci uygulama hizmetleri yapılandırmak için kullanın.  
  
-   Uygulama Hizmetleri ana bilgisayar ve istemci yapılandırmanızı test etmek için basit bir ASP.NET Web hizmeti uygulaması oluşturun.  
  
-   Form kimlik doğrulaması uygulamanıza ekleyin. Hizmet test etmek için bir sabit kodlanmış kullanıcı adı ve parola kullanarak başlar. Kimlik sağlayıcısı, uygulama yapılandırmasında olarak belirterek, bir oturum açma formu sonra ekleyeceksiniz.  
  
-   Etkinleştirme ve kullanıcılar için yalnızca bir düğme "Yönetici" rolünde görüntüleme rol tabanlı işlevselliği ekleyin.  
  
-   Web ayarları erişin. Üzerinde bir kimliği doğrulanmış (test) kullanıcı için Web ayarları yükleyerek başlayacak **ayarları** sayfası Proje Tasarımcısı'nın. Windows Form Tasarımcısı sonra Web ayarı için bir metin kutusu bağlamak için de kullanır. Son olarak, sunucuya geri değiştirilmiş değerini kaydeder.  
  
-   Oturum kapatma uygulayın. Bir oturum kapatma seçeneği forma ekleyin ve oturum kapatma yöntemini çağırın.  
  
-   Çevrimdışı modunu etkinleştirin. Böylece kullanıcılar kendi bağlantı durumu belirtebilir, bir onay kutusu sağlar. Sonra istemci uygulama hizmet sağlayıcıları kendi Web hizmetlerine erişme yerine yerel olarak önbelleğe alınan veriler kullanıp kullanmayacağını belirtmek için bu değeri kullanır. Son olarak, uygulama çevrimiçi moda döndürdüğünde geçerli kullanıcının yeniden kimliğini doğrular.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenler gerekir:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>İstemci Uygulamasını Oluşturma  
 Ne yapacağını ilk şey, bir Windows Forms projesi oluşturun. Bu kılavuzda Windows Forms kullanır, çünkü daha fazla kişinin ile sahibiyseniz, ancak Windows Presentation Foundation (WPF) projeleri için benzer bir işlemdir.  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Bir istemci uygulaması oluşturma ve istemci uygulama hizmetleri etkinleştirme  
  
1.  Visual Studio'da seçin **dosya &#124; yeni &#124; proje** menü seçeneği.  
  
2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde genişletin **Visual Basic** veya **Visual C#** düğümü ve select **Windows** proje türü.  
  
3.  Olduğundan emin olun **.NET Framework 3.5** seçili ve ardından **Windows Forms uygulaması** şablonu.  
  
4.  Proje değiştirme **adı** için `ClientAppServicesDemo`ve ardından **Tamam**.  
  
     Visual Studio'da yeni bir Windows Forms projesi açılır.  
  
5.  Üzerinde **proje** menüsünde, select **ClientAppServicesDemo özellikleri**.  
  
     Proje Tasarımcısı görünür.  
  
6.  Üzerinde **Hizmetleri** sekmesine **etkinleştirmek istemci uygulama hizmetleri**.  
  
7.  Olduğundan emin olun **formlar kimlik doğrulaması** seçilir ve ardından **kimlik doğrulama hizmeti konumu**, **rolleri hizmet konumu**, ve **Web ayarları hizmet konumu** için `http://localhost:55555/AppServices`.  
  
8.  Visual Basic üzerinde **uygulama** sekmesinde, ayarlamak **kimlik doğrulama modu** için **uygulama tanımlı**.  
  
 Tasarımcı belirtilen ayarlar uygulamanın app.config dosyasında depolar.  
  
 Bu noktada, uygulama, tüm üç hizmeti aynı ana bilgisayarından erişmek için yapılandırılır. Sonraki bölümde, böylece istemci yapılandırmanızı test etmek basit bir Web hizmeti uygulaması, ana bilgisayar oluşturur.  
  
## <a name="creating-the-application-services-host"></a>Uygulama Hizmetleri konağı oluşturma  
 Bu bölümde, kullanıcı verilerini yerel bir SQL Server Compact veritabanı dosyadan erişen basit bir Web hizmeti uygulaması oluşturacaksınız. Ardından, veritabanını kullanarak dolduracaktır [ASP.NET Web sitesi yönetim aracı](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Bu basit yapılandırma hızla istemci uygulamanızı test etmek etkinleştirir. Alternatif olarak, Web hizmeti ana bilgisayarını kullanıcı verilerine erişmek için tam SQL Server veritabanından veya özel aracılığıyla yapılandırabilirsiniz <xref:System.Web.Security.MembershipProvider> ve <xref:System.Web.Security.RoleProvider> sınıfları. Daha fazla bilgi için bkz: [oluşturma ve uygulama Hizmetleri veritabanı için SQL Server yapılandırma](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 Aşağıdaki yordamda oluşturun ve AppServices Web hizmetini yapılandırın.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Oluşturma ve uygulama hizmetleri ana bilgisayarı yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo çözümü seçin ve ardından **dosya** menüsünde, select **Ekle &#124; yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda **proje türleri** bölmesinde genişletin **Visual Basic** veya **Visual C#** düğümü ve seçin **Web** proje türü.  
  
3.  Olduğundan emin olun **.NET Framework 3.5** seçili ve ardından **ASP.NET Web hizmeti uygulama** şablonu.  
  
4.  Proje değiştirme **adı** için `AppServices` ve ardından **Tamam**.  
  
     Yeni bir ASP.NET Web hizmeti uygulama projesi çözüme eklenir ve Service1.asmx.vb veya Service1.asmx.cs dosyası Düzenleyicisi'nde görüntülenir.  
  
    > [!NOTE]
    >  Bu örnekte Service1.asmx.vb veya Service1.asmx.cs dosyasını kullanılmaz. Çalışma ortamınıza tıklatıncaya istiyorsanız, kapatmak ve silmek **Çözüm Gezgini**.  
  
5.  İçinde **Çözüm Gezgini**, AppServices projesini seçin ve ardından **proje** menüsünde, select **AppServices özellikleri**.  
  
     Proje Tasarımcısı görünür.  
  
6.  Üzerinde **Web** sekmesinde, olduğundan emin olun **kullanım Visual Studio geliştirme sunucusu** seçilir.  
  
7.  Seçin **belirli bir bağlantı noktası**, değerini belirtin `55555`ve ardından **sanal yolu** için `/AppServices`.  
  
8.  Tüm dosyalarını kaydedin.  
  
9. İçinde **Çözüm Gezgini**, Web.config dosyasını açın ve bulmak `<system.web>` etiketi açma.  
  
10. Önce aşağıdaki biçimlendirmeleri eklemek `<system.web>` etiketi.  
  
     `authenticationService`, `profileService`, Ve `roleService` bu biçimlendirme öğelerinde etkinleştirin ve uygulama hizmetlerini yapılandırın. Test amacıyla, `requireSSL` özniteliği `authenticationService` öğesi "false" olarak ayarlanmış. `readAccessProperties` Ve `writeAccessProperties` özniteliklerini `profileService` öğesi belirtmek `WebSettingsTestText` okuma/yazma özelliğidir.  
  
    > [!NOTE]
    >  Üretim kodunda Güvenli Yuva Katmanı (HTTPS protokolünü kullanarak SSL) üzerinden kimlik doğrulama hizmeti her zaman erişmelidir. SSL kurma hakkında daha fazla bilgi için bkz: [Güvenli Yuva Katmanı Yapılandırma (IIS 6.0 işlemler Kılavuzu)](http://go.microsoft.com/fwlink/?LinkId=91844).  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. Sonra aşağıdaki biçimlendirmeleri eklemek `<system.web>` etiketi içinde olmasını sağlamak açma `<system.web>` öğesi.  
  
     `profile` Öğesi yapılandırır adlandırılmış ayarlama tek bir Web `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 Aşağıdaki yordamda, hizmet yapılandırmasını tamamlamak ve yerel veritabanı dosyasını doldurmak için ASP.NET Web Sitesi Yönetim Aracı'nı kullanın. Adlı iki kullanıcı ekleyeceksiniz `employee` ve `manager` aynı adı taşıyan iki rollere ait. Kullanıcı parolaları `employee!` ve `manager!` sırasıyla.  
  
#### <a name="to-configure-membership-and-roles"></a>Üyelik ve roller yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, AppServices projesini seçin ve ardından **proje** menüsünde, select **ASP.NET yapılandırma**.  
  
     **ASP.NET Web sitesi yönetim aracı** görüntülenir.  
  
2.  Üzerinde **güvenlik** sekmesini tıklatın, **güvenlik adım adım yapılandırmak için Güvenlik Kurulum Sihirbazı'nı kullanın**.  
  
     **Güvenlik Kurulum Sihirbazı'nı** görünür ve görüntüler **Hoş Geldiniz** adım.  
  
3.  **İleri**'ye tıklayın.  
  
     **Erişim yöntemi seçin** adımı görüntülenir.  
  
4.  Seçin **internet'ten**. Hizmetini form kimlik doğrulaması yerine Windows kimlik doğrulaması kullanacak şekilde yapılandırır.  
  
5.  Tıklatın **sonraki** iki kez.  
  
     **Rolleri tanımlama** adımı görüntülenir.  
  
6.  Seçin **etkinleştirmek için bu Web sitesi rolleri**.  
  
7.  **İleri**'ye tıklayın. **Yeni rol oluşturma** formu görüntülenir.  
  
8.  İçinde **yeni rol adı** metin kutusunda, `manager` ve ardından **Rol Ekle**.  
  
     **Mevcut rolleri** tablo belirtilen değerle görünür.  
  
9. İçinde **yeni rol adı** metin kutusunda, yerine `manager` ile `employee` ve ardından **Rol Ekle**.  
  
     Yeni değer görünür **mevcut rolleri** tablo.  
  
10. **İleri**'ye tıklayın.  
  
     **Yeni kullanıcı Ekle** adımı görüntülenir.  
  
11. İçinde **kullanıcı oluştur** formunda, aşağıdaki değerleri belirtin.  
  
  	|||  
  	|-|-|  
  	|**Kullanıcı adı**|`manager`|  
  	|**Parola**|`manager!`|  
  	|**Parolayı onaylayın**|`manager!`|  
  	|**E-posta**|`manager@contoso.com`|  
  	|**Güvenlik sorusu**|`manager`|  
  	|**Güvenlik yanıtı**|`manager`|  
  
12. Tıklatın **kullanıcı oluşturma**.  
  
     Bir başarı iletisi görüntülenir.  
  
    > [!NOTE]
    >  **E-posta**, **Güvenlik sorusu**, ve **güvenlik yanıtı** değerleri form tarafından gerekir, ancak bu örnekte kullanılmaz.  
  
13. 
              **Devam**'a tıklayın.  
  
     **Kullanıcı oluştur** form görüntülenir.  
  
14. İçinde **kullanıcı oluştur** formunda, aşağıdaki değerleri belirtin.  
  
  	|||  
  	|-|-|  
  	|**Kullanıcı adı**|`employee`|  
  	|**Parola**|`employee!`|  
  	|**Parolayı onaylayın**|`employee!`|  
  	|**E-posta**|`employee@contoso.com`|  
  	|**Güvenlik sorusu**|`Employee`|  
  	|**Güvenlik yanıtı**|`employee`|  
  
15. Tıklatın **kullanıcı oluşturma**.  
  
     Bir başarı iletisi görüntülenir.  
  
16. **Son**'a tıklayın.  
  
     **Web sitesi yönetim aracı** görüntülenir.  
  
17. Tıklatın **Yöneticisi kullanıcıları**.  
  
     Kullanıcılar listesi görüntülenir.  
  
18. Tıklatın **Düzenle rolleri** için **çalışan** kullanıcı ve ardından **çalışan** rol.  
  
19. Tıklatın **Düzenle rolleri** için **Yöneticisi** kullanıcı ve ardından **Yöneticisi** rol.  
  
20. Barındıran tarayıcı penceresini kapatın **Web sitesi yönetim aracı**.  
  
21. Değiştirilen Web.config dosyasını yeniden yüklemek istiyorsanız, tıklatın isteyen bir ileti kutusu görüntülenirse **Evet**.  
  
 Bu Web hizmeti Kurulumu tamamlar. Bu noktada, istemci uygulamasını çalıştırmak için F5 tuşuna basabilirsiniz ve **ASP.NET Geliştirme Sunucusu** istemci uygulamanız ile birlikte otomatik olarak başlatılacak. Sunucu uygulamadan çıkmak, ancak uygulama yeniden başlatıldığında yeniden başlatılır sonra çalışmaya devam eder. Bu, Web.config dosyasına yapmış olduğunuz değişiklikleri algılamak üzere sağlar.  
  
 Sunucu el ile durdurmak için görev çubuğu bildirim alanında ASP.NET Geliştirme Sunucusu simgesine sağ tıklayın ve ardından **durdurmak**. Bu, zaman zaman temiz bir yeniden başlatma oluşması emin olmak kullanışlıdır.  
  
## <a name="adding-forms-authentication"></a>Form kimlik doğrulaması ekleme  
 Aşağıdaki yordamda, kullanıcıyı doğrulamak çalışır ve kullanıcı geçersiz kimlik bilgileri sağlayan olduğunda erişimini engellediği ana form için kodu ekleyin. Hizmet sınamak için bir sabit kodlanmış kullanıcı adı ve parolası'nı kullanın.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>Kullanıcı, uygulama kodunuzda doğrulamak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projesinde System.Web derlemesine başvuru ekleyin.  
  
2.  Form1 dosyasını seçin ve ardından **Görünüm &#124; kod** Visual Studio ana menüden.  
  
3.  Kod Düzenleyicisi'nde aşağıdaki deyimleri Form1 dosyasının üstüne ekleyin.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  İçinde **Çözüm Gezgini**, Form1 Tasarımcısı'nı görüntülemek için çift tıklayın.  
  
5.  Tasarımcısı'nda oluşturmak için form yüzeyini çift tıklayarak bir <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> adlı olay işleyicisi `Form1_Load`.  
  
     Kod Düzenleyicisi imleç görünür `Form1_Load` yöntemi.  
  
6.  Aşağıdaki kodu ekleyin `Form1_Load` yöntemi.  
  
     Bu kod, uygulamanın çıkılarak, kimliği doğrulanmamış kullanıcıları erişimini engeller. Alternatif olarak, kimliği doğrulanmamış kullanıcıların formun erişmesine izin vermek ancak belirli işlevlere erişim engelle. Normalde, sabit kodlu kullanıcı adı ve parola aşağıdaki gibi, ancak test amacıyla yararlıdır. Sonraki bölümde, bu kod bir oturum açma iletişim kutusu görüntüler ve özel durum işleme içeren daha sağlam koduyla yerini alır.  
  
     Unutmayın `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi konusu [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Bu yöntem, iş için yapılandırılan kimlik doğrulama sağlayıcısı atar ve döndürür `true` kimlik doğrulaması başarılı olduğunda. Uygulamanızın istemci kimlik doğrulama sağlayıcısı için doğrudan bir başvuru gerektirmez.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Şimdi uygulamayı çalıştırmak için F5'e basın ve doğru kullanıcı adı ve parola sağladığından, formu görürsünüz.  
  
> [!NOTE]
>  Uygulamayı çalıştırmak ASP.NET Geliştirme Sunucusu durdurma deneyin. Sunucu yeniden başlatıldıktan sonra bağlantı noktası için 55555 ayarlandığını doğrulayın.  
  
 Bunun yerine hata iletisini görmek için değiştirme <xref:System.Web.Security.Membership.ValidateUser%2A> parametreleri. Örneğin, ikinci yerine `"manager!"` hatalı bir parolanın parametresiyle ister `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Bir oturum açma formu bir kimlik sağlayıcısı olarak ekleme  
 Uygulama kodunuzda kullanıcı kimlik bilgilerini almak ve bunları geçirin <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi. Ancak, genellikle daha sonra değiştirmek istediğiniz durumda kimlik bilgileri alınırken kodunuzu uygulama kodunuzdan ayrı tutmak yararlı olacaktır.  
  
 Aşağıdaki yordamda, bir kimlik sağlayıcısı kullanın ve sonra değiştirmek için uygulamanızın yapılandırma, <xref:System.Web.Security.Membership.ValidateUser%2A> geçirmek için yöntem çağrısı <xref:System.String.Empty> her iki parametre için. Boş dizeler sinyal <xref:System.Web.Security.Membership.ValidateUser%2A> çağrılacak yöntem <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi yapılandırılan kimlik bilgileri sağlayıcısı.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Uygulamanızı bir kimlik sağlayıcısı kullanacak şekilde yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projesini seçin ve ardından **proje** menüsünde, select **ClientAppServicesDemo özellikleri**.  
  
     Proje Tasarımcısı görünür.  
  
2.  Üzerinde **Hizmetleri** sekmesinde, ayarlamak **isteğe bağlı: kimlik bilgileri sağlayıcısı** aşağıdaki değeri. Bu değer derleme nitelenmiş tür adını belirtir.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  Kodda Form1 kod dosyasına Değiştir `Form1_Load` aşağıdaki kod ile yöntemi.  
  
     Bu kod bir Hoş Geldiniz iletisi görüntüler ve ardından çağırır `ValidateUsingCredentialsProvider` sonraki adımda ekleyeceksiniz yöntemi. Kullanıcının kimliği doğrulanmazsa `ValidateUsingCredentialsProvider` yöntemi döndürür `false` ve `Form1_Load` yöntemi döndürür. Bu, herhangi bir ek kod uygulama çıktıktan önce çalışmasını önler. Hoş Geldiniz iletisi uygulama yeniden başlatıldığında temizleyin sağlamak kullanışlıdır. Bu kılavuzda daha sonra oturum kapatma uyguladığınızda uygulamayı yeniden başlatmak için kod ekleyeceksiniz.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Sonra aşağıdaki yöntemi ekleyin `Form1_Load` yöntemi.  
  
     Bu yöntem boş dizeler geçirir `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> görünmesi oturum açma iletişim kutusu neden yöntemi. Kimlik doğrulama hizmeti kullanılamıyorsa, <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi oluşturur bir <xref:System.Net.WebException>. Bu durumda, `ValidateUsingCredentialsProvider` yöntemi bir uyarı iletisi görüntüler ve kullanıcı yeniden çevrimdışı modda deneyin isteyip istemediği sorulur. Bu işlevsellik gerektirir **yerel olarak çevrimdışı oturum açma etkinleştirmek için parola karması Kaydet** özelliği açıklanan [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Bu özellik, yeni projeler için varsayılan olarak etkindir.  
  
     Kullanıcı doğrulanmaz, `ValidateUsingCredentialsProvider` yöntemi uygulamadan çıkar ve bir hata iletisi görüntüler. Son olarak, bu yöntem, kimlik doğrulama girişimi sonucunu döndürür.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Bir oturum açma formu oluşturma  
 Bir kimlik sağlayıcı uygulayan bir sınıftır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi. Bu arabirim adlı tek bir yöntemi olan <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> döndüren bir <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> nesnesi. Aşağıdaki yordamlar uygulayan bir oturum açma iletişim kutusu oluşturma açıklar <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> kendisini görüntülemek ve kullanıcı tarafından belirtilen kimlik bilgileri döndürmek için.  
  
 Ayrı yordamları sağlanan Visual Basic ve C# için Visual Basic sağladığından bir **oturum açma formu** şablonu. Bu işlem biraz zaman ve çaba kodlama kaydeder.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Visual Basic'te kimlik sağlayıcısı olarak bir oturum açma iletişim kutusu oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projesini seçin ve ardından **proje** menüsünde, select **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **oturum açma formu** şablonu, öğeyi değiştirmek **adı** için `Login.vb`ve ardından **Ekle** .  
  
     Windows Forms Tasarımcısı'nda oturum açma iletişim kutusu görüntülenir.  
  
3.  Tasarımcıda seçin **Tamam** düğmesine ve ardından **özellikleri** penceresindeki ayarlayın `DialogResult` için `OK`.  
  
4.  Tasarımcıda eklemek bir `CheckBox` formun altında denetimine **parola** metin kutusu.  
  
5.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `rememberMeCheckBox` ve **metin** değerini `&Remember me`.  
  
6.  Seçin **Görünüm &#124; kod** Visual Studio ana menüden.  
  
7.  Kod Düzenleyicisi'nde, aşağıdaki kodu dosyanın üst kısmına ekleyin.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Böylece sınıfı uygulayan sınıf imza değiştirmek <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. İmleç sonra olduğundan emin olun `IClientformsAuthenticationCredentialsProvider`, ve oluşturmak için ENTER tuşuna basın `GetCredentials` yöntemi.  
  
10. Bulun <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> uygulama ve aşağıdaki kod ile değiştirin.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 Aşağıdaki C# yordam bir basit oturum açma iletişim kutusu için kod listesinde yer alan tüm sağlar. Bu iletişim kutusunu düzenini biraz kaba olmakla birlikte, önemli bir parçasıdır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> uygulaması.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>C# kimlik sağlayıcısı olarak bir oturum açma iletişim kutusu oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projesini seçin ve ardından **proje** menüsünde, select **sınıfı Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusu, değişiklik **adı** için `Login.cs`ve ardından **Ekle**.  
  
     Kod Düzenleyicisi'nde Login.cs dosyayı açar.  
  
3.  Varsayılan kodu aşağıdaki kodla değiştirin.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Şimdi uygulamayı çalıştırın ve oturum açma iletişim kutusu görünür. Bu kodu test etmek için farklı kimlik bilgileri, geçerli ve geçersiz deneyin ve yalnızca geçerli kimlik bilgileriyle forma erişebilirsiniz onaylayın. Geçerli kullanıcı adları `employee` ve `manager` parolalarla `employee!` ve `manager!` sırasıyla.  
  
> [!NOTE]
>  Seçmeyin **Beni anımsa** bu noktaya veya, bu kılavuzda daha sonra oturum kapatma uygulayana kadar başka bir kullanıcı olarak oturum açmak mümkün olmaz.  
  
## <a name="adding-role-based-functionality"></a>Rol tabanlı işlevsellik ekleme  
 Aşağıdaki yordamda bir düğme forma ekleyin ve yalnızca Yöneticisi rolündeki kullanıcılar için görüntüleyin.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Kullanıcı rolü tabanlı kullanıcı arabirimi değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projede Form1 seçin ve ardından **Görünüm &#124; Tasarımcısı** Visual Studio ana menüden.  
  
2.  Tasarımcıda eklemek bir <xref:System.Windows.Forms.Button> formdan denetimine **araç**.  
  
3.  İçinde **özellikleri** penceresindeki düğmesi için aşağıdaki özellikleri ayarlayın.  
  
  	|Özellik|Değer|  
  	|--------------|-----------|  
  	|**(Ad)**|managerOnlyButton|  
  	|**Metin**|& Yöneticisi görevi|  
  	|**Görünür**|`False`|  
  
4.  Form1 kod düzenleyicisinde sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi.  
  
     Bu kod çağırır `DisplayButtonForManagerRole` sonraki adımda ekleyeceksiniz yöntemi.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Aşağıdaki yöntem Form1 sınıfı sonuna ekleyin.  
  
     Bu yöntemi çağırır <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi <xref:System.Security.Principal.IPrincipal> tarafından döndürülen `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği. İstemci uygulama hizmetleri kullanmak üzere yapılandırılan uygulamalar için bu özelliği döndürür bir <xref:System.Web.ClientServices.ClientRolePrincipal>. Bu sınıf uyguladığından <xref:System.Security.Principal.IPrincipal> arabirimi, gereksinim açıkça başvurmak.  
  
     Kullanıcı "Yönetici" rolünde ise `DisplayButtonForManagerRole` yöntemi kümeleri <xref:System.Windows.Forms.Control.Visible%2A> özelliği `managerOnlyButton` için `true`. Bu yöntem aynı zamanda bir hata iletisi görüntüler bir <xref:System.Net.WebException> oluşturulur, rol hizmeti kullanılamaz olduğunu gösterir.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> Yöntemi her zaman döndürecektir `false` kullanıcı oturum açma dolmuşsa. Uygulamanızı çağırırsa bu gerçekleşmez <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi için bu kılavuzda örnek kodda gösterildiği gibi kısa bir süre içinde kimlik doğrulamasından sonra bir kez. Diğer saatlerde uygulamanız kullanıcı rolleri almanız gerekir, kullanıcılar, oturum açma süresi doldu düzeltin kod eklemek isteyebilirsiniz. Tüm geçerli kullanıcıları rollere atanırsa, oturum açma çağırarak süresinin dolup dolmadığını belirleyebilirsiniz <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> yöntemi. Hiç rol döndürülürse, oturum açma süresi doldu. Bu işlev bir örnek için bkz: <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> yöntemi. Bu işlevsellik yalnızca seçtiyseniz gereklidir **sunucu tanımlama bilgisinin süresinin her tekrar oturum açmasını gerektiren** uygulama yapılandırma. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Kimlik doğrulaması başarılı olursa, istemci kimlik doğrulama sağlayıcısını ayarlar <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> örneği özelliğine <xref:System.Web.ClientServices.ClientRolePrincipal> sınıfı. Bu sınıf uygulayan <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi böylece iş yapılandırılmış rol sağlayıcısı için temsilci. Olarak önce uygulama kodunuzun hizmet sağlayıcısı için doğrudan bir başvuru gerektirmez.  
  
 Şimdi uygulamayı çalıştırın ve düğmesi değil görünür ve düğmesini görmek için yönetici olarak oturum açın, görmek için çalışan olarak oturum açın.  
  
## <a name="accessing-web-settings"></a>Web ayarlarına erişme  
 Aşağıdaki yordamda forma bir metin kutusu ekleyin ve bir Web ayarı bağlayın. Kimlik doğrulama ve roller kullanan önceki kod gibi ayarları kodunuzu ayarları sağlayıcısı doğrudan erişmez. Bunun yerine, türü kesin belirlenmiş kullanır `Settings` sınıfı (olarak erişilen `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te) projeniz için Visual Studio tarafından oluşturulur.  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Kullanıcı arabiriminde Web ayarlarını kullanmak için  
  
1.  Olduğundan emin olun **ASP.NET Web geliştirme sunucusu** görev çubuğunun bildirim alanına denetleyerek hala çalışıyor. Sunucu durdurduysanız (hangi sunucu otomatik olarak başlar) uygulama yeniden başlatıldıktan sonra oturum açma iletişim kutusunu kapatın.  
  
2.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projesini seçin ve ardından **proje** menüsünde, select **ClientAppServicesDemo özellikleri**.  
  
     Proje Tasarımcısı görünür.  
  
3.  Üzerinde **ayarları** sekmesini tıklatın, **yük Web ayarları**.  
  
     A **oturum açma** iletişim kutusu görüntülenir.  
  
4.  Çalışan veya Yöneticisi ve tıklatın için kimlik bilgilerini girin **oturum**. Kullanacağınız Web ayarı şekilde tıklatarak erişim için yalnızca kimliği doğrulanmış kullanıcılar tarafından yapılandırılan **Atla oturum açma** herhangi bir ayarı yüklemez.  
  
     `WebSettingsTestText` Ayar görünür, varsayılan değeriyle Tasarımcısı'nda `DefaultText`. Ayrıca, bir `Settings` içeren sınıf bir `WebSettingsTestText` özelliği, projeniz için oluşturulur.  
  
5.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projede Form1 seçin ve ardından **Görünüm &#124; Tasarımcısı** Visual Studio ana menüden.  
  
6.  Tasarımcıda eklemek bir <xref:System.Windows.Forms.TextBox> forma denetim.  
  
7.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `webSettingsTestTextBox`.  
  
8.  Kod Düzenleyicisi'nde sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi.  
  
     Bu kod çağırır `BindWebSettingsTestTextBox` sonraki adımda ekleyeceksiniz yöntemi.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Aşağıdaki yöntem Form1 sınıfı sonuna ekleyin.  
  
     Bu yöntem bağlar <xref:System.Windows.Forms.TextBox.Text%2A> özelliği `webSettingsTestTextBox` için `WebSettingsTestText` özelliği `Settings` bu yordamda daha önce oluşturulan sınıf. Bu yöntem aynı zamanda bir hata iletisi görüntüler bir <xref:System.Net.WebException> oluşturulur, Web ayarları hizmeti kullanılamaz olduğunu gösterir.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Veri bağlama genellikle bir denetim ve Web ayarı arasındaki otomatik çift yönlü iletişimi etkinleştirmek için de kullanır. Ancak, doğrudan olarak aşağıdaki örnekte gösterilen Web ayarları erişebilirsiniz:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. Form Tasarımcısı'nda seçin ve ardından **özellikleri** penceresinde tıklatın **olayları** düğmesi.  
  
11. Seçin <xref:System.Windows.Forms.Form.FormClosing> olayı ve bir olay işleyicisi oluşturmak için ENTER tuşuna basın.  
  
12. Oluşturulan yöntemini aşağıdaki kodla değiştirin.  
  
     <xref:System.Windows.Forms.Form.FormClosing> Olay işleyicisi çağrılarını `SaveSettings` sonraki bölümde ekleyeceksiniz oturum kapatma işlevi tarafından da kullanılan yöntem. `SaveSettings` Yöntemi ilk olarak onaylar ve kullanıcı oturum değil. Bunu denetleyerek yapar <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> özelliği <xref:System.Security.Principal.IIdentity> tarafından geçerli sorumlu döndürdü. Geçerli sorumlu üzerinden alınan `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği. Kullanıcı için istemci uygulama hizmetleri kimlik doğrulaması gerekiyorsa, kimlik doğrulama türü "ClientForms" olacaktır. `SaveSettings` Yöntemi yalnızca denetleyemez <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> özelliği kullanıcı oturum kapatma sonra geçerli bir Windows kimliği olabileceğinden.  
  
     Kullanıcı, oturum olmayan `SaveSettings` yöntem çağrılarını <xref:System.Configuration.ApplicationSettingsBase.Save%2A> yöntemi `Settings` bu yordamda daha önce oluşturulan sınıf. Bu yöntem atabilirsiniz bir <xref:System.Net.WebException> kimlik doğrulama tanımlama bilgisi dolmuşsa. Yalnızca seçtiyseniz bu gerçekleşir **sunucu tanımlama bilgisinin süresinin her tekrar oturum açmasını gerektiren** uygulama yapılandırma. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). `SaveSettings` Yöntemini çağırarak tanımlama bilgisinin süre sonu işleme <xref:System.Web.Security.Membership.ValidateUser%2A> oturum açma iletişim kutusunu görüntüleyin. Kullanıcı başarıyla oturum açarsa, `SaveSettings` yöntemi çalıştığında kendisini çağırarak ayarları yeniden kaydetmek.  
  
     Önceki kodda gibi `SaveSettings` yöntemi uzaktan hizmeti kullanılamıyorsa bir hata iletisi görüntüler. Uzak hizmet ayarları sağlayıcısı erişemiyorsanız, ayarlar hala yerel önbelleğe kaydedilen ve uygulama yeniden başlatıldığında yeniden yüklendi.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Aşağıdaki yöntem Form1 sınıfı sonuna ekleyin.  
  
     Bu kod işleme <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> olay ve ayarları varsa bir uyarı kaydedilemedi görüntüler. <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> Ayarları hizmeti kullanılamıyorsa veya kimlik doğrulama tanımlama bilgisi dolmuşsa olay oluşmaz. Ne zaman bir örneği <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> olay olan kullanıcı zaten oturum durumunda gerçekleşir. Oturum kapatma kodu ekleyerek bu olay işleyicisi sınayabilirsiniz `SaveSettings` önce doğrudan yöntemi <xref:System.Configuration.ApplicationSettingsBase.Save%2A> yöntem çağrısı. Kullanabileceğiniz oturum kapatma kodu sonraki bölümde açıklanmıştır.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. C# ' ta sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi. Bu kodu ile son adımda eklediğiniz yöntemi ilişkilendirir <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> olay.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Bu noktada uygulamayı test etmek için çalıştırın birden çok kez çalışan ve Yöneticisi ve farklı değerler metin kutusuna yazın. Değerleri, kullanıcı başına temelinde oturumlar arasında korunur.  
  
## <a name="implementing-logout"></a>Oturum kapatma uygulama  
 Kullanıcı seçtiğinde **Beni anımsa** uygulama olacaktır, otomatik olarak oturum açarken kutuyu sonraki çalıştırır kullanıcı kimlik doğrulaması. Otomatik kimlik doğrulama uygulaması çevrimdışı moddayken veya kimlik doğrulama tanımlama bilgisi süresi doluncaya kadar devam eder. Bazı durumlarda, ancak, birden çok kullanıcının uygulamaya erişim gerekir veya tek bir kullanıcı ara sıra farklı kimlik bilgileriyle oturum. Bu senaryoyu etkinleştirmek için aşağıdaki yordamda açıklandığı gibi oturum kapatma işlevselliği uygulamalıdır.  
  
#### <a name="to-implement-logout-functionality"></a>Oturum kapatma işlevselliği uygulamak için  
  
1.  Form1 Tasarımcısı'nda eklemek bir <xref:System.Windows.Forms.Button> formdan denetimine **araç**.  
  
2.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `logoutButton` ve **metin** değerini **& Log Out**.  
  
3.  Çift `logoutButton` oluşturmak için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
     Kod Düzenleyicisi imleç görünür `logoutButton_Click` yöntemi.  
  
4.  Oluşturulan Değiştir `logoutButton_Click` aşağıdaki kod ile yöntemi.  
  
     Bu olay işleyicisi önce çağırır `SaveSettings` önceki bölümde eklediğiniz yöntemi. Ardından, olay işleyici çağırması <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> yöntemi. Kimlik doğrulama hizmeti kullanılamıyorsa, <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> yöntemi oluşturur bir <xref:System.Net.WebException>. Bu durumda, `logoutButton_Click` yöntemi geçer geçici olarak çevrimdışı moda kullanıcı oturumu ve bir uyarı iletisi görüntüler. Çevrimdışı modda bir sonraki bölümde açıklanmıştır.  
  
     Uygulama yeniden başlatıldığında, oturum açma gerekli olacak şekilde oturum kapatma yerel kimlik doğrulama tanımlama bilgisi siler. Oturum kapatma sonra uygulama olay işleyicisini yeniden başlatır. Uygulama yeniden başlatıldığında, oturum açma iletişim kutusu tarafından izlenen Hoş Geldiniz iletisi görüntüler. Hoş Geldiniz iletisi temizleyin, uygulama yeniden başlatıldıktan kolaylaştırır. Bu, kullanıcı ayarlarını kaydetmek için oturum gerekir ve çünkü uygulama yeniden başlatıldıktan sonra yeniden oturum gerekir, olası karışıklığı engeller.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 Oturum kapatma işlevselliğini sınamak için uygulamayı çalıştırın ve seçin **Beni anımsa** oturum açma iletişim kutusunda. Ardından, kapatın ve, artık oturum açmaya sahip olduğunuzu onaylamak için uygulamayı yeniden başlatın. Son olarak, uygulama günlüğü tıklayarak yeniden başlatın.  
  
## <a name="enabling-offline-mode"></a>Çevrimdışı modda etkinleştirme  
 Aşağıdaki yordamda, forma çevrimdışı modda girmesini etkinleştirmek için bir onay kutusu ekleyin. Uygulamanızı çevrimdışı modda ayarlayarak gösterir `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> özelliğine `true`. Çevrimdışı durum tarafından belirtilen konumda yerel sabit diskte depolanan <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> özelliği. Başka bir deyişle, çevrimdışı durumunu bir üzerinde kullanıcı başına, uygulama başına temelinde depolanır.  
  
 Çevrimdışı modda, tüm istemci uygulama hizmet isteklerini hizmetlere erişmek denemek yerine yerel önbellek verilerini alma. Varsayılan yapılandırmada, kullanıcının parolasının şifrelenmiş biçimde yerel veriler içerir. Bu uygulamayı çevrimdışı moddayken oturum açmak kullanıcının sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Uygulamanızı çevrimdışı modda etkinleştirmek için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projede Form1 seçin ve ardından **Görünüm &#124; Tasarımcısı** Visual Studio ana menüden.  
  
2.  Tasarımcıda eklemek bir <xref:System.Windows.Forms.CheckBox> forma denetim.  
  
3.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `workOfflineCheckBox` ve **metin** değerini **& iş çevrimdışı**.  
  
4.  İçinde **özellikleri** penceresinde tıklatın **olayları** düğmesi.  
  
5.  Seçin <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayı ve bir olay işleyicisi oluşturmak için ENTER tuşuna basın.  
  
6.  Oluşturulan yöntemini aşağıdaki kodla değiştirin.  
  
     Bu kod güncelleştirmeleri <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> değer ve kullanıcının çevrimiçi moda döndüğünüzde sessiz bir şekilde yeniden doğrular. <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> Yöntemi, böylece açıkça oturum açmak kullanıcının yok önbelleğe alınmış kimlik bilgilerini kullanır. Kimlik doğrulama hizmeti kullanılamıyorsa bir uyarı iletisi görüntülenir ve uygulama çevrimdışı kalır.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> Yalnızca kolaylık sağlamak için bir yöntemdir. Dönüş değeri sahip olmadığından yeniden doğrulanması başarısız olup olmadığını belirtemez. Örneğin, kullanıcı kimlik bilgilerini sunucuda değiştirdiyseniz yeniden doğrulanması başarısız olabilir. Bu durumda, bir hizmeti çağrısı başarısız olduktan sonra kullanıcılar açıkça doğrulama kodu eklemek isteyebilirsiniz. Daha fazla bilgi için bu kılavuzda daha önce erişme Web ayarları bölümüne bakın.  
  
     Yeniden doğrulanması sonra bu kodu değişiklikleri yerel Web ayarları çağırarak kaydeder `SaveSettings` daha önce eklediğiniz yöntemi. Çağırarak sonra sunucuda yeni değerleri alır <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> projenin yöntemi `Settings` sınıfı (olarak erişilen `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi onay kutusunu geçerli bağlantı durumunu görüntülediğinden emin olun.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Bu örnek uygulama tamamlar. Çevrimdışı özelliği test etmek için uygulamayı çalıştırın, çalışan veya yönetici oturum ve ardından **Çevrimdışı Çalış**. Metin kutusundaki değeri değiştirin ve sonra da uygulamayı kapatın. Uygulamayı yeniden başlatın. Oturum açmadan önce görev çubuğu bildirim alanında ASP.NET Geliştirme Sunucusu simgesine sağ tıklayın ve ardından **durdurmak**. Ardından, normal gibi oturum açın. Sunucu bile çalışmadığı zaman, hala oturum açabilir. Metin kutusu değerini, çıkış ve değiştirilen değeri görmek için yeniden başlatma değiştirin.  
  
## <a name="summary"></a>Özet  
 Bu kılavuzda, etkinleştirme ve istemci uygulama hizmetleri bir Windows Forms uygulamasında kullanma öğrendiniz. Bir test sunucuyu ayarladıktan sonra kullanıcıların kimliğini doğrulamak ve kullanıcı rolleri ve uygulama ayarlarını sunucudan almak için uygulamanızı kod eklenir. Ayrıca bağlantı olmadığında uygulamanızı yerel veri önbelleği yerine uzak hizmetlerini kullanır. böylece çevrimdışı modunu etkinleştirmek öğrendiniz.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Gerçek dünya uygulamasında her zaman kullanılabilir durumda olmayabilir veya bildirilmeksizin gidebilir uzak bir sunucudan çok sayıda kullanıcı için veri erişim. Uygulamanızı sağlam hale için hizmetin kullanılabilir olduğu durumlar için uygun şekilde yanıt vermelidir. Bu kılavuzda yakalamak için try/catch blokları içeren bir <xref:System.Net.WebException> ve hizmet bulunmaması durumunda bir hata iletisi görüntülenir. Üretim kodunda çevrimdışı moda geçişi, uygulamadan çıkmak veya belirli işlevlere erişimi engelleme bu durumun üstesinden isteyebilirsiniz.  
  
 Uygulamanızın güvenliğini artırmak için uygulama ve sunucu dağıtmadan önce sınamanız emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Uygulama Servisleri](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [İstemci Uygulama Servislerine Genel Bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [ASP.NET Web sitesi yönetim aracı](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Oluşturma ve uygulama hizmetleri veritabanına SQL Server için yapılandırma](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [İzlenecek yol: ASP.NET uygulama hizmetlerini kullanma](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
