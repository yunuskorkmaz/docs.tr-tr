---
title: 'İzlenecek Yol: İstemci Uygulama Hizmetlerini Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
ms.openlocfilehash: b800848fc3cefb1f82fb5822007bc670c1684363
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539898"
---
# <a name="walkthrough-using-client-application-services"></a>İzlenecek Yol: İstemci Uygulama Hizmetlerini Kullanma
Bu konuda, kullanıcıların kimliklerini doğrulamak ve kullanıcı rolleri ile ayarları almak için istemci uygulama hizmetleri kullanan bir Windows uygulaması oluşturma işlemini açıklar.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Bir Windows Forms uygulaması oluşturma ve etkinleştirme ve istemci uygulama hizmetleri yapılandırmak için Visual Studio Proje Tasarımcısı'nı kullanın.  
  
-   Uygulama hizmetleri barındırır ve istemci yapılandırmanızı test etmek için basit bir ASP.NET Web hizmeti uygulaması oluşturun.  
  
-   Form kimlik doğrulaması için uygulamanızı ekleyin. Hizmeti test etmek için bir sabit kodlanmış kullanıcı adı ve parola kullanarak başlar. Ardından, uygulama yapılandırmanız bir kimlik sağlayıcısı olarak belirterek bir oturum açma formu ekleyeceksiniz.  
  
-   Etkinleştirme ve kullanıcılar için yalnızca bir düğmeye "Yönetici" rolünde görüntüleyerek rol tabanlı işlevselliği ekleyin.  
  
-   Web ayarları erişin. Şirket Web ayarları (test) kimliği doğrulanmış kullanıcı için yüklemeye başlar. **ayarları** sayfası Proje Tasarımcısı. Sonra bir metin kutusu için bir Web ayar bağlamak için Windows Form Tasarımcısı'nı kullanır. Son olarak, değiştirilmiş değer sunucuya geri kaydeder.  
  
-   Oturum kapatma uygulayın. Bir oturum kapatma seçeneği forma ekleyin ve oturum kapatma yöntemini çağırın.  
  
-   Çevrimdışı modunu etkinleştirin. Böylece kullanıcılar kendi bağlantı durumunu belirleyebilir, bir onay kutusu sağlar. Ardından, istemci uygulama hizmet sağlayıcıları kendi Web hizmetlerine erişme yerine yerel olarak önbelleğe alınmış verileri kullanıp kullanmayacağını belirtmek için bu değeri kullanır. Son olarak, uygulama çevrimiçi moda geri döndüğünde geçerli kullanıcının yeniden kimliğini doğrular.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşen ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>İstemci Uygulamasını Oluşturma  
 Yapacağınız ilk şey, bir Windows Forms projesi oluşturmaktır. Bu izlenecek yol, daha fazla insana kendisiyle ilgili bilgi sahibi olduğunuz, ancak işlemi için Windows Presentation Foundation (WPF) projelerini benzer çünkü Windows Forms kullanır.  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>İstemci uygulaması oluşturma ve istemci uygulama hizmetlerini etkinleştirmek için  
  
1.  Visual Studio'da **dosya &#124; yeni &#124; proje** menü seçeneği.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesini genişletin **Visual Basic** veya **Visual C#** düğüm ve select **Windows** proje türü.  
  
3.  Emin olun **.NET Framework 3.5** seçili ve ardından **Windows Forms uygulaması** şablonu.  
  
4.  Proje Değiştir **adı** için `ClientAppServicesDemo`ve ardından **Tamam**.  
  
     Yeni bir Windows Forms projesi Visual Studio'da açılır.  
  
5.  Üzerinde **proje** menüsünde **ClientAppServicesDemo özellikleri**.  
  
     Proje Tasarımcısı görüntülenir.  
  
6.  Üzerinde **Hizmetleri** sekmesinde **istemci uygulama hizmetlerini etkinleştirmek**.  
  
7.  Emin olun **formlar kimlik doğrulama** seçilir ve ardından **kimlik doğrulama hizmet konumu**, **rolleri hizmet konumu**, ve **Web ayarları hizmet konumu** için `http://localhost:55555/AppServices`.  
  
8.  Visual Basic'te üzerinde **uygulama** sekmesinde, belirleyin **kimlik doğrulama modu** için **uygulama tanımlı**.  
  
 Tasarımcı belirtilen ayarlar uygulamanın app.config dosyasında depolar.  
  
 Bu noktada uygulama, tüm üç hizmeti ana bilgisayardan erişmek için yapılandırılmıştır. Sonraki bölümde, böylece istemci yapılandırmanızı test etme basit bir Web hizmeti uygulama, ana bilgisayar oluşturur.  
  
