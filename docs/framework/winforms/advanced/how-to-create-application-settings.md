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
ms.openlocfilehash: e6e268169949994e1b58b5b8a7dcd0429895fb38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524176"
---
# <a name="how-to-create-application-settings"></a>Nasıl yapılır: Uygulama Ayarları Oluşturma
Yönetilen kod kullanarak, yeni uygulama ayarları oluşturabilir ve böylece bu ayarlar yüklenir ve çalışma zamanında otomatik olarak kaydedilir bunları özelliklerine formunuz veya, formun denetimlerinde bağlayın.  
  
 Aşağıdaki yordamda, el ile türeyen bir sarmalayıcı sınıfı oluşturmanız <xref:System.Configuration.ApplicationSettingsBase>. Bu sınıf için kullanıma sunmak istediğiniz her uygulama ayarı için genel olarak erişilebilir bir özellik ekleyin.  
  
 Ayrıca, bu yordamı Visual Studio tasarımcısında çok az kod kullanarak gerçekleştirebilirsiniz.  Ayrıca bkz. [nasıl yapılır: uygulama ayarları kullanarak Tasarımcı](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Yeni uygulama ayarları program aracılığıyla oluşturmak için  
  
1.  Projeniz için yeni bir sınıf ekleyin ve yeniden adlandırın. Bu yordam, biz Bu sınıf çağıracaktır `MyUserSettings`. Sınıf tanımını değiştirin, böylece sınıfın türetildiği <xref:System.Configuration.ApplicationSettingsBase>.  
  
2.  Bu sarmalayıcı sınıfı ihtiyaç duyduğunuz her uygulama ayarı için bir özellik tanımlamak ve bu özellik ile ya da geçerli <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>ayarı kapsamını bağlı olarak. Ayarları kapsamı hakkında daha fazla bilgi için bkz: [uygulama ayarlarına genel bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md). Artık, kodunuzu aşağıdaki gibi görünmelidir:  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  Bu sarmalayıcı sınıfının bir örneği, uygulamanızda oluşturun. Ayrıca, özel üye ana formun sık olacaktır. Sınıfınızda tanımladığınız, bir özelliği Bağla gerekir; Bu durumda, <xref:System.Windows.Forms.Form.BackColor%2A> formunuz özelliği. Bunu, formun gerçekleştirebilirsiniz `Load` olay işleyicisi.  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  Çalışma zamanında ayarlarını değiştirmek için bir yol belirtirseniz, kullanıcının geçerli ayarlarının, formu kapatır, aksi takdirde, bu değişiklikler kaybolacak diske kaydetmeniz gerekir.  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Şimdi başarıyla yeni bir uygulama ayarı oluşturduktan ve belirtilen özelliğe bağlı.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Varsayılan ayarları sağlayıcısı <xref:System.Configuration.LocalFileSettingsProvider>, yapılandırma dosyalarını bilgileri düz metin olarak devam ettirir. Bu, geçerli kullanıcı için işletim sistemi tarafından sağlanan dosya erişim güvenliği için güvenlik sınırlar. Bu nedenle dikkatli yapılandırma dosyalarında depolanan bilgileri alınması gerekir. Örneğin, bir genel uygulama ayarları için uygulamanın veri deposuna'nın üzerine bağlantı dizeleri depolamak için kullanılır. Ancak, güvenlik sorunları nedeniyle, parolalar gibi dizeleri içermemelidir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz: <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Nasıl yapılır: Uygulama Ayarlarını Doğrulama](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
