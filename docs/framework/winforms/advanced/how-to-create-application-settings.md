---
title: 'Nasıl yapılır: Uygulama Ayarları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 5cf109aec8b55650f43f07f5b303c6373df4efc7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305981"
---
# <a name="how-to-create-application-settings"></a>Nasıl yapılır: Uygulama Ayarları Oluşturma
Yönetilen kod kullanarak, yeni uygulama ayarları oluşturma ve böylece bu ayarlar yüklenir ve çalışma zamanında otomatik olarak kaydedilir bunları özelliklerine formunuza veya form denetimlerinde bağlayın.  
  
 Aşağıdaki yordamda, el ile türetilen bir sarmalayıcı sınıfı oluşturmanız <xref:System.Configuration.ApplicationSettingsBase>. Bu sınıf için kullanıma sunmak istediğiniz her uygulama ayarı için ortak olarak erişilebilen bir özellik ekleyin.  
  
 Ayrıca, bu yordamı Visual Studio Tasarımcısı'nda çok az kod kullanarak gerçekleştirebilirsiniz.  Ayrıca bkz: [nasıl yapılır: Tasarımcıyı kullanarak uygulama ayarları oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Yeni uygulama ayarları program aracılığıyla oluşturmak için  
  
1. Projenize yeni bir sınıf ekleyin ve adlandırın. Bu yordam için Biz bu sınıf göndereceği `MyUserSettings`. Sınıf tanımını değiştirin, böylece bu sınıfın türetildiği <xref:System.Configuration.ApplicationSettingsBase>.  
  
2. Bu sarmalayıcı sınıf için ihtiyaç duyduğunuz her uygulama ayarı üzerinde bir özellik tanımlayın ve bu özellik ile ya da geçerli <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>ayarı kapsamını bağlı olarak. Ayar kapsamı hakkında daha fazla bilgi için bkz: [uygulama ayarlarına genel bakış](application-settings-overview.md). Artık, kodunuz şu şekilde görünmelidir:  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3. Uygulamanızda bu sarmalayıcı sınıfının bir örneğini oluşturun. Bu genellikle ana formu özel üyesi olacaktır. Sınıfınıza tanımladığınıza göre bir özelliğine bağlamak gerekir; Bu durumda, <xref:System.Windows.Forms.Form.BackColor%2A> formunuza bir özelliğidir. Bunu, formun içinde gerçekleştirebilirsiniz `Load` olay işleyicisi.  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4. Çalışma zamanında ayarlarını değiştirmek için bir yol sağlar, kullanıcının geçerli ayarlarının formunuza kapatır, aksi takdirde, bu değişiklikler kaybolacak diske kaydetmek gerekir.  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Artık başarıyla oluşturulmuş yeni bir uygulama ayarı ve belirtilen özelliğe bağlı.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Varsayılan ayar sağlayıcısı <xref:System.Configuration.LocalFileSettingsProvider>, yapılandırma dosyalarındaki bilgileri düz metin olarak kalıcıdır. Bu, geçerli kullanıcı için işletim sistemi tarafından sağlanan dosya erişim güvenliği için güvenlik sınırlar. Bu nedenle dikkatli yapılandırma dosyalarında depolanan bilgileri alınması gerekir. Örneğin, bir uygulama ayarları uygulamanın veri deposuna işaret eden bağlantı dizeleri depolamak için kullanılır. Ancak, güvenlik kaygıları nedeniyle, parolalar gibi dizeleri içermemelidir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
- [Nasıl yapılır: Uygulama ayarlarını doğrulama](how-to-validate-application-settings.md)