## <a name="creating-the-application-services-host"></a>Uygulama Hizmetleri konağı oluşturma  
 Bu bölümde, kullanıcı verilerini yerel bir SQL Server Compact veritabanı dosyası erişen basit bir Web hizmeti uygulaması oluşturacaksınız. Ardından, veritabanını kullanarak doldurulur [ASP.NET Web sitesi yönetim aracı](https://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Bu basit bir yapılandırma, hızlı bir şekilde istemci uygulamanızı test etmek sağlar. Alternatif olarak, Web hizmeti konak tam SQL Server veritabanından veya özel aracılığıyla kullanıcı verilerine erişmek için yapılandırabileceğiniz <xref:System.Web.Security.MembershipProvider> ve <xref:System.Web.Security.RoleProvider> sınıfları. Daha fazla bilgi için [oluşturma ve uygulama hizmetleri veritabanına SQL Server için yapılandırma](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 Aşağıdaki yordamda, oluşturun ve AppServices Web hizmetini yapılandırın.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Oluşturma ve uygulama hizmetleri konağı yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo çözümü seçin ve ardından **dosya** menüsünde **Ekle &#124; yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusundaki **proje türleri** bölmesini genişletin **Visual Basic** veya **Visual C#** düğüm ve seçin **Web** proje türü.  
  
3.  Emin olun **.NET Framework 3.5** seçili ve ardından **ASP.NET Web hizmeti uygulama** şablonu.  
  
4.  Proje Değiştir **adı** için `AppServices` ve ardından **Tamam**.  
  
     Yeni bir ASP.NET Web hizmeti uygulaması projesi çözüme eklenir ve Service1.asmx.vb veya Service1.asmx.cs dosya Düzenleyicisi'nde görünür.  
  
    > [!NOTE]
    >  Bu örnekte Service1.asmx.vb veya Service1.asmx.cs dosyasını kullanılmaz. Çalışma ortamınızda sade tutmak istiyorsanız, kapatın ve silmek **Çözüm Gezgini**.  
  
5.  İçinde **Çözüm Gezgini**, AppServices projeyi seçin ve ardından **proje** menüsünde **AppServices özellikleri**.  
  
     Proje Tasarımcısı görüntülenir.  
  
6.  Üzerinde **Web** sekmesinde, emin olun **kullanım Visual Studio geliştirme sunucusu** seçilir.  
  
7.  Seçin **belirli bağlantı noktası**, değerini belirtirseniz `55555`ve ardından **sanal yolu** için `/AppServices`.  
  
8.  Tüm dosyaları kaydedin.  
  
9. İçinde **Çözüm Gezgini**, Web.config dosyasını açın ve bulma `<system.web>` etiketiyle.  
  
10. Önce aşağıdaki işaretlemeyi ekleyin `<system.web>` etiketi.  
  
     `authenticationService`, `profileService`, Ve `roleService` bu işaretleme öğeleri etkinleştirin ve uygulama hizmetlerini yapılandırın. Sınama amacıyla, `requireSSL` özniteliği `authenticationService` öğesi, "false" olarak ayarlanır. `readAccessProperties` Ve `writeAccessProperties` özniteliklerini `profileService` öğe belirtmek `WebSettingsTestText` okuma/yazma özelliğidir.  
  
    > [!NOTE]
    >  Üretim kodunda, kimlik doğrulama hizmeti her zaman Güvenli Yuva Katmanı (HTTPS protokolü kullanarak SSL) üzerinden erişmelidir. SSL kurma hakkında daha fazla bilgi için bkz: [Güvenli Yuva Katmanı Yapılandırma (IIS 6.0 işlemler Kılavuzu)](https://go.microsoft.com/fwlink/?LinkId=91844).  
  
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
  
11. Sonra aşağıdaki işaretlemeyi ekleyin `<system.web>` içinde böylece etiketiyle `<system.web>` öğesi.  
  
     `profile` Öğesi yapılandırır adlı ayar tek bir Web `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 Aşağıdaki yordamda, hizmet yapılandırmasını tamamlayın ve yerel veritabanı dosyasındaki doldurmak için ASP.NET Web Sitesi Yönetim Aracı'nı kullanın. Adlı iki kullanıcı ekleyeceksiniz `employee` ve `manager` aynı ada sahip iki rollere ait. Kullanıcı parolaları `employee!` ve `manager!` sırasıyla.  
  
#### <a name="to-configure-membership-and-roles"></a>Üyelik ve rolleri yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, AppServices projeyi seçin ve ardından **proje** menüsünde **ASP.NET yapılandırma**.  
  
     **ASP.NET Web sitesi yönetim aracı** görünür.  
  
2.  Üzerinde **güvenlik** sekmesinde **Güvenlik Kurulum Sihirbazı adım adım güvenliği yapılandırmak için kullanmak**.  
  
     **Güvenlik Kurulum Sihirbazı'nı** görünür ve görüntüler **Hoş Geldiniz** adım.  
  
3.  **İleri**'ye tıklayın.  
  
     **Erişim yöntemi seçin** adımı görüntülenir.  
  
4.  Seçin **internet'ten**. Bu, form kimlik doğrulaması Windows kimlik doğrulaması yerine kullanılacak hizmeti yapılandırır.  
  
5.  Tıklayın **sonraki** iki kez.  
  
     **Rolleri tanımlama** adımı görüntülenir.  
  
6.  Seçin **etkinleştirmek için bu Web sitesi rolleri**.  
  
7.  **İleri**'ye tıklayın. **Yeni Rol Oluştur** formu görüntülenir.  
  
8.  İçinde **yeni rol adı** metin kutusunda, `manager` ve ardından **Rol Ekle**.  
  
     **Var olan rolleri** tablo belirtilen değerle görünür.  
  
9. İçinde **yeni rol adı** metin kutusunda, yerine `manager` ile `employee` ve ardından **Rol Ekle**.  
  
     Yeni bir değer görünür **var olan rolleri** tablo.  
  
10. **İleri**'ye tıklayın.  
  
     **Yeni kullanıcı Ekle** adımı görüntülenir.  
  
11. İçinde **Create User** formunda, aşağıdaki değerleri belirtin.  
  
  	|||  
  	|-|-|  
  	|**Kullanıcı adı**|`manager`|  
  	|**Parola**|`manager!`|  
  	|**Parolayı onaylayın**|`manager!`|  
  	|**E-posta**|`manager@contoso.com`|  
  	|**Güvenlik sorusu**|`manager`|  
  	|**Güvenlik yanıtı**|`manager`|  
  
12. Tıklayın **oluşturacağı**.  
  
     Başarılı iletisi görüntülenir.  
  
    > [!NOTE]
    >  **E-posta**, **Güvenlik sorusu**, ve **güvenlik yanıtı** değerler formu tarafından gerekli, ancak bu örnekte kullanılmaz.  
  
13. 
              **Devam**'a tıklayın.  
  
     **Create User** formu yeniden görüntülenir.  
  
14. İçinde **Create User** formunda, aşağıdaki değerleri belirtin.  
  
  	|||  
  	|-|-|  
  	|**Kullanıcı adı**|`employee`|  
  	|**Parola**|`employee!`|  
  	|**Parolayı onaylayın**|`employee!`|  
  	|**E-posta**|`employee@contoso.com`|  
  	|**Güvenlik sorusu**|`Employee`|  
  	|**Güvenlik yanıtı**|`employee`|  
  
15. Tıklayın **oluşturacağı**.  
  
     Başarılı iletisi görüntülenir.  
  
16. **Son**'a tıklayın.  
  
     **Web sitesi yönetim aracı** yeniden görüntülenir.  
  
17. Tıklayın **Yöneticisi kullanıcıları**.  
  
     Kullanıcıların listesi görünür.  
  
18. Tıklayın **rolleri düzenleme** için **çalışan** kullanıcı tıklayın ve ardından **çalışan** rol.  
  
19. Tıklayın **rolleri düzenleme** için **manager** kullanıcı tıklayın ve ardından **manager** rol.  
  
20. Barındıran tarayıcı penceresini kapatın **Web sitesi yönetim aracı**.  
  
21. Değiştirilen Web.config dosyasını yeniden yüklemek istiyorsanız, tıklayın isteyen bir ileti kutusu görüntülenirse **Evet**.  
  
 Bu Web hizmeti Kurulumu tamamlanır. Bu noktada, istemci uygulamasını çalıştırmak için F5 tuşuna basarak ve **ASP.NET Geliştirme Sunucusu** yanı sıra istemci uygulamanızı otomatik olarak başlatılacak. Sunucu sonra uygulamadan çıkın, ancak uygulama yeniden başlatıldığında yeniden çalışmaya devam eder. Bu durum, Web.config dosyasına yapmış olduğunuz değişiklikleri algılamak sağlar.  
  
 El ile sunucu durdurmak için görev çubuğu bildirim alanında ASP.NET Geliştirme Sunucusu simgesine sağ tıklayın ve ardından **Durdur**. Bu, bazen temiz bir yeniden başlatma oluştuğunu emin olmak kullanışlıdır.  
  
## <a name="adding-forms-authentication"></a>Form kimlik doğrulaması ekleme  
 Aşağıdaki yordamda, kodu kullanıcı doğrulamayı dener ve kullanıcı geçersiz kimlik bilgileri sağladığı zaman erişimini engellediği ana formu ekleyin. Hizmeti test etmek için bir sabit kodlanmış kullanıcı adı ve parola kullanın.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>Uygulama kodunuzda kullanıcıyı doğrulamak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projesinde System.Web derlemesine bir başvuru ekleyin.  
  
2.  Form1 dosyasını seçin ve ardından **görünümü &#124; kod** Visual Studio ana menüden.  
  
3.  Kod Düzenleyicisi'nde Form1 dosyasının en üstüne aşağıdaki deyimleri ekleyin.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  İçinde **Çözüm Gezgini**, Form1 Tasarımcı görüntülemek için çift tıklayın.  
  
5.  Tasarımcıda oluşturmak için form yüzeyi çift bir <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> adlı olay işleyicisi `Form1_Load`.  
  
     İmleç ile Kod Düzenleyicisi görünür `Form1_Load` yöntemi.  
  
6.  Aşağıdaki kodu ekleyin `Form1_Load` yöntemi.  
  
     Bu kod, uygulamanın çıkarak, kimliği doğrulanmamış kullanıcılar için erişimi engeller. Alternatif olarak, kimliği doğrulanmamış kullanıcılar formun erişmesine ancak belirli işlevlerine erişimi reddet. Normalde, sabit kodlu kullanıcı adı ve parola böyle, ancak test amacıyla yararlıdır. Sonraki bölümde, bir oturum açma iletişim kutusu görüntüler ve özel durum işleme içeren daha güçlü kodla bu kod yerini alır.  
  
     Unutmayın `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi konusu [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Bu yöntem kendi iş için yapılandırılan kimlik doğrulama sağlayıcısı atar ve döndürür `true` kimlik doğrulaması başarılı olursa. Uygulamanız, istemci kimlik doğrulama sağlayıcısı için bir doğrudan başvuru gerektirmez.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Şimdi uygulamayı çalıştırmak için F5 tuşuna basarak ve doğru kullanıcı adını ve parolayı sağladığından, formu görürsünüz.  
  
> [!NOTE]
>  Uygulamayı çalıştırmak ASP.NET Geliştirme Sunucusu durdurma deneyin. Sunucu yeniden başlatıldıktan sonra bağlantı noktası için 55555 ayarlandığını doğrulayın.  
  
 Bunun yerine hata iletisini görmek isterseniz değiştirme <xref:System.Web.Security.Membership.ValidateUser%2A> parametreleri. Örneğin, ikinci değiştirin `"manager!"` parametresi yanlış bir parolayla ister `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Oturum açma formu, bir kimlik sağlayıcısı olarak ekleme  
 Uygulama kodunuzda kullanıcı kimlik bilgilerini almak ve bunları geçirmek <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi. Ancak, genellikle daha sonra değiştirmek istediğiniz durumlarda kimlik bilgileri alınırken kodunuzu uygulama kodunuzdan ayrı tutmak kullanışlıdır.  
  
 Aşağıdaki yordamda, bir kimlik sağlayıcısı kullanın ve sonra değiştirmek için uygulamanızı yapılandırma, <xref:System.Web.Security.Membership.ValidateUser%2A> geçirmek için yöntem çağrısının <xref:System.String.Empty> parametre için de. Boş dizeler sinyal <xref:System.Web.Security.Membership.ValidateUser%2A> çağrılacak yöntem <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi yapılandırılmış kimlik sağlayıcısı.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Uygulamanızı bir kimlik sağlayıcısı kullanacak şekilde yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projeyi seçin ve ardından **proje** menüsünde **ClientAppServicesDemo özellikleri**.  
  
     Proje Tasarımcısı görüntülenir.  
  
2.  Üzerinde **Hizmetleri** sekmesinde, belirleyin **isteğe bağlı: kimlik bilgisi sağlayıcı** aşağıdaki değer. Bu değer, derleme nitelikli tür adı gösterir.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  Form1 kod dosyasında değiştirin `Form1_Load` yöntemini aşağıdaki kod ile.  
  
     Bu kod bir karşılama iletisi görüntüleyecek ve `ValidateUsingCredentialsProvider` sonraki adımda eklenecek yöntemi. Kullanıcının kimliği doğrulanmazsa `ValidateUsingCredentialsProvider` yöntemi döndürür `false` ve `Form1_Load` yöntemi döndürür. Bu, herhangi bir ek kod uygulama çıktıktan önce çalışmasını engeller. Hoş Geldiniz iletisi, uygulama yeniden başlatıldığında Temizle sağlamak kullanışlıdır. Bu izlenecek yolda, oturum kapatma uyguladığınızda uygulamanın yeniden başlatmak için kod ekleyeceksiniz.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Sonra aşağıdaki yöntemi ekleyin `Form1_Load` yöntemi.  
  
     Bu yöntem boş dizeler geçirir `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi oturum açma iletişim kutusunun görünmesini neden olur. Kimlik doğrulama hizmeti kullanılamıyorsa <xref:System.Web.Security.Membership.ValidateUser%2A> yöntemi oluşturur bir <xref:System.Net.WebException>. Bu durumda, `ValidateUsingCredentialsProvider` yöntemi bir uyarı iletisi görüntüler ve kullanıcının çevrimdışı modda yeniden denemek isteyip istemediğini sorar. Bu işlevsellik gerektirir **çevrimdışı oturum açma yerel olarak etkinleştirmek için parola karması Kaydet** özellik açıklanan [nasıl yapılır: istemci uygulama servislerini yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Bu özellik, yeni projeler için varsayılan olarak etkindir.  
  
     Kullanıcı doğrulanmazsa `ValidateUsingCredentialsProvider` yöntemi bir hata iletisi görüntüler ve uygulamadan çıkar. Son olarak, bu yöntem, kimlik doğrulama girişiminin sonucunu döndürür.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Bir oturum açma formu oluşturma  
 Bir kimlik sağlayıcısı uygulayan sınıftır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi. Bu arabirim adlı tek bir yöntem olan <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> döndüren bir <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> nesne. Aşağıdaki yordamlar uygulayan bir oturum açma iletişim kutusu oluşturma işlemini açıklar <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> kendisini görüntülemek ve kullanıcı tarafından belirtilen kimlik bilgilerini döndürmek için.  
  
 Ayrı yordamları sağlanan Visual Basic ve C# için Visual Basic sağladığından bir **oturum açma formu** şablonu. Bu biraz zaman ve çaba kodlama kaydeder.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Visual Basic'te bir kimlik sağlayıcısı oturum açma iletişim kutusu oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projeyi seçin ve ardından **proje** menüsünde **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **oturum açma formu** şablonu, öğeyi değiştirmek **adı** için `Login.vb`ve ardından **Ekle** .  
  
     Windows Form Tasarımcısı'nda oturum açma iletişim kutusu görünür.  
  
3.  Tasarımcıda seçin **Tamam** düğmesine ve ardından **özellikleri** penceresinde `DialogResult` için `OK`.  
  
4.  Tasarımcıda ekleme bir `CheckBox` altında forma **parola** metin kutusu.  
  
5.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `rememberMeCheckBox` ve **metin** değerini `&Remember me`.  
  
6.  Seçin **görünümü &#124; kod** Visual Studio ana menüden.  
  
7.  Kod Düzenleyicisi'nde dosyasının en üstüne aşağıdaki kodu ekleyin.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Sınıf uygulayan sınıfı imzası değiştirin <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. İmleç sonra olduğundan emin olun `IClientformsAuthenticationCredentialsProvider`, ve oluşturmak için ENTER tuşuna basın `GetCredentials` yöntemi.  
  
10. Bulun <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> uygulama aşağıdaki kodla değiştirin.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 Aşağıdaki C# yordamı tüm kod için bir basit bir oturum açma iletişim kutusu listesini sağlar. Bu iletişim kutusu düzenini biraz kaba olsa da önemli bir parçasıdır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> uygulaması.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>C# dilinde bir kimlik sağlayıcısı oturum açma iletişim kutusu oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projeyi seçin ve ardından **proje** menüsünde **sınıfı Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, değişiklik **adı** için `Login.cs`ve ardından **Ekle**.  
  
     Login.cs dosyası Kod Düzenleyicisi'nde açılır.  
  
3.  Varsayılan kodu aşağıdaki kodla değiştirin.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Şimdi uygulamayı çalıştırın ve oturum açma iletişim kutusu görünür. Bu kodu test etmek için farklı kimlik bilgileri, geçerli ve geçersiz, deneyin ve formu yalnızca geçerli kimlik bilgileriyle erişebileceğiniz onaylayın. Geçerli kullanıcı adları `employee` ve `manager` parolalarla `employee!` ve `manager!` sırasıyla.  
  
> [!NOTE]
>  Seçmeyin **Beni Hatırla** bu noktaya veya siz bu kılavuzda daha sonra oturum kapatma uygulayana kadar başka bir kullanıcı oturum açmanız mümkün olmayacaktır.  
  
## <a name="adding-role-based-functionality"></a>Rol tabanlı işlevsellik ekleme  
 Aşağıdaki yordamda, forma bir düğme ekleyin ve yalnızca yönetici rolündeki kullanıcılar için görüntüler.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Kullanıcı rolü tabanlı kullanıcı arabirimi değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**Form1 ClientAppServicesDemo proje seçin ve ardından **görünümü &#124; Tasarımcısı** Visual Studio ana menüden.  
  
2.  Tasarımcıda ekleme bir <xref:System.Windows.Forms.Button> formu denetimine **araç kutusu**.  
  
3.  İçinde **özellikleri** penceresinde düğme için aşağıdaki özellikleri ayarlayın.  
  
  	|Özellik|Değer|  
  	|--------------|-----------|  
  	|**(Ad)**|managerOnlyButton|  
  	|**Metin**|& Yöneticisi görevi|  
  	|**Görünür**|`False`|  
  
4.  Form1 kod düzenleyicisinde sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi.  
  
     Bu kod `DisplayButtonForManagerRole` sonraki adımda eklenecek yöntemi.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Form1 sınıfı sonuna aşağıdaki yöntemi ekleyin.  
  
     Bu yöntemin çağırdığı <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi <xref:System.Security.Principal.IPrincipal> tarafından döndürülen `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği. İstemci uygulama hizmetleri kullanmak üzere yapılandırılmış uygulamalar için bu özellik döndürür bir <xref:System.Web.ClientServices.ClientRolePrincipal>. Bu sınıf uyguladığından <xref:System.Security.Principal.IPrincipal> arabirimi gerektirmeyen açıkça başvurmak.  
  
     Kullanıcı "Yönetici" rolünde, `DisplayButtonForManagerRole` yöntemi kümeleri <xref:System.Windows.Forms.Control.Visible%2A> özelliği `managerOnlyButton` için `true`. Bu yöntem Ayrıca, bir hata iletisi görüntüler bir <xref:System.Net.WebException> oluşturulur, rol hizmeti kullanılamaz olduğunu gösterir.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> Yöntemi her zaman döndürecektir `false` kullanıcı oturumunu dolmuşsa. Uygulamanız çağırıyorsa oluşmaz <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi bu izlenecek yol için örnek kodda gösterildiği gibi kısa bir süre sonra kimlik doğrulamasından sonra bir kez. Uygulamanız diğer zamanlarda kullanıcı rollerini almak gerekir, kullanıcılar, oturum açma doldu düzeltin için kod ekleyin isteyebilirsiniz. Tüm geçerli kullanıcılar rollere atanır, oturum açma çağırarak süresinin dolup dolmadığını belirleyebilirsiniz <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> yöntemi. Rol döndürdüyse oturum süresi doldu. Bu işlev bir örnek için bkz <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> yöntemi. Bu işlev yalnızca seçtiyseniz gereklidir **sunucu tanımlama bilgisi süresi her yeniden oturum açmasını gerektiren** uygulama yapılandırmanızda. Daha fazla bilgi için [nasıl yapılır: istemci uygulama servislerini yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Kimlik doğrulaması başarılı olursa, istemci kimlik doğrulama sağlayıcısı ayarlar <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> örneğine özellik <xref:System.Web.ClientServices.ClientRolePrincipal> sınıfı. Bu sınıfın uyguladığı <xref:System.Security.Principal.IPrincipal.IsInRole%2A> yöntemi böylece iş için yapılandırılan rol sağlayıcısını temsilci. Olarak önce uygulama kodunuz hizmet sağlayıcısına doğrudan bir başvuru gerektirmez.  
  
 Artık uygulamayı çalıştırabilir ve düğme değil görünür ve düğmeyi görmek için yönetici olarak oturum açın, görmek için çalışan olarak oturum açın.  
  
## <a name="accessing-web-settings"></a>Web ayarlarına erişme  
 Aşağıdaki yordamda, forma metin kutusu ekleyin ve bir Web ayarına bağlama. Kimlik doğrulama ve roller kullanan önceki kodu gibi ayarları kodunuzu ayar sağlayıcısı doğrudan erişmez. Bunun yerine, türü kesin belirlenmiş kullanır `Settings` sınıfı (erişilebilir `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te), projeniz için Visual Studio tarafından oluşturulan.  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Web ayarları, kullanıcı arabiriminde kullanmak için  
  
1.  Emin olun **ASP.NET Web geliştirme sunucusu** görev çubuğu bildirim alanında denetleyerek hala çalışıyor. Sunucu durursa, (hangi sunucu otomatik olarak başlar) uygulama yeniden başlatıldıktan sonra oturum açma iletişim kutusunu kapatın.  
  
2.  İçinde **Çözüm Gezgini**, ClientAppServicesDemo projeyi seçin ve ardından **proje** menüsünde **ClientAppServicesDemo özellikleri**.  
  
     Proje Tasarımcısı görüntülenir.  
  
3.  Üzerinde **ayarları** sekmesinde **yük Web ayarları**.  
  
     A **oturum açma** iletişim kutusu görüntülenir.  
  
4.  Çalışan veya Yöneticisi ve tıklatın için kimlik bilgilerini girin **oturum**. Kullanacağınız Web ayar şekilde tıklayarak için erişimi yalnızca kimliği doğrulanmış kullanıcılar tarafından yapılandırılmış **Atla oturum açma** herhangi bir ayarı yüklemez.  
  
     `WebSettingsTestText` Ayarı Tasarımcı varsayılan değeri ile görünür `DefaultText`. Ayrıca, bir `Settings` içeren sınıf bir `WebSettingsTestText` özelliği, projeniz için oluşturulur.  
  
5.  İçinde **Çözüm Gezgini**Form1 ClientAppServicesDemo proje seçin ve ardından **görünümü &#124; Tasarımcısı** Visual Studio ana menüden.  
  
6.  Tasarımcıda ekleme bir <xref:System.Windows.Forms.TextBox> forma.  
  
7.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `webSettingsTestTextBox`.  
  
8.  Kod Düzenleyicisi'nde sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi.  
  
     Bu kod `BindWebSettingsTestTextBox` sonraki adımda eklenecek yöntemi.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Form1 sınıfı sonuna aşağıdaki yöntemi ekleyin.  
  
     Bu yöntem bağlar <xref:System.Windows.Forms.TextBox.Text%2A> özelliği `webSettingsTestTextBox` için `WebSettingsTestText` özelliği `Settings` bu yordamda daha önce oluşturulan sınıf. Bu yöntem Ayrıca, bir hata iletisi görüntüler bir <xref:System.Net.WebException> oluşturulur, Web ayarları hizmeti kullanılamaz olduğunu gösterir.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Genellikle veri bağlama denetimi ve bir Web ayar arasında otomatik iki yönlü iletişim sağlamak için de kullanır. Ancak, doğrudan olarak aşağıdaki örnekte gösterilen Web ayarları da erişebilirsiniz:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. Form Tasarımcısı'nda seçin ve ardından **özellikleri** penceresinde tıklayın **olayları** düğmesi.  
  
11. Seçin <xref:System.Windows.Forms.Form.FormClosing> olay ve bir olay işleyicisi oluşturmak için ENTER tuşuna basın.  
  
12. Oluşturulan yöntemini aşağıdaki kodla değiştirin.  
  
     <xref:System.Windows.Forms.Form.FormClosing> Olay işleyicisi çağrılarını `SaveSettings` yöntemi, sonraki bölümde ekleyeceksiniz oturum kapatma işlevi tarafından kullanılır. `SaveSettings` Yöntemi önce doğrular ve kullanıcı oturum değil. Bunu kontrol ederek yapar <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> özelliği <xref:System.Security.Principal.IIdentity> tarafından geçerli sorumlu döndürdü. Geçerli sorumlu üzerinden alınan `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği. Kullanıcı istemci uygulama hizmetleri için kimlik doğrulaması gerekiyorsa, kimlik doğrulama türü "ClientForms" olacaktır. `SaveSettings` Yöntemi az önce denetleyemez <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> özelliği geçerli bir Windows kimliği oturum kapatma kullanıcının olabileceğinden.  
  
     Kullanıcı, oturum olmayan `SaveSettings` yöntem çağrılarını <xref:System.Configuration.ApplicationSettingsBase.Save%2A> yöntemi `Settings` bu yordamda daha önce oluşturulan sınıf. Bu yöntem oluşturabilecek bir <xref:System.Net.WebException> kimlik doğrulama tanımlama dolmuşsa. Yalnızca seçtiyseniz böyle **sunucu tanımlama bilgisi süresi her yeniden oturum açmasını gerektiren** uygulama yapılandırmanızda. Daha fazla bilgi için [nasıl yapılır: istemci uygulama servislerini yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). `SaveSettings` Yöntemi çağırarak tanımlama bilgisi süre sonunu işler <xref:System.Web.Security.Membership.ValidateUser%2A> oturum açma iletişim kutusunu görüntüleyin. Kullanıcı başarıyla oturum açarsa, `SaveSettings` yöntemi ayarları kendisini çağırarak kaydetmeyi yeniden dener.  
  
     Önceki kodda, ister `SaveSettings` yöntemi uzak hizmeti kullanılamıyorsa bir hata iletisi görüntüler. Uzak hizmet ayar sağlayıcısı erişemiyorsanız, ayarlar hala yerel önbelleğe kaydedilir ve uygulama yeniden başlatıldığında yeniden.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Form1 sınıfı sonuna aşağıdaki yöntemi ekleyin.  
  
     Bu kodu işleme <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> olay ve ayarları varsa bir uyarı kaydedilemedi görüntüler. <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> Olay ayarları hizmeti kullanılamıyorsa veya kimlik doğrulama tanımlama dolmuşsa oluşmaz. Ne zaman bir örneği <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> olay olan kullanıcının zaten oturum açmış olduğu durumunda oluşur. Oturum kapatma kod ekleyerek bu olay işleyicisi sınayabilirsiniz `SaveSettings` yöntemini doğrudan önce <xref:System.Configuration.ApplicationSettingsBase.Save%2A> yöntem çağrısı. Kullanabileceğiniz oturum kapatma kod, sonraki bölümde açıklanmıştır.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. C# ' ta sonuna aşağıdaki kodu ekleyin. `Form1_Load` yöntemi. Bu kod son adımda eklediğiniz yöntemi ilişkilendirir <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> olay.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Bu noktada uygulamayı test etmek için çalıştırma, birden çok kez hem çalışan hem de yönetici olarak ve farklı değerleri metin kutusuna yazın. Kullanıcı başına temelinde oturumlar arasında değerler kalır.  
  
## <a name="implementing-logout"></a>Uygulama oturum kapatma  
 Kullanıcı seçtiğinde **Beni Hatırla** uygulama oluşturacak, otomatik olarak oturum açarken kutuyu sonraki çalışmaları kullanıcı kimlik doğrulaması. Otomatik kimlik doğrulama uygulaması çevrimdışı modda olsa veya kimlik doğrulama tanımlama süresi dolana kadar devam eder. Bazı durumlarda, ancak birden çok kullanıcı uygulamaya erişmesi veya tek bir kullanıcı, bazen farklı kimlik bilgileriyle oturum. Bu senaryoyu etkinleştirmek için aşağıdaki yordamda açıklanan şekilde oturum kapatma işlevselliği uygulamalıdır.  
  
#### <a name="to-implement-logout-functionality"></a>Oturum kapatma işlevselliği uygulamak için  
  
1.  Form1 Tasarımcısı'nda ekleyin bir <xref:System.Windows.Forms.Button> formu denetimine **araç kutusu**.  
  
2.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `logoutButton` ve **metin** değerini **& Log Out**.  
  
3.  Çift `logoutButton` oluşturmak için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
     İmleç ile Kod Düzenleyicisi görünür `logoutButton_Click` yöntemi.  
  
4.  Oluşturulan değiştirin `logoutButton_Click` yöntemini aşağıdaki kod ile.  
  
     Bu olay işleyicisi önce çağırır `SaveSettings` önceki bölümde eklediğiniz yöntemi. Ardından, olay işleyicisini çağırır <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> yöntemi. Kimlik doğrulama hizmeti kullanılamıyorsa <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> yöntemi oluşturur bir <xref:System.Net.WebException>. Bu durumda, `logoutButton_Click` yöntemi geçer geçici olarak çevrimdışı moda kullanıcı oturumu ve bir uyarı iletisi görüntüler. Çevrimdışı modda, sonraki bölümde açıklanmıştır.  
  
     Oturum kapatma, uygulama yeniden başlatıldığında, oturum açma gerekli olacak yerel kimlik doğrulama tanımlama bilgisi siler. Oturum kapatma olay işleyicisi, uygulamayı yeniden başlatır. Uygulama yeniden başlatıldıktan sonra oturum açma iletişim kutusu tarafından izlenen Hoş Geldiniz iletisi görüntüler. Hoş Geldiniz iletisi temizleyin, uygulama yeniden başlatıldıktan kolaylaştırır. Bu, olası Karışıklığı önlemek için kullanıcı ayarlarını kaydetmek için oturum açmalısınız ve nedeniyle uygulama yeniden başlatıldıktan sonra yeniden oturum açmanız gerekir engeller.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 Oturum kapatma işlevselliğini test etmek için uygulamayı çalıştırmak ve seçmek **Beni Hatırla** oturum açma iletişim kutusunda. Ardından, kapatın ve, artık oturum açmaya sahip olduğunu onaylamak için uygulamayı yeniden başlatın. Son olarak, oturumu kapatma tıklayarak uygulamayı yeniden başlatın.  
  
## <a name="enabling-offline-mode"></a>Çevrimdışı modu etkinleştirme  
 Aşağıdaki yordamda girmesini çevrimdışı modu etkinleştirmek için forma onay kutusu ekleyin. Uygulamanızı çevrimdışı modda ayarlayarak gösterir `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> özelliğini `true`. Çevrimdışı durum tarafından belirtilen konumda yerel sabit diskte depolanan <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> özelliği. Bu, çevrimdışı durumunu bir kullanıcı, uygulama başına temelinde depolandığı anlamına gelir.  
  
 Çevrimdışı modda, tüm istemci uygulama hizmeti istekleri hizmetlere erişmeye yerine yerel önbellekten veri alın. Varsayılan yapılandırmasında, bir kullanıcının parolasını şifrelenmiş yerel veriler içerir. Bu, uygulamanın çevrimdışı moddayken oturum açmak kullanıcının sağlar. Daha fazla bilgi için [nasıl yapılır: istemci uygulama servislerini yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Uygulamanızı çevrimdışı modda etkinleştirmek için  
  
1.  İçinde **Çözüm Gezgini**Form1 ClientAppServicesDemo proje seçin ve ardından **görünümü &#124; Tasarımcısı** Visual Studio ana menüden.  
  
2.  Tasarımcıda ekleme bir <xref:System.Windows.Forms.CheckBox> forma.  
  
3.  İçinde **özellikleri** penceresinde belirtin bir **(ad)** değerini `workOfflineCheckBox` ve **metin** değerini **& iş çevrimdışı**.  
  
4.  İçinde **özellikleri** penceresinde tıklayın **olayları** düğmesi.  
  
5.  Seçin <xref:System.Windows.Forms.CheckBox.CheckedChanged> olay ve bir olay işleyicisi oluşturmak için ENTER tuşuna basın.  
  
6.  Oluşturulan yöntemini aşağıdaki kodla değiştirin.  
  
     Bu kod güncelleştirmeleri <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> değer ve bunların çevrimiçi moda döndüğünüzde kullanıcı sessiz bir şekilde yeniden doğrular. <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> Yöntemi açıkça oturum açmak kullanıcının yok, önbelleğe alınmış kimlik bilgilerini kullanır. Kimlik doğrulama hizmeti kullanılamıyorsa bir uyarı iletisi görüntülenir ve uygulamayı çevrimdışı kalır.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> Yalnızca kolaylık sağlamak için bir yöntemdir. Dönüş değeri olmadığından yeniden doğrulama başarısız olup olmadığını belirten olamaz. Örneğin, kullanıcı kimlik bilgilerinin sunucuda değiştirdiyseniz yeniden doğrulama başarısız olabilir. Bu durumda, bir hizmet çağrısı başarısız olduktan sonra kullanıcıların açıkça doğrulayan bir kodu eklemek isteyebilirsiniz. Daha fazla bilgi için bu kılavuzda daha önce açıklanan erişme Web ayarları bölümüne bakın.  
  
     Yeniden doğrulama sonra bu kod değişiklikleri yerel Web ayarlarına çağırarak kaydeder `SaveSettings` daha önce eklemiş olduğunuz yöntemi. Çağırarak sonra sunucuda yeni değerleri alır <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> projenin yöntemi `Settings` sınıfı (erişilebilir `Properties.Settings.Default` C# ve `My.Settings` Visual Basic'te).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Sonuna aşağıdaki kodu ekleyin `Form1_Load` yöntemi onay kutusunu geçerli bağlantı durumu görüntülediğinden emin olun.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Bu örnek uygulama tamamlar. Çevrimdışı özelliği test etmek için uygulamayı çalıştırın, çalışanın ya da Yöneticisi olarak oturum ve ardından **Çevrimdışı Çalış**. Metin kutusundaki değeri değiştirin ve sonra da uygulamayı kapatın. Uygulamayı yeniden başlatın. Oturum açmadan önce görev çubuğu bildirim alanında ASP.NET Geliştirme Sunucusu simgesine sağ tıklayın ve ardından **Durdur**. Ardından, normal gibi oturum açın. Sunucu bile çalışmadığı zaman, hala oturum. Metin kutusu değeri, çıkış ve değiştirilmiş değer görmek için yeniden başlatma değiştirin.  
  
## <a name="summary"></a>Özet  
 Bu kılavuzda, etkinleştirme ve istemci uygulama hizmetleri, bir Windows Forms uygulamasında kullanma hakkında bilgi edindiniz. Bir test sunucuyu ayarladıktan sonra uygulamanız kullanıcıların kimliğini doğrulama ve kullanıcı rolleri ve uygulama ayarları sunucudan almak için kod eklenir. Ayrıca bağlantı kullanılabilir değilse, uygulamanızın yerel veri önbelleği yerine uzak Hizmetleri kullanır. böylece, çevrimdışı modu etkinleştirme öğrendiniz.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Gerçek bir uygulamada, verileri çok sayıda kullanıcı için her zaman kullanılabilir olmayabilir ya da bir bildirim olmadan gidebilir bir Uzak sunucudan erişir. Uygulamanızı sağlam hale getirmek için hizmet kullanılabilir olduğu durumlar için uygun şekilde yanıt vermelidir. Bu izlenecek yolda yakalamak için try/catch blokları içerir. bir <xref:System.Net.WebException> ve hizmet kullanılabilir olmadığında bir hata iletisi görüntüler. Üretim kodunda bu durumda, çevrimdışı moda geçişi, uygulamadan çıkmak veya belirli işlevlere erişimi engelleme işlemek isteyebilirsiniz.  
  
 Uygulamanızın güvenliğini artırmak için uygulama ve dağıtımdan önce sunucu sınamanız emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Uygulama Servisleri](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [İstemci Uygulama Servislerine Genel Bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [ASP.NET Web sitesi yönetim aracı](https://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Oluşturma ve uygulama hizmetleri veritabanına SQL Server için yapılandırma](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [İzlenecek yol: ASP.NET uygulama hizmetleri kullanma](https://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
