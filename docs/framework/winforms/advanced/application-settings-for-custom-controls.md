---
title: Özel Denetimler için Uygulama Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040468"
---
# <a name="application-settings-for-custom-controls"></a>Özel Denetimler için Uygulama Ayarları
Özel denetimlerinizi, denetimler üçüncü taraf uygulamalarda barındırıldığı zaman uygulama ayarlarını kalıcı hale getirmek için bazı görevleri tamamlamalısınız.

 Uygulama ayarları özelliği hakkındaki belgelerin çoğu, tek başına bir uygulama oluşturduğunuz varsayımına göre yazılmıştır. Ancak, diğer geliştiricilerin uygulamalarında barındırmasını sağlayan bir denetim oluşturuyorsanız, denetiminizin ayarlarını düzgün bir şekilde kalıcı hale getirmek için birkaç ek adım uygulamanız gerekir.

## <a name="application-settings-and-custom-controls"></a>Uygulama ayarları ve özel denetimler
 Denetiminizin ayarlarını düzgün bir şekilde kalıcı hale getirmek için, ' den <xref:System.Configuration.ApplicationSettingsBase>türetilmiş kendi adanmış uygulama ayarları sarmalayıcı sınıfını oluşturarak işlemi kapsületmelidir. Ayrıca, ana denetim sınıfının uygulaması <xref:System.Configuration.IPersistComponentSettings>gerekir. Arabirim birçok özellik <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> ve <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>iki yöntem içerir. Denetiminizi, Visual Studio 'daki **Windows Form Tasarımcısı** kullanarak bir forma eklerseniz, Denetim başlatıldığında Windows Forms <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> otomatik olarak çağrılır; denetim `Dispose` yöntemi içinde kendi kendinize çağrı <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> yapmanız gerekir.

 Ayrıca, Özel denetimlerin uygulama ayarlarının Visual Studio gibi tasarım zamanı ortamlarında düzgün şekilde çalışması için aşağıdakileri uygulamalısınız:

1. Tek bir parametre <xref:System.ComponentModel.IComponent> olarak alan Oluşturucu içeren özel bir uygulama ayarları sınıfı. Tüm uygulama ayarlarınızı kaydetmek ve yüklemek için bu sınıfı kullanın. Bu sınıfın yeni bir örneğini oluşturduğunuzda, oluşturucuyu kullanarak özel denetiminizi geçirin.

2. Denetim oluşturulduktan ve formun <xref:System.Windows.Forms.Form.Load> olay işleyicisindeki gibi bir forma yerleştirildiğinde, bu özel ayarlar sınıfını oluşturun.

 Özel ayarlar sınıfı oluşturma yönergeleri için bkz [. nasıl yapılır: Uygulama ayarları](how-to-create-application-settings.md)oluşturun.

## <a name="settings-keys-and-shared-settings"></a>Ayarlar anahtarlar ve paylaşılan ayarlar
 Bazı denetimler aynı form içinde birden çok kez kullanılabilir. Çoğu zaman bu denetimlerin kendi bireysel ayarlarını kalıcı hale getirmek isteyeceksiniz. <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> Özelliğiile,birformüzerindebirdenetiminbirdençoksürümünüayırtetmekiçindavranan<xref:System.Configuration.IPersistComponentSettings>benzersiz bir dize sağlayabilirsiniz.

 Uygulamamanın <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> en kolay yolu, <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>için denetiminin <xref:System.Windows.Forms.Control.Name%2A> özelliğini kullanmaktır. Denetimin ayarlarını yüklediğinizde veya kaydettiğinizde, öğesinin <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> değerini <xref:System.Configuration.ApplicationSettingsBase> sınıfının özelliğine geçirirsiniz. Uygulama ayarları, kullanıcının ayarlarının XML olarak devam ettiği durumlarda bu benzersiz anahtarı kullanır. Aşağıdaki kod örneği, bir `<userSettings>` bölümün, `Text` özelliği için bir ayar kaydeden adlı `CustomControl1` bir özel denetimin örneğini nasıl arayacağı gösterilmektedir.

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 Bir denetimin değer <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> sağlamamayan tüm örnekleri aynı ayarları paylaşır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Uygulama Ayarları Mimarisi](application-settings-architecture.md)
