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
ms.openlocfilehash: 72a15736fd21d1d626f88e728d70b7dd7ee6768f
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990177"
---
# <a name="application-settings-overview"></a>Uygulama Ayarlarına Genel Bakış

Bu makalede, uygulama ve kullanıcılarınız adına ayar verilerinin nasıl oluşturulacağı ve depolandığı açıklanır.

 Windows Forms uygulama ayarları özelliği, istemci bilgisayarda özel uygulama ve Kullanıcı tercihleri oluşturmayı, depolamayı ve bakımını yapmayı kolaylaştırır. Windows Forms uygulama ayarları ile, yalnızca veritabanı bağlantı dizeleri gibi uygulama verilerini, ancak kullanıcı uygulama tercihleri gibi kullanıcıya özgü verileri de kaydedebilirsiniz. Visual Studio veya özel yönetilen kod kullanarak yeni ayarlar oluşturabilir, bunları diskten okuyabilir ve diske yazabilir, formlarınızın özelliklerine bağlayabilir ve yükleme ve kaydetmeden önce ayar verilerini doğrulayabilirsiniz.

 Uygulama ayarları, geliştiricilerin çok az özel kod kullanarak durumunu uygulamasına kaydetmesini sağlar ve .NET Framework önceki sürümlerindeki dinamik özelliklerin yerini alır. Uygulama ayarları, salt okunurdur ve geç bağlantılı olan dinamik özellikler üzerinde birçok geliştirme içerir ve daha fazla özel programlama gerektirir. Dinamik özellik sınıfları .NET Framework 2,0 ' de tutulur, ancak yalnızca uygulama ayarları sınıflarını ölçülü bir şekilde kaydıramayan kabuk sınıflarıdır.

## <a name="what-are-application-settings"></a>Uygulama ayarları nelerdir?
 Windows Forms uygulamalarınız genellikle uygulamayı çalıştırmak için önemli olan verileri gerektirir, ancak uygulamanın koduna doğrudan dahil etmek istemezsiniz. Uygulamanız bir Web hizmeti veya bir veritabanı sunucusu kullanıyorsa, daha sonra yeniden derlemeden değiştirebilmek için bu bilgileri ayrı bir dosyada depolamak isteyebilirsiniz. Benzer şekilde, uygulamalarınız geçerli kullanıcıya özgü verilerin depolanmasını gerektirebilir. Örneğin çoğu uygulama, uygulamanın görünümünü ve davranışını özelleştiren kullanıcı tercihlerine sahiptir.

 Uygulama ayarları, hem uygulama kapsamlı hem de kullanıcı kapsamlı ayarları istemci bilgisayarda depolamanın kolay bir yolunu sağlayarak her iki ihtiyacı da ele alır. Visual Studio 'Yu veya bir kod düzenleyicisini kullanarak, adını, veri türünü ve kapsamını (uygulama veya Kullanıcı) belirterek belirli bir özellik için bir ayar tanımlarsınız. Daha kolay kullanım ve okunabilirlik için ilgili ayarları adlandırılmış gruplara da yerleştirebilirsiniz. Tanımlandıktan sonra, bu ayarlar kalıcı hale getirilir ve çalışma zamanında otomatik olarak belleğe geri okunurdur. Takılabilir bir mimari, kalıcılık mekanizmasının değiştirilmesini sağlar, ancak varsayılan olarak yerel dosya sistemi kullanılır.

 Uygulama ayarları, ayarın uygulama kapsamlı veya Kullanıcı kapsamında olup olmadığına karşılık gelen farklı yapılandırma (. config) dosyaları için XML olarak kalıcı veriler tarafından kullanılır. Çoğu durumda, uygulama kapsamlı ayarlar salt okunurdur; Program bilgileri olduklarından, genellikle bu bilgilerin üzerine yazmanız gerekmez. Bunun aksine, uygulamanız kısmi güven altında çalışıyor olsa bile, kullanıcı kapsamlı ayarlar çalışma zamanında okunabilir ve güvenli bir şekilde yazılabilir. Kısmi güven hakkında daha fazla bilgi için bkz. [güvenlik Windows Forms genel bakış](../security-in-windows-forms-overview.md).

 Ayarlar, yapılandırma dosyalarında XML parçaları olarak depolanır. Uygulama kapsamlı ayarlar öğesi tarafından temsil edilir `<applicationSettings>` ve genellikle *uygulama*.exe.config yerleştirilir, burada *uygulama* ana yürütülebilir dosyanızın adıdır. Kullanıcı kapsamlı ayarlar, öğesi tarafından temsil edilir `<userSettings>` ve Kullanıcı. config dosyasına *user*yerleştirilir, burada *Kullanıcı* uygulamayı çalıştırmakta olan kişinin kullanıcı adıdır. *Uygulama.exe.config dosyasını* uygulamanızla dağıtmanız gerekir; ayarlar mimarisi, uygulamanın ayarları ilk kez kaydettiğinde *Kullanıcı*. config dosyalarını isteğe bağlı olarak oluşturur. Ayrıca, `<userSettings>` Kullanıcı kapsamlı ayarlar için varsayılan değerler sağlamak üzere *uygulama*.exe.config içinde bir blok tanımlayabilirsiniz.

 Özel denetimler, yöntemi sunan arabirimini uygulayarak kendi ayarlarını da kaydedebilir <xref:System.Configuration.IPersistComponentSettings> <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> . Windows Forms <xref:System.Windows.Forms.ToolStrip> denetimi, araç çubuklarının ve araç çubuğu öğelerinin konumunu uygulama oturumları arasında kaydetmek için bu arabirimi uygular. Özel denetimler ve uygulama ayarları hakkında daha fazla bilgi için bkz. [özel denetimler Için uygulama ayarları](application-settings-for-custom-controls.md).

