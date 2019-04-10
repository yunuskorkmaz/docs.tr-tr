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
ms.openlocfilehash: b603e81a342652a6639f54a78fb998cda5fdc35a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203632"
---
# <a name="application-settings-overview"></a>Uygulama Ayarlarına Genel Bakış
Bu konuda, oluşturmak ve uygulamanız ve kullanıcılarınız adına ayar verileri depolamak nasıl ele alınmaktadır.  
  
 Windows Forms uygulaması ayarları özelliğini oluşturulacağı, depolanacağı ve özel uygulama ve istemci bilgisayarda kullanıcı tercihlerini korumak daha kolay hale getirir. İle Windows Forms uygulama ayarları, yalnızca veritabanı bağlantı dizeleri gibi uygulama verilerini, aynı zamanda kullanıcı uygulama tercihleri gibi kullanıcıya özgü verileri depolayabilirsiniz. Visual Studio veya özel yönetilmiş kod kullanarak, yeni ayarları oluşturabilir, bunları okuyun ve bunları disk formlarınızı özellikleri bağlamak ve yükleme ve kaydetme önce veri ayarlarını doğrulayın.  
  
 Uygulama ayarları geliştiricilerin özel çok az kod kullanarak, uygulama durumunu kaydetmeyi etkinleştirir ve önceki sürümlerinde dinamik özelliklerin yerini [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Uygulama ayarları, salt okunur, geç bağlanan ve daha fazla özel programlama gerektiren Dinamik özellikler üzerinde birçok geliştirme içerir. Dinamik özellik sınıfları görevlendirdiğimiz [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], ancak bunlar yalnızca ölçülü kaynak uygulama ayarları sınıfları sarmalamak Kabuk sınıfları.  
  
## <a name="what-are-application-settings"></a>Uygulama ayarları nelerdir?  
 Windows Forms uygulamalarınızı genellikle uygulamayı çalıştıran için kritik olan ancak doğrudan uygulama kodu dahil etmek istemediğiniz veri gerektirir. Uygulamanız bir Web hizmeti veya veritabanı sunucusu kullanıyorsa, böylece bunu gelecekte yeniden derleme olmadan değiştirebilirsiniz, ayrı bir dosyada bu bilgileri depolamak isteyebilirsiniz. Benzer şekilde, geçerli kullanıcıya özgü verileri depolamak, uygulamalarınızın gerektirebilir. Çoğu uygulama, örneğin, uygulamanın görünümünü ve davranışını özelleştirin kullanıcı tercihlerini sahip.  
  
 Uygulama ayarları adres hem istemci bilgisayarda hem uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamak için kolay bir yol sağlayarak olması gerekir. Visual Studio veya bir kod Düzenleyicisi'ni kullanarak, onun adı, veri türüne ve kapsamına (uygulama veya kullanıcıya) belirterek belirli bir özellik için bir ayarı tanımlar. İlgili ayarlar daha kolay kullanım ve okunabilirliği adlandırılmış gruplara bile yerleştirebilirsiniz. Tanımlandıktan sonra bu ayarlar kalıcı ve belleğe geri otomatik olarak çalışma zamanında okuyun. Eklenebilir mimari değiştirilecek Kalıcılık mekanizması sağlar, ancak varsayılan olarak, yerel dosya sistemi kullanılır.  
  
 XML olarak kalıcı veri olup olmadığını ayar uygulama kapsamlı kullanıcı kapsamlı veya için karşılık gelen farklı (.config) yapılandırma dosyalarına göre uygulama ayarları çalışır. Çoğu durumda, salt okunur uygulama kapsamlı ayarlar; program bilgilerini olduklarından, genellikle bunların üzerine gerekmez. Bunun aksine, kullanıcı kapsamlı ayarları okunabilir ve uygulamanızın çalıştığı kısmi güven altında olsa bile çalışma zamanında, güvenli bir şekilde yazılmış. Kısmi güven hakkında daha fazla bilgi için bkz: [Windows Forms'ta Güvenliğe genel bakış](../security-in-windows-forms-overview.md).  
  
 Ayarları, yapılandırma dosyalarındaki XML parçaları olarak depolanır. Uygulama kapsamlı ayarlar tarafından temsil edilir `<application.Settings>` öğesi ve genellikle yerleştirilir *uygulama*. exe.config olarak, burada *uygulama* ana yürütülebilir dosyanın adı. Kullanıcı kapsamlı ayarları tarafından temsil edilir `<userSettings>` öğesi ve bu yerleştirildiğinde *kullanıcı*.config, burada *kullanıcı* çalışmakta olan uygulamayı kişinin kullanıcı adı. Dağıtmalısınız *uygulama*. exe.config dosyası uygulamanızla; mimarisi oluşturacaktır ayarları *kullanıcı*.config dosyaları ilk isteğe bağlı saat ayarları söz konusu kullanıcı için uygulamayı kaydeder. Ayrıca tanımlayabilirsiniz bir `<userSettings>` içinde engellemek *uygulama*. exe.config kullanıcı kapsamlı ayarları için varsayılan değerler sağlamak için.  
  
 Özel denetimler de kaydedebilir kendi ayarlarını uygulayarak <xref:System.Configuration.IPersistComponentSettings> kullanıma sunan arabirim <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> yöntemi. Windows Forms <xref:System.Windows.Forms.ToolStrip> denetimi araç çubukları ve araç çubuğu öğelerini uygulama oturumları arasında konumunu kaydetmek için bu arabirimi uygular. Özel denetimler ve uygulama ayarları hakkında daha fazla bilgi için bkz. [özel denetimler için uygulama ayarları](application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Uygulama ayarları sınırlamaları  
 Uygulama ayarları barındıran yönetilmeyen bir uygulamada kullanamazsınız [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Visual Studio eklentileri, C++ için Microsoft Office, Internet Explorer veya Microsoft Outlook eklentileri ve projelerinde barındırma denetimi olarak, bu tür ortamlarda ayarları çalışmaz.  
  
 Windows Forms'ta bazı özellikler şu anda bağlanılamıyor. En önemli örnek <xref:System.Windows.Forms.Form.ClientSize%2A> özelliği, bu özelliği için bağlama olarak neden öngörülemeyen davranışlara çalışma zamanında. Genellikle kaydetme ve bu ayarları yüklenirken bu sorunların çözüm çalışabilir programlı olarak.  
  
 Uygulama ayarları olan bilgileri otomatik olarak şifrelemek için yerleşik bulunmaz. Düz metin olarak veritabanı parolalar gibi güvenlikle ilgili bilgileri hiçbir zaman depolamanız gerekir. Gibi hassas bilgileri depolamak istiyorsanız, uygulama geliştiricisi olarak güvenli olduğundan emin olmak sorumlu olursunuz. Bağlantı dizeleri depolamak istiyorsanız, Windows tümleşik güvenliğini kullan ve parolaları kodlamak için URL'de başvurmadan değil öneririz. Daha fazla bilgi için [kod erişimi güvenliği ve ADO.NET](../../data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Uygulama ayarları ile çalışmaya başlama  
 Visual Studio kullanıyorsanız, Windows Form Tasarımcısı kullanarak içinde ayarlar tanımlayabilirsiniz **(ApplicationSettings)** özelliğinde **özellikleri** penceresi. Bu şekilde ayarlarını tanımlarken, Visual Studio otomatik olarak her bir ayar bir sınıf özelliği ile ilişkilendiren özel bir yönetilen sarmalayıcı sınıfı oluşturur. Visual Studio ayrıca, form görüntülenir ve form kapatıldığında otomatik olarak kaydedilen denetim ayarları otomatik olarak geri yüklenir, böylece ayarı bir form veya denetim özelliğine bağlama üstlenir.  
  
 Ayarlarınızı üzerinde ayrıntılı denetim istiyorsanız, kendi özel uygulamalar ayarları sarmalayıcı sınıfı tanımlayabilirsiniz. Bu bir sınıftan türetme tarafından gerçekleştirilir <xref:System.Configuration.ApplicationSettingsBase>, her ayar ve bu özelliklerin özel öznitelikleri uygulama karşılık gelen özellik ekleme. Sarmalayıcı sınıfları oluşturma hakkında daha fazla ayrıntı için bkz. [uygulama ayarları mimarisi](application-settings-architecture.md).  
  
 Ayrıca <xref:System.Windows.Forms.Binding> ayarları formlar ve denetimler üzerinde özelliklerine program aracılığıyla bağlamak için sınıf.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [Nasıl yapılır: Uygulama Ayarlarını Doğrulama](how-to-validate-application-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
- [Nasıl yapılır: Çalışma Zamanında C# ile Ayarları Okuma](how-to-read-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Uygulama Ayarları Mimarisi](application-settings-architecture.md)
- [Özel Denetimler için Uygulama Ayarları](application-settings-for-custom-controls.md)
