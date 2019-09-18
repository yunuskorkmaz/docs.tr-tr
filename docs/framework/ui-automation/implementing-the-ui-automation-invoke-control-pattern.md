---
title: UI Otomasyon Çağırma Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: e9815e4c2c0740f213632681200e48c8e4786657
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043389"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>UI Otomasyon Çağırma Denetim Düzenini Uygulama

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.IInvokeProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.

<xref:System.Windows.Automation.InvokePattern> Denetim stili, etkinleştirildiğinde durumu korumayan ancak tek, belirsiz bir eylem başlatan veya gerçekleştiren denetimleri desteklemek için kullanılır. Onay kutuları ve radyo düğmeleri gibi durum koruması olan denetimler bunun yerine <xref:System.Windows.Automation.Provider.IToggleProvider> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider> sırasıyla kullanılmalıdır. Invoke denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları

Invoke denetim deseninin uygulanması sırasında, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:

- Aynı davranış <xref:System.Windows.Automation.Provider.IInvokeProvider> başka bir denetim örüntüsünün içinden gösterilmediği takdirde, denetimleri uygular. Örneğin, <xref:System.Windows.Automation.InvokePattern.Invoke%2A> bir denetimdeki Yöntem <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> veya <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> yöntemiyle aynı eylemi gerçekleştiriyorsa, denetim uygulamamalıdır <xref:System.Windows.Automation.Provider.IInvokeProvider>.

- Bir denetimi çağırmak, genellikle ENTER 'a tıklanması veya çift tıklanması ya da önceden tanımlanmış bir klavye kısayolu ya da birkaç tuş vuruşu birleşimi tarafından gerçekleştirilir.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>, etkinleştirilmiş bir denetimde oluşturulur (ilişkili eylemini gerçekleştiren bir denetime yanıt olarak). Mümkünse, Denetim eylemi tamamladıktan ve engellenmeden sonra olay tetiklenir. Çağrılan olay, aşağıdaki senaryolarda Invoke isteğine hizmet vermeden önce oluşturulmalıdır:

  - Eylem tamamlanana kadar beklemeniz mümkün değildir veya pratik değildir.

  - Eylem Kullanıcı etkileşimi gerektirir.

  - Eylem zaman alır ve çağıran istemcinin önemli bir süre için engellenmesine neden olur.

- Denetimin çağrılması önemli yan etkilere sahipse, bu yan etkiler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> özelliği aracılığıyla gösterilmelidir. Örneğin, seçimle ilişkili olmasa <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> bile, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> başka bir denetimin seçili olmasına neden olabilir.

- Üzerine gelme (veya fare üzerinden) etkileri genellikle çağrılan bir olay oluşturmamaktadır. Ancak, üzerine gelme durumuna bağlı olarak bir eylem gerçekleştiren (görsel efekte değil) denetimlerin <xref:System.Windows.Automation.InvokePattern> denetim modelini desteklemesi gerekir.

> [!NOTE]
> Bu uygulama, denetimin yalnızca fareyle ilgili bir yan etkisi sonucu olarak çağrılabilir olması halinde bir erişilebilirlik sorunu olarak kabul edilir.

- Bir denetimi çağırmak bir öğe seçmeden farklıdır. Ancak, denetime bağlı olarak, öğesinin çağrılması öğenin yan etkisi olarak seçili olmasına neden olabilir. Örneğin, Belgelerim klasöründeki bir [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belge listesi öğesini çağırmak öğeyi seçer ve belgeyi açar.

- Bir öğe, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrıldığında hemen sonra görünümden kaybolur. Olay geri çağırması tarafından belirtilen öğeden bilgi istemek bir sonuç olarak başarısız olabilir. Önbelleğe alınan bilgileri önceden getirme önerilen geçici çözümdür.

- Denetimler, birden çok denetim deseni uygulayabilir. Örneğin, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] araç çubuğundaki Fill Color denetimi <xref:System.Windows.Automation.InvokePattern> hem hem de <xref:System.Windows.Automation.ExpandCollapsePattern> denetim düzenlerini uygular. <xref:System.Windows.Automation.ExpandCollapsePattern>menüyü gösterir ve <xref:System.Windows.Automation.InvokePattern> etkin seçimi seçilen renkle doldurur.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>IInvokeProvider için gerekli Üyeler

Uygulamak <xref:System.Windows.Automation.Provider.IInvokeProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.

|Gerekli Üyeler|Üye türü|Notlar|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|yöntemi|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>zaman uyumsuz bir çağrıdır ve engelleme olmadan hemen dönmesi gerekir.<br /><br /> Bu davranış, çağrıldığında doğrudan veya dolaylı olarak, çağrıldığında kalıcı iletişim kutusu Başlatan denetimler için özellikle önemlidir. Kalıcı iletişim kutusu kapatılıncaya kadar olayı kapatan herhangi bir UI Otomasyon istemcisi engellenmiş olarak kalır.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Özel Durumlar

Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.

|Özel Durum Türü|Koşul|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkinleştirilmemişse.|

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Denetim Çağırma](invoke-a-control-using-ui-automation.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