## <a name="limitations-of-application-settings"></a>Uygulama ayarlarının sınırlamaları
 .NET Framework barındıran yönetilmeyen bir uygulamada uygulama ayarlarını kullanamazsınız. Ayarlar, Visual Studio eklentileri, Microsoft Office için C++, Internet Explorer 'da barındırılacak denetim veya Microsoft Outlook eklentileri ve projeleri gibi bu ortamlarda çalışmayacaktır.

 Şu anda Windows Forms bazı özelliklere bağlayamazsınız. En önemli örnek, <xref:System.Windows.Forms.Form.ClientSize%2A> Bu özelliğe yönelik bağlama çalışma zamanında öngörülemeyen davranışlara neden olacağından özelliktir. Bu ayarları genellikle programlı bir şekilde kaydederek ve yükleyerek bu sorunları geçici olarak çözebilirsiniz.

 Uygulama ayarlarında bilgileri otomatik olarak şifrelemek için yerleşik bir tesis yoktur. Veritabanı parolaları gibi güvenlikle ilgili bilgileri asla şifresiz metin olarak depolamamalısınız. Bu tür gizli bilgileri depolamak istiyorsanız, uygulamanın güvenli olduğundan emin olmak için uygulama geliştiricisi sorumludur. Bağlantı dizelerini depolamak istiyorsanız, Windows tümleşik güvenliği 'ni kullanmanızı ve bu parolaları URL 'de sabit kodlanmasını öneririz. Daha fazla bilgi için bkz. [kod erişimi güvenliği ve ADO.net](../../data/adonet/code-access-security.md).

## <a name="getting-started-with-application-settings"></a>Uygulama ayarlarını kullanmaya başlama
 Visual Studio kullanıyorsanız, **Özellikler** penceresindeki **(ApplicationSettings)** özelliğini kullanarak Windows Form Tasarımcısı ayarları tanımlayabilirsiniz. Ayarları bu şekilde tanımladığınızda, Visual Studio otomatik olarak her bir ayarı bir sınıf özelliğiyle ilişkilendiren özel bir yönetilen sarmalayıcı sınıfı oluşturur. Visual Studio, form görüntülenirken denetimin ayarlarının otomatik olarak geri yüklenmesi ve form kapatıldığında otomatik olarak kaydedilmesi için ayarı bir form veya denetimdeki bir özelliğe bağlamayı de gerçekleştirir.

 Ayarlarınız üzerinde daha ayrıntılı denetim istiyorsanız, kendi özel uygulama ayarları sarmalayıcı sınıfınızı tanımlayabilirsiniz. Bu, öğesinden bir sınıf türeterek <xref:System.Configuration.ApplicationSettingsBase> , her ayara karşılık gelen bir özellik eklenerek ve bu özelliklere özel öznitelikler uygulanarak gerçekleştirilir. Sarmalayıcı sınıfları oluşturma hakkında ayrıntılı bilgi için bkz. [uygulama ayarları mimarisi](application-settings-architecture.md).

 Ayrıca, <xref:System.Windows.Forms.Binding> ayarları form ve denetimlerin özelliklerine programlı bir şekilde bağlamak için sınıfını da kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [Nasıl yapılır: Uygulama Ayarlarını Doğrulama](how-to-validate-application-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
- [Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma](how-to-read-settings-at-run-time-with-csharp.md)
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Uygulama Ayarları Mimarisi](application-settings-architecture.md)
- [Özel Denetimler için Uygulama Ayarları](application-settings-for-custom-controls.md)
