---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616304"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a>.NET 4,8 için Windows Forms Denetimlerinde erişilebilirlik geliştirmeleri

#### <a name="details"></a>Ayrıntılar

Windows Forms Framework, Windows Forms müşterileri daha iyi destekleyecek şekilde erişilebilirlik teknolojileriyle nasıl çalıştığını iyileştirmeye devam etmektedir. Bunlar aşağıdaki değişiklikleri içerir:

- Yüksek Karşıtlık modunda görüntülemeyi artırmak için değişiklikler.
- Ekran okuyucusu ile etkileşim olarak değişir.
- Erişilebilir hiyerarşideki değişiklikler (UI Otomasyon ağacı aracılığıyla gezinmeyi geliştirir).

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4,8 üzerinde çalışması gerekir. Uygulama, aşağıdaki yollarla bu değişiklikleri kabul edebilir:

- .NET Framework 4,8 ' i hedeflemek için yeniden derlenir. Bu erişilebilirlik değişiklikleri, .NET Framework 4,8 ' i hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilmiştir.
- [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` Aşağıdaki örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve ' ı ' a ayarlayarak, .NET Framework 4.7.2 veya önceki bir sürümü, eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

.NET Framework 4,8 ' de eklenen erişilebilirlik özelliklerini kabul etmek için ayrıca .NET Framework 4.7.1 ve 4.7.2 erişilebilirlik özelliklerini de kabul etmeniz gerektiğini unutmayın. .NET Framework 4,8 ' i hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` . Klavye araç Ipucu çağırma desteğini etkinleştirmek için `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` satırın AppContextSwitchOverrides değerine eklenmesi gerekir:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

Bu özelliğin etkinleştirilmesinde, .NET Framework 4.7.1-4,8 ' nin belirtilen erişilebilirlik özelliklerine yönelik olarak etkinleştirilmesi gerektiğini unutmayın. Ayrıca, erişilebilirlik özelliklerinden herhangi biri kabul edilmez ancak araç ipucu görüntüleme özelliği kabul edildiğinde, <xref:System.NotSupportedException> Bu özelliklere ilk erişimde bir çalışma zamanı atılır. Özel durum iletisi, klavye araç Ipuçlarının etkinleştirilecek düzey 3 ' ün erişilebilirlik geliştirmeleri gerektirdiğini gösterir.

**Yüksek Karşıtlık Temaları 'nda işletim sistemi tanımlı renklerin kullanımı**

- Gelişmiş yüksek karşıtlıklı Temalar.

**İyileştirilmiş ekran okuyucusu desteği**

- Ekran okuyucusu artık <xref:System.Windows.Forms.DataGridViewColumn> erişilebilir bir adı duyurusu yaparken öğesinin sıralama yönünü duyurur <xref:System.Windows.Forms.DataGridViewCell> .

**Geliştirilmiş CheckedListBox erişilebilirlik desteği**

- Denetim için iyileştirilmiş ekran okuyucusu desteği <xref:System.Windows.Forms.CheckedListBox> . <xref:System.Windows.Forms.CheckedListBox>Klavye kullanılarak denetime gezinilirken, ekran okuyucusu öğeyi odaklar <xref:System.Windows.Forms.CheckedListBox> ve duyurur.
- Boş bir CheckedListBox denetiminin artık, denetim odaklanıldığında bir sanal ilk öğe için çizilmiş bir odak dikdörtgeni vardır.

**Geliştirilmiş ComboBox erişilebilirlik desteği**

- <xref:System.Windows.Forms.ComboBox>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma olanağı sunan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.
**Geliştirilmiş DataGridView erişilebilirlik desteği**

- <xref:System.Windows.Forms.DataGridView>UI Otomasyonu bildirimlerini ve DIĞER UI Otomasyon özelliklerini kullanma yeteneği olan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.
- Ya da öğesine karşılık gelen UI Otomasyon öğesi <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> , <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> buna karşılık gelen bir Düzenle hücresinin alt öğesidir.

**İyileştirilmiş LinkLabel erişilebilirlik desteği**

- Gelişmiş <xref:System.Windows.Forms.LinkLabel> Denetim erişilebilirliği: ilgili <xref:System.Windows.Forms.LinkLabel> denetim devre dışı bırakılmışsa, ekran okuyucusu bağlantının devre dışı durumunu duyurur.

**Geliştirilmiş ProgressBar erişilebilirlik desteği**

- <xref:System.Windows.Forms.ProgressBar>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma özelliği ile denetim IÇIN UI Otomasyonu desteği etkinleştirildi. Geliştiriciler artık, ekran okuyucusu 'Nun ilerlemeyi göstermek için duyurabileceği Kullanıcı Arabirimi Otomasyonu bildirimlerini kullanabiliyor.
UI Otomasyonu olaylarına genel bakış için Kullanıcı Arabirimi Otomasyonu bildirim olayları dahil bir genel bakış için bkz. [UI Otomasyonu olaylarına genel](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview)bakış.

**Geliştirilmiş PropertyGrid erişilebilirlik desteği**

- <xref:System.Windows.Forms.PropertyGrid>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma olanağı sunan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.
- Şu anda düzenlenmekte olan özelliğe karşılık gelen UI Otomasyon öğesi artık ilgili özellik öğesi UI Otomasyon öğesinin bir alt öğesidir.
- Ana <xref:System.Windows.Forms.PropertyGrid> Denetim Kategori görünümü olarak AYARLANDıYSA UI Otomasyonu özellik öğesi öğesi artık karşılık gelen category öğesinin bir alt öğesidir.

**Geliştirilmiş ToolStrip desteği**

- <xref:System.Windows.Forms.ToolStrip>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma olanağı sunan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.
- Öğeler aracılığıyla geliştirilmiş gezinme <xref:System.Windows.Forms.ToolStrip> .
- Öğe modunda, ekran okuyucusu odağı görünmez ve gizli öğelere gitmez.

**Geliştirilmiş görsel ipuçları**

- Boş bir <xref:System.Windows.Forms.CheckedListBox> Denetim artık odak aldığında odak göstergesi görüntülüyor.
Not: UI Otomasyon desteği çalışma zamanında denetimler için etkinleştirilmiştir ancak tasarım zamanında kullanılmaz. UI Otomasyonu 'na genel bakış için bkz. [UI Otomasyonu genel bakış](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

**Denetimlerin klavye ile araç Ipuçlarını çağırma**

- Denetim araç ipucu artık, klavye ile denetim altına odaklanarak çağrılabilir. Bu özelliğin uygulama için açıkça etkinleştirilmesi gerekir ( ** &quot; Bu değişikliklerin &quot; nasıl kabul edilebilir veya devre dışı**kılındığı bölümüne bakın)

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |
