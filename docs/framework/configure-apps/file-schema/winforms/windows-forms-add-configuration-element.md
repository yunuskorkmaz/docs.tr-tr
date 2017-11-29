---
title: "Windows Forms yapılandırma öğesi Ekle"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 367ca30c577cbb4ed7fed130bdcbd4faac2d46c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms yapılandırma öğesi Ekle

`<add>` Öğesi Windows Form uygulamanızı Windows Forms uygulamaları için .NET Framework 4.7 ya da daha sonra eklenen özellikler destekleyip desteklemediğini belirtir önceden tanımlanmış bir anahtar ekler.

## <a name="syntax"></a>Sözdizimi

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
| `key`     | Gerekli öznitelik. Belirli bir Windows Forms özelleştirilebilir özellik karşılık gelen önceden tanımlanmış bir anahtar adı. |
| `value`   | Gerekli öznitelik. Değer atamak için `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key`öznitelik adları ve ilişkili değerleri

| `key`adı | Değerler | Açıklama |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true" &#124;" false" | Bağlantılı denetimleri tek geçişte ölçeklenir olup olmadığını gösterir. tek devre dışı bırakmak için "true" ölçeklendirme geçirin; Aksi takdirde false. "Tek geçirmek ölçeklendirme" bölümüne bakın [açıklamalar](#Remarks) daha fazla bilgi için. |
| "DpiAwareness" | "PerMonitorV2" &#124;" false" | Bir uygulama DPI olup olmadığını gösterir. DPI tanıma; desteklemek için "PerMonitorV2" anahtarına ayarlayın Aksi takdirde, "false" olarak ayarlanmış. DPI tanıma, bir katılımı özelliğidir; Windows Forms yüksek DPI desteğinin yararlanmak için "PerMonitorV2" değerine ayarlamanız gerekir. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm. |
| "CheckedListBox.DisableHighDpiImprovements" | "true" &#124;" false" | Gösterir olup olmadığını <xref:System.Windows.Forms.CheckedListBox> denetim .NET Framework 4.7 sunulan ölçekleme ve düzeni geliştirmeleri avantajlarından yararlanır. "true" caling ve düzeni geliştirmeleri dışında kabul etmek için; Aksi durumda, "false". |
| "DataGridView.DisableHighDpiImprovements" | "true" &#124;" false" | Gösterir olup olmadığını <xref:System.Windows.Forms.DataGridView> denetlemek .NET Framework 4.7 sunulan ölçekleme ve düzeni geliştirmeleri. "true" DPI tanıma dışında kabul etmek için; "false" Aksi takdirde. |
| "DisableDpiChangedMessageHandling" | "true" &#124;" false" | "true" değişiklikleri ölçeklendirme DPI ilgili iletileri alma dışında kabul etmek için; "false" Aksi takdirde. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true" &#124;" false" | Bir Windows Forms uygulaması DPI ölçeklendirme değişiklikler nedeniyle otomatik olarak yeniden boyutlandırılır olup olmadığını gösterir. "true" otomatik yeniden boyutlandırma etkinleştirmek için; Aksi takdirde false. |
| "Form.DisableSinglePassControlScaling" | "true" &#124;" false" | Gösterir olup olmadığını <xref:System.Windows.Forms.Form> tek geçişte ölçeklendirilir. devre dışı bırakmak için "true" tek ölçeklendirme geçiş; Aksi takdirde false. "Tek geçirmek ölçeklendirme" bölümüne bakın [açıklamalar](#Remarks) daha fazla bilgi için. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true" &#124;" false" | Gösterir olup olmadığını <xref:System.Windows.Forms.MonthCalendar> denetim tek geçişte ölçeklendirilebilir. devre dışı bırakmak için "true" tek ölçeklendirme geçiş; Aksi takdirde false. "Tek geçirmek ölçeklendirme" bölümüne bakın [açıklamalar](#Remarks) daha fazla bilgi için. |
| "Toolstrip.DisableHighDpiImprovements" | "true" &#124;" false" | Gösterir olup olmadığını <xref:System.Windows.Forms.ToolStrip> denetim .NET Framework 4.7 sunulan ölçekleme ve düzeni geliştirmeleri avantajlarından yararlanır. "true" DPI tanıma dışında kabul etmek için; "false" Aksi takdirde. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Yeni Windows Forms uygulaması özellikleri için destek yapılandırır. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" />Açıklamalar

.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza olanak sağlar. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Öğesi bir veya daha fazla alt eklemenizi sağlayan `<add>` öğeleri, her biri belirli bir yapılandırma ayarını tanımlar.  

