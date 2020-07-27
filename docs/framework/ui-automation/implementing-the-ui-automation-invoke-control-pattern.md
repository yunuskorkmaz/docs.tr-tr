---
title: UI Otomasyon Çağırma Denetim Düzenini Uygulama
description: UI otomasyonunda Invoke denetim deseninin uygulanması için yönergeleri ve kuralları okuyun. IInvokeProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: b464b3ab5cd2b0789798f8b865b946c5eae017eb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166172"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>UI Otomasyon Çağırma Denetim Düzenini Uygulama

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konu <xref:System.Windows.Automation.Provider.IInvokeProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.

<xref:System.Windows.Automation.InvokePattern>Denetim stili, etkinleştirildiğinde durumu korumayan ancak tek, belirsiz bir eylem başlatan veya gerçekleştiren denetimleri desteklemek için kullanılır. Onay kutuları ve radyo düğmeleri gibi durum koruması olan denetimler bunun yerine <xref:System.Windows.Automation.Provider.IToggleProvider> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider> sırasıyla kullanılmalıdır. Invoke denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları

Invoke denetim deseninin uygulanması sırasında, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:

- <xref:System.Windows.Automation.Provider.IInvokeProvider>Aynı davranış başka bir denetim örüntüsünün içinden gösterilmediği takdirde, denetimleri uygular. Örneğin, <xref:System.Windows.Automation.InvokePattern.Invoke%2A> bir denetimdeki Yöntem veya yöntemiyle aynı eylemi gerçekleştiriyorsa <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> , denetim uygulamamalıdır <xref:System.Windows.Automation.Provider.IInvokeProvider> .

- Bir denetimi çağırmak, genellikle ENTER 'a tıklanması veya çift tıklanması ya da önceden tanımlanmış bir klavye kısayolu ya da birkaç tuş vuruşu birleşimi tarafından gerçekleştirilir.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>, etkinleştirilmiş bir denetimde oluşturulur (ilişkili eylemini gerçekleştiren bir denetime yanıt olarak). Mümkünse, Denetim eylemi tamamladıktan ve engellenmeden sonra olay tetiklenir. Çağrılan olay, aşağıdaki senaryolarda Invoke isteğine hizmet vermeden önce oluşturulmalıdır:

  - Eylem tamamlanana kadar beklemeniz mümkün değildir veya pratik değildir.

  - Eylem Kullanıcı etkileşimi gerektirir.

  - Eylem zaman alır ve çağıran istemcinin önemli bir süre için engellenmesine neden olur.

- Denetimin çağrılması önemli yan etkilere sahipse, bu yan etkiler özelliği aracılığıyla gösterilmelidir <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> . Örneğin, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> seçimle ilişkili olmasa bile, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> başka bir denetimin seçili olmasına neden olabilir.

- Üzerine gelme (veya fare üzerinden) etkileri genellikle çağrılan bir olay oluşturmamaktadır. Ancak, üzerine gelme durumuna bağlı olarak bir eylem gerçekleştiren (görsel efekte değil) denetimlerin <xref:System.Windows.Automation.InvokePattern> Denetim modelini desteklemesi gerekir.

> [!NOTE]
> Bu uygulama, denetimin yalnızca fareyle ilgili bir yan etkisi sonucu olarak çağrılabilir olması halinde bir erişilebilirlik sorunu olarak kabul edilir.

- Bir denetimi çağırmak bir öğe seçmeden farklıdır. Ancak, denetime bağlı olarak, öğesinin çağrılması öğenin yan etkisi olarak seçili olmasına neden olabilir. Örneğin, Belgelerim klasöründeki bir Microsoft Word belge listesi öğesini çağırmak öğeyi seçer ve belgeyi açar.

- Bir öğe, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrıldığında hemen sonra görünümden kaybolur. Olay geri çağırması tarafından belirtilen öğeden bilgi istemek bir sonuç olarak başarısız olabilir. Önbelleğe alınan bilgileri önceden getirme önerilen geçici çözümdür.

- Denetimler, birden çok denetim deseni uygulayabilir. Örneğin, Microsoft Excel araç çubuğundaki Fill Color denetimi hem hem de <xref:System.Windows.Automation.InvokePattern> <xref:System.Windows.Automation.ExpandCollapsePattern> Denetim düzenlerini uygular. <xref:System.Windows.Automation.ExpandCollapsePattern>menüyü gösterir ve <xref:System.Windows.Automation.InvokePattern> etkin seçimi seçilen renkle doldurur.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>IInvokeProvider için gerekli Üyeler

Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IInvokeProvider> .

|Gerekli Üyeler|Üye türü|Notlar|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|method|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>zaman uyumsuz bir çağrıdır ve engelleme olmadan hemen dönmesi gerekir.<br /><br /> Bu davranış, çağrıldığında doğrudan veya dolaylı olarak, çağrıldığında kalıcı iletişim kutusu Başlatan denetimler için özellikle önemlidir. Kalıcı iletişim kutusu kapatılıncaya kadar olayı kapatan herhangi bir UI Otomasyon istemcisi engellenmiş olarak kalır.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Özel durumlar

Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.

|Özel durum türü|Koşul|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkinleştirilmemişse.|

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Denetim Çağırma](invoke-a-control-using-ui-automation.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
