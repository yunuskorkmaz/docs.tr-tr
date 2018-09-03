---
title: Uygulama Ayarları Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: 9ed549cb1e10b22c4fa34d984133a6be11dfab44
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481168"
---
# <a name="application-settings-attributes"></a>Uygulama Ayarları Öznitelikleri
Uygulama ayarları mimarisi, uygulama ayarlarını sarmalayıcı sınıfı veya bireysel özelliklerini uygulanabilir birçok öznitelikleri sağlar. Bu öznitelikler çalışma zamanında uygulama ayarları altyapısı tarafından genellikle özel ayar sağlayıcısı kendi işlevi için belirtilen özel bir sarmalayıcı gereksinimlerine uyarlamak için incelenir.  
  
 Aşağıdaki tabloda, uygulama ayarlarını sarmalayıcı sınıfı, bu sınıfın tek tek özellikler veya her ikisi de uygulanabilir öznitelikleri listeler. Tanım, yalnızca tek bir kapsam özniteliği tarafından —**UserScopedSettingAttribute** veya **ApplicationScopedSettingAttribute**— Ayarları özelliğini her uygulanmış olması gerekir.  
  
> [!NOTE]
>  Özel ayarlar sağlayıcısı, türetilen <xref:System.Configuration.SettingsProvider> sınıfı, yalnızca aşağıdaki üç öznitelikleri tanımak için gereklidir: **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**, ve **DefaultSettingValueAttribute**.  
  
|Öznitelik|Hedef|Açıklama|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Her ikisi de|Kalıcılık için kullanılacak ayarları sağlayıcının kısa adını belirtir.<br /><br /> Bu öznitelik sağlanmazsa, varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>, varsayılır.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Her ikisi de|Bir özelliği, bir uygulamanın kullanıcı kapsamlı ayarı olarak tanımlar.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Her ikisi de|Bir özellik olarak bir uygulama kapsamlı uygulama ayarı tanımlar.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Özellik|Sağlayıcı tarafından bu özellik için sabit kodlu varsayılan değerine seri durumdan çıkarılabiliyorsa bir dize belirtir.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Bu özniteliği gerektirmez ve bu özniteliği tarafından varsa bir değer zaten kalıcı sağlanan herhangi bir değer kılar.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Özellik|Öncelikli olarak çalışma zamanı ve tasarım zamanı araçları tarafından kullanılan tek bir ayar açıklayıcı test sağlar.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|örneği|Ayarları grubu için açık bir ad sağlar. Bu öznitelik yoksa, <xref:System.Configuration.ApplicationSettingsBase> sarmalayıcı sınıf adını kullanır.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|örneği|Açıklayıcı test öncelikli olarak çalışma zamanı ve tasarım zamanı araçları tarafından kullanılan bir ayarları grubu sağlar.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Her ikisi de|Sıfır veya daha fazla yönetilebilirlik Hizmetleri ayarları Grup veya özellik için sağlanmalıdır belirtir. Kullanılabilir hizmetleri tarafından açıklanan <xref:System.Configuration.SettingsManageability> sabit listesi.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Özellik|Bir ayar ayar sağlayıcısı tarafından özel işleme öneren bir bağlantı dizesi gibi özel, önceden tanımlanmış bir kategoriye ait olduğunu gösterir. Bu öznitelik için tanımlanmış kategorilerle tarafından tanımlanan <xref:System.Configuration.SpecialSetting> sabit listesi.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Her ikisi de|Ayarlar Grup veya özellik için bir tercih edilen seri hale getirme mekanizmasını belirtir. Kullanılabilir serileştirme mekanizması tarafından tanımlanan <xref:System.Configuration.SettingsSerializeAs> sabit listesi.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Özellik|İşaretli bir özellik için tüm uygulama yükseltmesi işlevi bir ayar sağlayıcısı devre dışı bırakmalısınız belirtir.|  
  
 *Sınıf* özniteliği yalnızca bir uygulama ayarları sarmalayıcı sınıfı için uygulanabilir gösterir. *Özellik* uygulanan ayarları özellikler yalnızca öznitelik olabileceğini gösterir. *Her ikisi de* belirten özniteliği ya da düzeyinde uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [Uygulama Ayarları Mimarisi](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Nasıl yapılır: Uygulama Ayarları Oluşturma](https://msdn.microsoft.com/library/53b3af80-1c02-4e35-99c6-787663148945)
