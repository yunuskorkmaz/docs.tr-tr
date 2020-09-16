---
title: Windows Forms yapılandırma öğesi Ekle
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
ms.openlocfilehash: dc1786f1f2dcc7bd01488dd24c6ef454f7e1cfbd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557638"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms yapılandırma öğesi Ekle

`<add>`Öğesi, Windows form uygulamanızın .NET Framework 4,7 veya sonraki sürümlerde Windows Forms uygulamalara eklenen özellikleri destekleyip desteklemediğini belirten önceden tanımlanmış bir anahtar ekler.

## <a name="syntax"></a>Syntax

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
| --------- | ----------- |
| `key`     | Gerekli öznitelik. Belirli bir Windows Forms özelleştirilebilir özelliğe karşılık gelen önceden tanımlanmış anahtar adı. |
| `value`   | Gerekli öznitelik. Atanacak değer `key` . |

### <a name="key-attribute-names-and-associated-values"></a>`key` öznitelik adları ve ilişkili değerler

| `key` ada | Değerler | Açıklama |
| ---------- | ------ | ----------- |
| "AnchorLayout. Disablesinglepasscontrolölçeklendirmesi" | "true" &#124; "false" | Bağlantılı denetimlerin tek bir geçişte ölçeklendirip ölçeklendirilmeyeceğini belirtir. Tek geçişli ölçeklendirmeyi devre dışı bırakmak için "true"; Aksi takdirde, false. Daha fazla bilgi için, bkz. [açıklamalar](#remarks) 'Daki "Tekli geçiş Ölçeklendirmesi" bölümü. |
| "Dpitanıma" | "PerMonitorV2" &#124; "false" | Bir uygulamanın DPı duyarlı olup olmadığını gösterir. DPI tanımayı desteklemek için anahtarı "PerMonitorV2" olarak ayarlayın; Aksi takdirde, bunu "false" olarak ayarlayın. DPı tanıma, bir katılım özelliğidir; Windows Forms ' yüksek DPı desteğinin avantajlarından yararlanmak için değerini "PerMonitorV2" olarak ayarlamanız gerekir. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. |
| "CheckedListBox. Disablehighdpiiyileştirmeler" | "true" &#124; "false" | <xref:System.Windows.Forms.CheckedListBox>Denetimin .NET Framework 4,7 ' de tanıtılan ölçeklendirme ve düzen geliştirmelerinden faydalanıp yararlanmadığını gösterir. ölçeklendirmeyi ve düzen geliştirmelerini devre dışı bırakmak için "true"; Aksi takdirde, "false". |
| "DataGridView. Disablehighdpiiyileştirmeler" | "true" &#124; "false" | <xref:System.Windows.Forms.DataGridView>Denetim ölçeklendirmesinin ve düzen geliştirmelerinden .NET Framework 4,7 ' de tanıtıldığını gösterir. DPı tanımayı devre dışı bırakmak için "true"; Aksi takdirde "false". |
| "DisableDpiChangedMessageHandling" | "true" &#124; "false" | DPı ölçeklendirme değişiklikleriyle ilgili iletileri almayı devre dışı bırakmak için "true"; Aksi takdirde "false". Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. |
| Dosyasından enablewindowsformshighdpiautoresizing | "true" &#124; "false" | DPı ölçeklendirme değişikliklerinden dolayı bir Windows Forms uygulamasının otomatik olarak yeniden boyutlandırılıp boyutlandırılmayacağını belirtir. Otomatik yeniden boyutlandırmayı etkinleştirmek için "true"; Aksi takdirde, false. |
| "Form. Disablesinglepasscontrolölçeklendiriliyor" | "true" &#124; "false" | <xref:System.Windows.Forms.Form>' Nin tek bir geçişte ölçeklendirip ölçeklendirilmediğini belirtir. Tek geçişli ölçeklendirmeyi devre dışı bırakmak için "true"; Aksi takdirde, false. Daha fazla bilgi için, bkz. [açıklamalar](#remarks) 'Daki "Tekli geçiş Ölçeklendirmesi" bölümü. |
| "MonthCalendar. Disablesinglepasscontrolölçeklendirmesi" | "true" &#124; "false" | <xref:System.Windows.Forms.MonthCalendar>Denetimin tek bir geçişte ölçeklendirip ölçeklendirilmediğini belirtir. Tek geçişli ölçeklendirmeyi devre dışı bırakmak için "true"; Aksi takdirde, false. Daha fazla bilgi için, bkz. [açıklamalar](#remarks) 'Daki "Tekli geçiş Ölçeklendirmesi" bölümü. |
| "ToolStrip. Disablehighdpiiyileştirmeler" | "true" &#124; "false" | <xref:System.Windows.Forms.ToolStrip>Denetimin .NET Framework 4,7 ' de tanıtılan ölçeklendirme ve düzen geliştirmelerinden faydalanıp yararlanmadığını gösterir. DPı tanımayı devre dışı bırakmak için "true"; Aksi takdirde "false". |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | Yeni Windows Forms uygulama özellikleri için destek yapılandırır. |

## <a name="remarks"></a>Açıklamalar

