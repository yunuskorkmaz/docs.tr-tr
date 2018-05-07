---
title: Özel Denetimler için Uygulama Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 46300f679471874ac5046d0a1077d8abca57f2c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="application-settings-for-custom-controls"></a>Özel Denetimler için Uygulama Ayarları
Özel denetimler denetimleri üçüncü taraf uygulamalarda barındırıldığında uygulama ayarlarını sürdürmek vermek için belirli görevleri tamamlamanız gerekir.  
  
 Uygulama ayarları özelliği ilgili belgelere çoğunu bağımsız uygulama oluşturmakta olduğunuz varsayılır altında yazılır. Diğer geliştiriciler barındıracak bir denetim uygulamalarında oluşturuyorsanız, ancak denetim ayarlarını kalıcı hale getirmek için bazı ek adımlar uygulamanız ihtiyacınız düzgün.  
  
## <a name="application-settings-and-custom-controls"></a>Uygulama ayarları ve özel denetimler  
 Denetiminizi düzgün ayarlarını kalıcı hale getirmek, bu işlem türetilen ayarları sarmalayıcı sınıfı, kendi özel uygulamaları oluşturarak sarmalamalıdır <xref:System.Configuration.ApplicationSettingsBase>. Ayrıca, ana denetim sınıfı uygulamalıdır <xref:System.Configuration.IPersistComponentSettings>. Arabirim iki yöntem yanı sıra çeşitli özellikler içerir <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> ve <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Kullanarak bir form denetiminizi eklerseniz **Windows Form Tasarımcısı** Visual Studio'da Windows Forms çağıracak <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> otomatik olarak zaman denetim başlatılır; çağırmalısınız <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> kendiniz `Dispose` Denetim yöntemi.  
  
 Ayrıca, Visual Studio tasarım-zamanı ortamlarda düzgün çalışması özel denetimler için uygulama ayarları için sırayla aşağıdakileri uygulamanız gerekir:  
  
1.  Özel uygulama ayarlarını sınıf alan Oluşturucu ile bir <xref:System.ComponentModel.IComponent> tek bir parametre olarak. Bu sınıf, kaydetme ve uygulama ayarlarının tümünü yükleme kullanın. Bu sınıfın yeni bir örneğini oluştururken Oluşturucusu kullanarak özel denetim geçirin.  
  
2.  Denetim oluşturulur ve bir form üzerinde gibi formun yerleştirilen sonra bu özel ayarları sınıfı oluşturmak <xref:System.Windows.Forms.Form.Load> olay işleyicisi.  
  
 Özel ayarlar sınıfı oluşturma ile ilgili yönergeler için bkz: [nasıl yapılır: uygulama ayarları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Ayarları anahtarları ve paylaşılan ayarları  
 Bazı denetimler aynı form içindeki birden çok kez kullanılabilir. Çoğu zaman, tek tek kendi ayarlarını sürdürmek için bu denetimleri isteyeceksiniz. İle <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> özelliği <xref:System.Configuration.IPersistComponentSettings>, formdaki bir denetime birden fazla sürümünü belirsizliğini ortadan kaldırmak için davranır benzersiz bir dize sağlayabilirsiniz.  
  
 Uygulamak için en basit yolu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> kullanmaktır <xref:System.Windows.Forms.Control.Name%2A> özelliği için bir denetim <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Yük ya da denetim ayarlarını Kaydet değerini geçirin <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> oturum <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> özelliği <xref:System.Configuration.ApplicationSettingsBase> sınıfı. Uygulama ayarları, kullanıcının ayarlarını XML ediyorsa bu benzersiz anahtar kullanır. Aşağıdaki örnekte gösterildiği nasıl kod bir `<userSettings>` bölümüne adlı özel bir denetim örneği için bakın `CustomControl1` için bir ayar kaydeder, `Text` özelliği.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Tüm örnekleri için bir değer sağlamazsanız bir denetimin <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> aynı ayarları paylaşır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Uygulama Ayarları Mimarisi](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