Windows Forms yüksek DPI Destek genel bakış için bkz: [yüksek DPI destekleyen Windows Forms'ta](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

.NET Framework sunulan yüksek DPI geliştirmeleri avantajlarından yararlanmak için .NET Framework 4.7 ile başlayan Windows 10 oluşturucuları Edition ve hedef .NET Framework sürümleri ile başlayarak Windows sürümleri altında çalışacağı Windows Forms uygulamaları yapılandırılabilir 4.7. Bu güncelleştirmeler şunlardır:

- Bir Windows Forms uygulaması başlatıldıktan sonra kullanıcı DPI veya ölçek faktörü değişiklikleri dinamik DPI senaryolar için destek.

- Gibi ölçekleme ve çok sayıda Windows Forms düzeni geliştirmeler denetimleri <xref:System.Windows.Forms.MonthCalendar> denetim ve <xref:System.Windows.Forms.CheckedListBox> denetim. 

Yüksek DPI tanıma, bir katılımı özelliğidir; Varsayılan olarak, değeri `DpiAwareness` olan `false`. Bu anahtarın değeri ayarlayarak Windows Forms desteği için DPI tanıma seçebilirsiniz `PerMonitorV2` uygulama yapılandırma dosyasında. DPI tanıma etkinleştirilirse, tüm tek tek DPI özellikleri de etkinleştirilir. Bu güncelleştirmeler şunlardır:

- DPI değiştirilen tarafından denetlenen iletileri `DisableDpiChangedMessageHandling` anahtarı.

- Tarafından denetlenen dinamik DPI desteği `EnableWindowsFormsHighDpiAutoResizing` anahtarı.

- Tek denetim ölçeklendirme, tarafından denetlenen geçiş `Form.DisableSinglePassControlScaling` kişi için <xref:System.Windows.Forms.Form> göre denetimleri `AnchorLayout.DisableSinglePassControlScaling` bağlantılı denetimleri için ve tarafından anahtar `MonthCalendar.DisableSinglePassControlScaling` için anahtar <xref:System.Windows.Forms.MonthCalendar> denetimi 

- Denetlenen yüksek DPI ölçekleme ve düzeni geliştirmeleri, `CheckListBox.DisableHighDpiImprovements` için anahtar <xref:System.Windows.Forms.CheckedListBox> göre denetimi `DataGridView.DisableHighDpiImprovements` için anahtar <xref:System.Windows.Forms.DataGridView> denetimi kullanarak ve `Toolstrip.DisableHighDpiImprovements` için anahtar <xref:System.Windows.Forms.ToolStrip> denetim.  

Ayarı sağlanan tek varsayılan katılımı ayar `DpiAwareness` için `PerMonitorV2` yeni Windows Forms uygulamaları için genellikle yeterlidir. Ancak, uygulama yapılandırma dosyasına karşılık gelen anahtarı ekleyerek dışında tek tek yüksek DPI geliştirmeleri sonra seçebilirsiniz. Örneğin, dinamik DPI desteği hariç tüm yeni DPI featuers yararlanmak için aşağıdaki uygulama yapılandırma dosyasına eklediğiniz:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Genellikle, programlı olarak işlemek seçtiğiniz çünkü dışında belirli bir özellik kabul et.

Windows Forms uygulamalarında yüksek DPI desteği alma Avantajı hakkında daha fazla bilgi için bkz: [yüksek DPI destekleyen Windows Forms'ta](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

.NET Framework 4.7 ile başlayarak, Windows Forms denetimleri DPI ölçeklendirme değişiklikler ile ilgili olay sayısı yükseltin. Bunlar <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, ve <xref:System.Windows.Forms.Form.DpiChanged> olaylar. Değeri `DisableDpiChangedMessageHandling` anahtarı bu olayları bir Windows Forms uygulamasında oluşturup oluşturmadığını belirler. 

### <a name="single-pass-scaling"></a>Tek geçişi ölçeklendirme

Ölçek tek veya çok geçişi etkiler kullanıcı arabiriminin algılanan yanıtlama ve bunlar ölçeklenir gibi görünümünü kullanıcı arabirim öğeleri. .NET Framework 4.7 ile başlayarak, Windows Forms tek geçişi ölçeklendirme kullanır. .NET Framework önceki sürümlerde ölçeklendirme hangi ölçeklendirilmesi için bazı denetimler neden birden çok gerekli birden çok geçer gerçekleştirildi. Uygulamanızı eski davranışı bağımlıysa tek geçişi ölçeklendirme yalnızca devre dışı gerekir.  

## <a name="see-also"></a>Ayrıca bkz.
 
[Windows Forms yapılandırma bölümü](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Windows Forms'ta yüksek DPI desteği](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