.NET Framework 4,7 ' den başlayarak, `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamalarını yapılandırmanıza olanak tanır.

`<System.Windows.Forms.ApplicationConfigurationSection>`Öğesi `<add>` , her biri belirli bir yapılandırma ayarını tanımlayan bir veya daha fazla alt öğe eklemenize olanak tanır.

Windows Forms yüksek DPı desteğine genel bakış için bkz. [Windows Forms yüksek DPI desteği](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms).

### <a name="dpiawareness"></a>Dpitanıma

Windows 10 Creators Edition ve .NET Framework 4,7 ile başlayan .NET Framework hedef sürümleriyle başlayan Windows Forms uygulamalar, .NET Framework 4,7 ' de sunulan yüksek DPı geliştirmelerinden faydalanmak için yapılandırılabilir. Bu güncelleştirmeler şunlardır:

- Windows Forms bir uygulama başlatıldıktan sonra kullanıcının DPı veya ölçek faktörünü değiştirdiği dinamik DPı senaryoları için destek.

- Denetim ve denetim gibi bir dizi Windows Forms denetiminin ölçeklendirilmesine ve düzenine yönelik iyileştirmeler <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> .

Yüksek DPı tanıma, bir katılım özelliğidir; Varsayılan olarak, değeri `DpiAwareness` `false` . Bu anahtarın değerini uygulama yapılandırma dosyasında olarak ayarlayarak DPı tanıma desteğini Windows Forms tercih edebilirsiniz `PerMonitorV2` . DPı tanıma etkinse, tüm tek DPı özellikleri de etkinleştirilir. Bu güncelleştirmeler şunlardır:

- Anahtar tarafından denetlenen DPı değiştirilmiş iletileri `DisableDpiChangedMessageHandling` .

- Anahtar tarafından denetlenen dinamik DPı desteği `EnableWindowsFormsHighDpiAutoResizing` .

- Tek `Form.DisableSinglePassControlScaling` tek denetimler için, <xref:System.Windows.Forms.Form> `AnchorLayout.DisableSinglePassControlScaling` bağlantılı denetimlerin anahtarına ve `MonthCalendar.DisableSinglePassControlScaling` <xref:System.Windows.Forms.MonthCalendar> denetimin anahtarına göre denetlenen tek geçişli denetim Ölçeklendirmesi

- Denetim için anahtar tarafından, denetim için anahtar ve denetimin anahtarı tarafından denetlenen yüksek DPı ölçeklendirme ve Düzen geliştirmeleri `CheckListBox.DisableHighDpiImprovements` <xref:System.Windows.Forms.CheckedListBox> `DataGridView.DisableHighDpiImprovements` <xref:System.Windows.Forms.DataGridView> `Toolstrip.DisableHighDpiImprovements` <xref:System.Windows.Forms.ToolStrip> .

Ayarıyla belirtilen tek varsayılan kabul etme ayarı, `DpiAwareness` `PerMonitorV2` Yeni Windows Forms uygulamaları için genellikle yeterlidir. Ancak, uygulama yapılandırma dosyasına karşılık gelen anahtarı ekleyerek tek başına yüksek DPı geliştirmelerinden vazgeçebilirsiniz. Örneğin, dinamik DPı desteği hariç tüm yeni DPı özelliklerinden yararlanmak için aşağıdaki uygulama yapılandırma dosyanıza ekleyin:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Genellikle, belirli bir özelliği, uygulamayı programlama yoluyla işlemeye seçtiğiniz için devre dışı bırakmış olursunuz.

Windows Forms uygulamalarında yüksek DPı desteğinin avantajlarından yararlanma hakkında daha fazla bilgi için, bkz. [Windows Forms yüksek DPI desteği](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms).

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

.NET Framework 4,7 ' den başlayarak, Windows Forms denetimleri DPı ölçeklendirirken değişikliklerle ilgili birkaç olay yükseltir. Bunlar, <xref:System.Windows.Forms.Control.DpiChangedAfterParent> <xref:System.Windows.Forms.Control.DpiChangedBeforeParent> ve <xref:System.Windows.Forms.Form.DpiChanged> olaylarını içerir. Anahtarın değeri, `DisableDpiChangedMessageHandling` Bu olayların bir Windows Forms uygulamasında oluşturulup oluşturulmayacağını belirler.

### <a name="single-pass-scaling"></a>Tek geçişli ölçekleme

Tek veya çok taramalı ölçekleme, Kullanıcı arabiriminin algılanan yanıt hızını ve ölçeklendiği gibi kullanıcı arabirimi öğelerinin görsel görünümünü etkiler. .NET Framework 4,7 ' den başlayarak, Windows Forms tek geçişli ölçeklendirmeyi kullanır. .NET Framework önceki sürümlerinde ölçeklendirme, bazı denetimlerin gerekenden daha fazla ölçeklendirilmesine neden olan birden çok geçiş ile gerçekleştirildi. Tek geçişli ölçekleme yalnızca uygulamanız eski davranışa bağımlıysa devre dışı bırakılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms yapılandırma bölümü](index.md)
- [Windows Forms yüksek DPı desteği](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
