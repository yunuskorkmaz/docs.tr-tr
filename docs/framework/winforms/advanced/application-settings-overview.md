---
title: Uygulama Ayarlarına Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
ms.openlocfilehash: a827eeeca3f9d2719b4467bd19e66b3a40eb2c1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="application-settings-overview"></a>Uygulama Ayarlarına Genel Bakış
Bu konuda oluşturmak ve uygulamanızı ve kullanıcılarınızın adına ayar verileri depolamak nasıl ele alınmıştır.  
  
 Windows Forms uygulaması ayarları özelliğini oluşturmak, depolamak ve özel uygulama ve istemci bilgisayardaki kullanıcı tercihlerini korumak daha kolay hale getirir. Windows Forms uygulama ayarları, yalnızca veritabanı bağlantı dizelerini gibi uygulama verilerini, aynı zamanda kullanıcı uygulama tercihleri gibi kullanıcıya özgü verileri depolayabilir. Visual Studio veya özel yönetilmiş kod kullanarak, yeni ayarları oluşturabilir, bunları okuyun ve bunları disk, formlarınızı özellikleri bağlamak ve yükleme ve kaydetme önce ayarları verileri doğrulamak için yazar.  
  
 Uygulama ayarları geliştiricilerin çok az özel kod kullanarak kendi uygulama durumunu kaydetmeyi etkinleştirir ve önceki sürümlerinde, dinamik özelliklerin yerini [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Uygulama ayarları olan salt okunur, geç bağlama ve daha fazla özel programlama gerektiren dinamik özellikleri birçok iyileştirme içerir. Dinamik özellik sınıfları içinde tutulur [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], ancak yalnızca uygulama ayarlarını sınıfları ölçülü sarmalamak Kabuk sınıfları etmektedir.  
  
## <a name="what-are-application-settings"></a>Uygulama ayarları nelerdir?  
 Windows Forms uygulamaları genellikle uygulama çalıştıran için kritik olan ancak doğrudan uygulama kodunda dahil etmek istemediğiniz veri gerektirir. Uygulamanızı bir Web hizmeti veya bir veritabanı sunucusu kullanıyorsa, böylece bunu gelecekte yeniden derleme olmadan değiştirmek, ayrı bir dosyaya, bu bilgileri depolamak isteyebilirsiniz. Benzer şekilde, uygulamalarınızı geçerli kullanıcıya özgü veri depolama gerektirebilir. Çoğu uygulama, örneğin, uygulamanın görünümünü ve davranışını özelleştirmek kullanıcı tercihleri gerekir.  
  
 Uygulama ayarları adresleri hem uygulama kapsamlı hem de kullanıcı kapsamlı ayarlarını istemci bilgisayarda depolamak için kolay bir yol sağlayarak gerekir. Visual Studio ya da bir kod düzenleyicisini kullanarak, ad, veri türü ve kapsam (uygulama veya kullanıcı) belirterek belirli bir özellik için bir ayar tanımlayın. İlgili ayarlar daha kolay kullanım ve okunabilirliği adlandırılmış gruplar halinde bile yerleştirebilirsiniz. Bir kez tanımlandıktan sonra bu ayarlar kalıcı ve çalışma zamanında otomatik olarak geri belleğe okuyun. Eklenebilir mimari değiştirilecek Kalıcılık mekanizması sağlar, ancak varsayılan olarak, yerel dosya sistemi kullanılır.  
  
 Uygulama ayarları Works'ün farklı yapılandırma (.config) dosyaları, ayar uygulama kapsamlı kullanıcı kapsamlı mı için karşılık gelen XML olarak kalıcı veri. Çoğu durumda, uygulama kapsamlı ayarları salt okunur; program bilgilerini olduklarından, genellikle bunların üzerine gerekmez. Bunun aksine, kullanıcı kapsamlı ayarları okunabilir ve kısmi güven altında uygulamanız çalıştırıyor olsa bile çalışma zamanında güvenle yazılmış. Kısmi güven hakkında daha fazla bilgi için bkz: [Windows Forms'a genel bakış güvenlik](../../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
 Ayarları yapılandırma dosyalarında XML parçaları olarak depolanır. Uygulama kapsamlı ayarları temsil ettiği `<application.Settings>` öğesi ve genellikle yerleştirilir *uygulama*. exe.config, burada *uygulama* , ana yürütülebilir dosyanın adıdır. Kullanıcı kapsamlı ayarları temsil ettiği `<userSettings>` öğesi ve bu yerleştirilen içinde *kullanıcı*.config, burada *kullanıcı* uygulama şu anda çalışan kişinin kullanıcı adıdır. Dağıtmanız gerekir *uygulama*. exe.config dosyası uygulamanız ile; mimarisi oluşturacak ayarları *kullanıcı*.config dosyaları isteğe bağlı ilk zaman uygulamayı o kullanıcı için ayarları kaydeder. Ayrıca tanımlayabilirsiniz bir `<userSettings>` içinde engelleme *uygulama*. exe.config kullanıcı kapsamlı ayarları için varsayılan değerleri sağlayın.  
  
 Özel denetimler de kaydedebilir, kendi ayarları uygulayarak <xref:System.Configuration.IPersistComponentSettings> arabirim, hangi çıkarır <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> yöntemi. Windows Forms <xref:System.Windows.Forms.ToolStrip> Denetim araç çubukları ve araç çubuğu öğeleri uygulama oturumları arasında konumunu kaydetmek için bu arabirimi uygular. Özel denetimler ve uygulama ayarları hakkında daha fazla bilgi için bkz: [özel denetimler için uygulama ayarları](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Uygulama ayarları sınırlamaları  
 Uygulama ayarları barındıran yönetilmeyen bir uygulamada kullanamazsınız [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Visual Studio eklentileri, C++ için Microsoft Office, Internet Explorer veya Microsoft Outlook eklentiler ve projeleri barındırma denetimi olarak ayarları bu tür ortamlarda çalışmaz.  
  
 Windows Forms'ta bazı özellikleri şu anda bağlanılamıyor. En önemli örnek <xref:System.Windows.Forms.Form.ClientSize%2A> özelliği, bu özelliği için bağlama beklenmeyen davranışlara neden çalışma zamanında. Kaydetme ve bu ayarları yükleme genellikle bu sorunları çalışabilirsiniz programlı olarak.  
  
 Uygulama ayarları bilgilerini otomatik olarak şifrelemek için hiçbir yerleşik olanağı vardır. Veritabanı parolaları gibi güvenlikle ilgili bilgileri hiçbir zaman şifresiz metin olarak depolamanız gerekir. Gibi hassas bilgileri depolamak istiyorsanız, uygulama geliştiricisi olarak, güvenli olduğundan emin olmak sorumludur. Bağlantı dizeleri depolamak istiyorsanız, Windows tümleşik güvenliğini kullan ve parolalarını sabit kodlama URL'ye çözümlemelere değil öneririz. Daha fazla bilgi için bkz: [kod erişim güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Uygulama ayarları ile çalışmaya başlama  
 Visual Studio kullanıyorsanız, Windows Form Tasarımcısı kullanarak içinde ayarlarını tanımlayabilir **(ApplicationSettings)** özelliğinde **özellikleri** penceresi. Bu şekilde ayarları tanımladığınızda, Visual Studio ile sınıf özelliği her bir ayarın ilişkilendiren özel yönetilen sarmalayıcı sınıfı otomatik olarak oluşturur. Visual Studio ayrıca kendi form görüntülenir ve form kapatıldığında otomatik olarak kaydedilir ve denetim ayarlarını otomatik olarak geri böylece ayarı bir form veya denetim özellikte bağlama mvc'deki.  
  
 Ayarlarınızı üzerinde ayrıntılı denetim isterseniz, kendi özel uygulamalar ayarları sarmalayıcı sınıfı tanımlayabilirsiniz. Bu bir sınıftan türetilen tarafından gerçekleştirilir <xref:System.Configuration.ApplicationSettingsBase>, her ayarlama ve özel öznitelikleri için bu özellikleri uygulama karşılık gelen özellik ekleme. Sarmalayıcı sınıfları oluşturma hakkında daha fazla bilgi için bkz: [uygulama ayarları mimarisi](../../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
 Aynı zamanda <xref:System.Windows.Forms.Binding> ayarları formlar ve denetimler özellikleri programlı olarak bağlamak için sınıf.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Nasıl yapılır: Uygulama Ayarlarını Doğrulama](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 [Uygulama Ayarlarını Yönetme](http://msdn.microsoft.com/library/35254321-ad14-47d9-b8c6-39ab3203c5d9)  
 [Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Uygulama Ayarları Mimarisi](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Özel Denetimler için Uygulama Ayarları](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)
