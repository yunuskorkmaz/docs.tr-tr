---
title: Özel Denetimler için Uygulama Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 69a5caef8bab45503b9f34422de8c2ba2e7f01ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960907"
---
# <a name="application-settings-for-custom-controls"></a>Özel Denetimler için Uygulama Ayarları
Özel denetimlerinizi denetimleri üçüncü taraf uygulamalarda barındırıldığında uygulama ayarlarını kalıcı yapma olanağı vermek için belirli görevleri tamamlamanız gerekir.  
  
 Uygulama ayarları özelliğiyle ilgili belgelerin çoğu, bir tek başına uygulama oluşturma varsayım altında yazılır. Uygulamalarında diğer geliştiriciler barındıracak bir denetim oluşturma, ancak denetim ayarlarını kalıcı hale getirmek için bazı ek adımlar uygulamanız gerekiyorsa, doğru.  
  
## <a name="application-settings-and-custom-controls"></a>Uygulama ayarları ve özel denetimler  
 Denetiminiz düzgün ayarlarını kalıcı hale getirmek, bu işlem ayarları sarmalayıcı sınıfından türetilen kendi özel uygulamalar oluşturarak yalıtmanız gerekir <xref:System.Configuration.ApplicationSettingsBase>. Ayrıca, ana denetim sınıf uygulamalıdır <xref:System.Configuration.IPersistComponentSettings>. Çeşitli özelliklerin yanı sıra, iki yöntem arabirimi içeren <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> ve <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Kullanarak bir formu, denetimi eklerseniz **Windows Form Tasarımcısı** Visual Studio'da, Windows Forms çağıracak <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> otomatik olarak ne zaman denetimi başlatılır; çağırmalısınız <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> kendiniz `Dispose` Denetiminizin yöntemi.  
  
 Ayrıca, aşağıdaki gibi Visual Studio tasarım zamanı ortamlarda düzgün çalışması özel denetimler için uygulama ayarları için sırayla uygulamalıdır:  
  
1. Bir özel uygulama ayarları sınıf alan bir Oluşturucu ile bir <xref:System.ComponentModel.IComponent> tek bir parametre olarak. Bu sınıfı kaydedin ve tüm uygulama ayarlarınızı yüklemek için kullanın. Bu sınıfın yeni bir örneğini oluşturduğunuzda, oluşturucu kullanılarak özel denetiminizi geçirin.  
  
2. Denetim oluşturulan ve bir form üzerinde olduğu gibi formun yerleştirilir. sonra bu özel ayarları sınıfı oluşturma <xref:System.Windows.Forms.Form.Load> olay işleyicisi.  
  
 Özel ayarlar sınıfı oluşturma ile ilgili yönergeler için bkz: [nasıl yapılır: Uygulama ayarları oluşturma](how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Ayarları anahtarları ve paylaşılan ayarları  
 Bazı denetimler, birden çok kez aynı form içinde kullanılabilir. Çoğu zaman, kullanıcıların kendi tek tek ayarların kalıcı olması için bu denetimleri isteyeceksiniz. İle <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> özelliği <xref:System.Configuration.IPersistComponentSettings>, bir form denetiminde birden fazla sürümünü ayırt etmek için görevi gören benzersiz bir dize sağlayabilirsiniz.  
  
 Uygulamak için en basit yolu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> kullanmaktır <xref:System.Windows.Forms.Control.Name%2A> özelliği için denetimin <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Yük ya da denetim ayarlarını Kaydet değerini geçirmelidir <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> oturum <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> özelliği <xref:System.Configuration.ApplicationSettingsBase> sınıfı. Uygulama ayarları, XML'e kullanıcı ayarlarını kalıcı olduğunda bu benzersiz anahtar kullanır. Aşağıdaki örnekte gösterildiği nasıl kod bir `<userSettings>` bölümü adlı bir özel denetim örneği için görünebileceğini `CustomControl1` için bir ayar kaydeder, `Text` özelliği.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Tüm örnekleri için bir değer belirtmediğiniz bir denetimin <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> aynı ayarları paylaşır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Uygulama Ayarları Mimarisi](application-settings-architecture.md)
