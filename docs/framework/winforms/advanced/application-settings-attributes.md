---
title: Uygulama Ayarları Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: b38ed931cab3a333a56dd027d5843b1c8f00dcb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916671"
---
# <a name="application-settings-attributes"></a>Uygulama Ayarları Öznitelikleri
Uygulama ayarları mimarisi, uygulama ayarları sarmalayıcı sınıfına veya tek tek özelliklerine uygulanabilen birçok öznitelik sağlar. Bu öznitelikler, çalışma zamanında uygulama ayarları altyapısı, genellikle özellikle ayar sağlayıcısı tarafından, çalışmasını özel sarmalayıcının belirtilen ihtiyaçlarına göre uyarlamak için bir şekilde incelenir.  
  
 Aşağıdaki tablo, uygulama ayarları sarmalayıcı sınıfına, bu sınıfın tek tek özelliklerine veya her ikisine de uygulanabilen öznitelikleri listeler. Tanım olarak, her bir ve her ayar özelliğine yalnızca tek bir kapsam özniteliği (**UserScopedSettingAttribute** veya **ApplicationScopedSettingAttribute**) uygulanmalıdır.  
  
> [!NOTE]
> <xref:System.Configuration.SettingsProvider> Sınıfından türetilen özel bir ayar sağlayıcısı yalnızca aşağıdaki üç özniteliği tanımak için gereklidir: **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**ve **DefaultSettingValueAttribute**.  
  
|Öznitelik|Hedef|Açıklama|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Her ikisi de|Kalıcılık için kullanılacak ayar sağlayıcısının kısa adını belirtir.<br /><br /> Bu öznitelik sağlanmazsa, varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>varsayılır.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Her ikisi de|Bir özelliği kullanıcı kapsamlı uygulama ayarı olarak tanımlar.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Her ikisi de|Bir özelliği uygulama kapsamlı uygulama ayarı olarak tanımlar.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Özellik|Bu özellik için sabit kodlanmış varsayılan değere sağlayıcı tarafından seri durumdan çıkarılacak bir dize belirtir.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Bu özniteliği gerektirmez ve zaten kalıcı bir değer varsa bu öznitelik tarafından belirtilen değeri geçersiz kılar.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Özellik|Öncelikle çalışma zamanı ve tasarım zamanı araçları tarafından kullanılan tek bir ayar için açıklayıcı test sağlar.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|örneği|Bir ayarlar grubu için açık bir ad sağlar. Bu öznitelik eksikse, <xref:System.Configuration.ApplicationSettingsBase> sarmalayıcı sınıf adını kullanır.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|örneği|Öncelikle çalışma zamanı ve tasarım zamanı araçları tarafından kullanılan bir ayarlar grubu için açıklayıcı test sağlar.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Her ikisi de|Ayarlar grubuna veya özelliğine sağlanması gereken sıfır veya daha fazla yönetilebilirlik hizmeti belirtir. Kullanılabilir hizmetler, <xref:System.Configuration.SettingsManageability> sabit listesi tarafından açıklanmıştır.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Özellik|Bir ayarın özel, önceden tanımlanmış bir kategoriye (örneğin, bir bağlantı dizesi) ait olduğunu belirtir. Bu, ayarlar sağlayıcısı tarafından özel işlem önerisinde bulunur. Bu öznitelik için önceden tanımlanmış kategoriler, <xref:System.Configuration.SpecialSetting> sabit listesi tarafından tanımlanır.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Her ikisi de|Bir ayarlar grubu veya özelliği için tercih edilen bir serileştirme mekanizmasını belirtir. Kullanılabilir serileştirme mekanizmaları <xref:System.Configuration.SettingsSerializeAs> Listeleme tarafından tanımlanır.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Özellik|Bir ayar sağlayıcısının, işaretlenmiş özellik için tüm uygulama yükseltme işlevlerini devre dışı bırakabilmelidir.|  
  
 *Sınıf* , özniteliğin yalnızca bir uygulama ayarları sarmalayıcı sınıfına uygulanabileceğini gösterir. *Özelliği* , özniteliğin yalnızca ayarlar özellikleri uygulanabileceğini gösterir. *Her Ikisi de* özniteliğin her Iki düzeyde de uygulanabileceğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [Uygulama Ayarları Mimarisi](application-settings-architecture.md)
- [Nasıl yapılır: Uygulama ayarları oluştur](how-to-create-application-settings.md)
