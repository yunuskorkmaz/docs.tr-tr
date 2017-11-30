---
title: "Uygulama Ayarları Öznitelikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1879ac6704619092c4c0d9cd6fab0356ea07a13d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-attributes"></a>Uygulama Ayarları Öznitelikleri
Uygulama ayarları mimarisi uygulamaları ayarları sarmalayıcı sınıfı veya tek tek özellikleri uygulanabilir birçok öznitelikleri sağlar. Bu öznitelikler çalışma zamanında uygulama ayarları altyapısı tarafından genellikle özellikle ayarları sağlayıcısı çalışan kendi özel sarmalayıcı belirtilen gereksinimlerine uyarlamak için incelenir.  
  
 Aşağıdaki tabloda, uygulama ayarları sarmalayıcı sınıfı, bu sınıfın tek tek özellikleri veya her ikisi de uygulanabilir öznitelikleri listeler. Tanımı, yalnızca tek bir kapsam özniteliği tarafından —**UserScopedSettingAttribute** veya **ApplicationScopedSettingAttribute**— her Ayarları özelliğini uygulanmış olması gerekir.  
  
> [!NOTE]
>  Bir özel ayarlar sağlayıcısı, türetilen <xref:System.Configuration.SettingsProvider> sınıfı, yalnızca aşağıdaki üç öznitelikleri tanımak için gereklidir: **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**, ve **DefaultSettingValueAttribute**.  
  
|Öznitelik|Hedef|Açıklama|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Her ikisi|Kısa kalıcılığını için kullanılan ayarları sağlayıcının adını belirtir.<br /><br /> Bu öznitelik sağlanmazsa, varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>, varsayılır.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Her ikisi|Bir özelliği bir kullanıcı kapsamlı uygulama ayarı olarak tanımlar.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Her ikisi|Bir özelliği bir uygulama kapsamlı uygulama ayarı olarak tanımlar.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Özellik|Bu özellik için sabit kodlanmış varsayılan değer içine sağlayıcı tarafından seri durumdan çıkarılabiliyorsa bir dizeyi belirtir.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Bu özniteliği gerektirmez ve bu öznitelik tarafından varsa bir değer zaten kalıcı sağlanan herhangi bir değer geçersiz kılar.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Özellik|Öncelikle çalışma zamanı ve tasarım zamanı araçları tarafından kullanılan tek bir ayar için açıklayıcı test sağlar.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|örneği|Ayarlar Grup için açıkça bir ad sağlar. Bu öznitelik yoksa, <xref:System.Configuration.ApplicationSettingsBase> sarmalayıcı sınıfı adını kullanır.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|örneği|Öncelikle çalışma zamanı ve tasarım zamanı araçları tarafından kullanılan ayarları grubu, açıklayıcı test sağlar.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Her ikisi|Ayarlar Grup veya özellik sağlanmalıdır sıfır veya daha fazla yönetilebilirlik Hizmetleri belirtir. Kullanılabilir hizmetler tarafından açıklanan <xref:System.Configuration.SettingsManageability> numaralandırması.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Özellik|Bir ayar ayarları sağlayıcısı tarafından özel işleme öneren bir bağlantı dizesi gibi özel, önceden tanımlı bir kategoriye ait olduğunu gösterir. Bu öznitelik için tanımlanmış kategorilerle tarafından tanımlanan <xref:System.Configuration.SpecialSetting> numaralandırması.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Her ikisi|Ayarlar Grup veya özellik için tercih edilen seri hale getirme mekanizmasını belirtir. Kullanılabilir seri hale getirme mekanizmaları tarafından tanımlanan <xref:System.Configuration.SettingsSerializeAs> numaralandırması.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Özellik|Ayarları sağlayıcısı işaretli bir özellik için tüm uygulama yükseltme işlevselliği devre dışı bırakmalısınız belirtir.|  
  
 *Sınıf* özniteliği yalnızca bir uygulama ayarları sarmalayıcı sınıfı için uygulanabilir gösterir. *Özellik* özniteliği yalnızca uygulanan ayarları özellikleri olabileceğini gösterir. *Her ikisi de* özniteliği ya da düzeyinde uygulanabilir gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [Uygulama ayarları mimarisi](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Nasıl yapılır: uygulama ayarları oluştur](http://msdn.microsoft.com/en-us/53b3af80-1c02-4e35-99c6-787663148945)
