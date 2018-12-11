---
title: Windows Forms yapılandırma öğesi Ekle
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cb0d058cd1ade65bfdc966819c0c41d9c1a9750
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155099"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms yapılandırma öğesi Ekle

`<add>` Öğesi Windows Form uygulamanıza Windows Forms uygulamaları için .NET Framework 4.7 veya daha sonra eklenen özellikler destekleyip desteklemediğini belirten bir önceden tanımlanmış bir anahtar ekler.

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
| `value`   | Gerekli öznitelik. Değeri atanacak `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key` öznitelik adları ve ilişkili değerleri

| `key` Adı | Değerler | Açıklama |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Bağlantılı denetimleri tek bir geçişinde ölçeklenir olup olmadığını gösterir. tek devre dışı bırakmak için "true" ölçeklendirme geçirin; Aksi takdirde false. "Tek ölçeklendirme başarılı" bölümüne bakın [açıklamalar](#Remarks) daha fazla bilgi için. |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Uygulamanın DPI kullanan olup olmadığını belirtir. DPI tanıma; desteklemek için "PerMonitorV2" anahtarına ayarlayın Aksi takdirde, "false" olarak ayarlayın. DPI tanıma, bir katılım özelliğidir; Windows Forms yüksek DPI desteği avantajlarından yararlanmak için "PerMonitorV2" değerine ayarlamanız gerekir. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için. |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | Belirtir olup olmadığını <xref:System.Windows.Forms.CheckedListBox> denetimi, .NET Framework 4.7 içinde tanıtılan ölçeklendirme ve Düzen geliştirmeleri avantajlarından yararlanır. "true" dışında caling ve Düzen iyileştirmeleri kabul etme; Aksi durumda, "false". |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | Belirtir olup olmadığını <xref:System.Windows.Forms.DataGridView> denetlemek .NET Framework 4.7 sunulan ölçeklendirme ve Düzen iyileştirmeleri. "true" dışında DPI tanıma kabul etme; "false" Aksi takdirde. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true" DPI ölçeklendirme değişiklikler için ilgili iletilerini alma dışında kabul etme; "false" Aksi takdirde. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Bir Windows Forms uygulaması DPI ölçeklendirme değişiklikleri nedeniyle otomatik olarak yeniden boyutlandırılır olup olmadığını gösterir. "true" otomatik yeniden boyutlandırma etkinleştirmek için; Aksi takdirde false. |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | Belirtir olup olmadığını <xref:System.Windows.Forms.Form> tek bir geçişinde ölçeklendirilir. devre dışı bırakmak için "true" tek ölçeklendirme geçişli; Aksi takdirde false. "Tek ölçeklendirme başarılı" bölümüne bakın [açıklamalar](#Remarks) daha fazla bilgi için. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | Belirtir olup olmadığını <xref:System.Windows.Forms.MonthCalendar> denetim tek bir geçişinde Ölçeklendirildi. devre dışı bırakmak için "true" tek ölçeklendirme geçişli; Aksi takdirde false. "Tek ölçeklendirme başarılı" bölümüne bakın [açıklamalar](#Remarks) daha fazla bilgi için. |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | Belirtir olup olmadığını <xref:System.Windows.Forms.ToolStrip> denetimi, .NET Framework 4.7 içinde tanıtılan ölçeklendirme ve Düzen geliştirmeleri avantajlarından yararlanır. "true" dışında DPI tanıma kabul etme; "false" Aksi takdirde. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Yeni Windows Forms uygulaması özellikleri için destek yapılandırır. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> Açıklamalar

.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza imkan sağlar. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Öğesi bir veya daha fazla alt eklemenizi sağlayan `<add>` öğeleri, her biri belirli yapılandırma ayarını tanımlar.  

Windows Forms yüksek DPI desteği genel bakış için bkz. [Windows Forms'ta yüksek DPI desteği](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

.NET Framework 4.7 ile başlayan Windows 10 Creators Edition ve .NET Framework sürümlerini hedef ile başlayan Windows sürümlerinde çalışması Windows Forms uygulamaları, .NET Framework'teki sunulan yüksek DPI geliştirmeleri avantajlarından yararlanmak için yapılandırılabilir 4.7. Bu güncelleştirmeler şunlardır:

- Bir Windows Forms uygulaması başlatıldıktan sonra kullanıcı DPI veya ölçek faktörü değişiklik dinamik DPI senaryolar için destek.

- Gibi ölçeklendirme ve düzen çok sayıda Windows Forms denetimleri <xref:System.Windows.Forms.MonthCalendar> denetimi ve <xref:System.Windows.Forms.CheckedListBox> denetimi. 

Yüksek DPI tanıma, bir katılım özelliğidir; Varsayılan olarak, değerini `DpiAwareness` olduğu `false`. Bu anahtar için değerini ayarlayarak Windows Forms desteği için DPI tanıma seçebilirsiniz `PerMonitorV2` uygulama yapılandırma dosyasında. DPI tanıma etkinleştirilirse DPI özellikleri tek tek de etkinleştirilir. Bu güncelleştirmeler şunlardır:

- DPI denetlediği iletileri değişti `DisableDpiChangedMessageHandling` anahtarı.

- Denetlenen dinamik DPI desteği `EnableWindowsFormsHighDpiAutoResizing` anahtarı.

- Tek denetimini ölçeklendirme, tarafından denetlenen geçişli `Form.DisableSinglePassControlScaling` kişi için <xref:System.Windows.Forms.Form> göre denetimleri `AnchorLayout.DisableSinglePassControlScaling` bağlantılı denetimleri için ve göre anahtar `MonthCalendar.DisableSinglePassControlScaling` anahtarını <xref:System.Windows.Forms.MonthCalendar> denetimi 

- Denetlenen yüksek DPI ölçeklendirme ve Düzen iyileştirmeler `CheckListBox.DisableHighDpiImprovements` için anahtar <xref:System.Windows.Forms.CheckedListBox> göre denetimi `DataGridView.DisableHighDpiImprovements` için anahtar <xref:System.Windows.Forms.DataGridView> denetimi ve `Toolstrip.DisableHighDpiImprovements` için anahtar <xref:System.Windows.Forms.ToolStrip> denetimi.  

Ayarlayarak sağlanan tek varsayılan kabul etme ayarı `DpiAwareness` için `PerMonitorV2` genellikle yeni bir Windows Forms uygulamaları için yeterlidir. Ancak, uygulama yapılandırma dosyasına karşılık gelen anahtar ekleyerek dışında ayrı yüksek DPI geliştirmeleri ardından seçebilirsiniz. Örneğin, dinamik DPI desteği hariç tüm yeni DPI featuers yararlanmak için uygulama yapılandırma dosyasına aşağıdaki eklersiniz:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Genellikle, programlı olarak işlemek seçtiğiniz çünkü belirli bir özellik dışında tercih et.

Windows Forms uygulamalarındaki yüksek DPI desteği alma Avantajı hakkında daha fazla bilgi için bkz. [Windows Forms'ta yüksek DPI desteği](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

.NET Framework 4.7 ile başlayarak, Windows Forms denetimleri DPI ölçeklendirme değişiklikler ilgili olayların sayısını artırabilir. Bunlar <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, ve <xref:System.Windows.Forms.Form.DpiChanged> olayları. Değerini `DisableDpiChangedMessageHandling` anahtarı bu olayları bir Windows Forms uygulamasında oluşturup oluşturmadığını belirler. 

### <a name="single-pass-scaling"></a>Tek geçişli ölçeklendirme

Bunlar artırıldıkça tek veya çoklu geçiş ölçeklendirme kullanıcı arabiriminin yanıt verebilirliği ve kullanıcı arabirimi öğeleri görünümünü etkiler. .NET Framework 4.7 ile başlayarak, Windows Forms tek parola ölçeklendirme kullanır. Önceki .NET Framework sürümlerinde, ölçeklendirme, gerekli birden ölçeklendirilmesi bazı denetimler neden birden çok geçer gerçekleştirildi. Uygulamanız eski davranışa bağlıysa tek geçişli ölçeklendirme yalnızca devre dışı gerekir.  

## <a name="see-also"></a>Ayrıca bkz.
 
[Windows Forms yapılandırma bölümü](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Windows Forms'ta yüksek DPI desteği](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
