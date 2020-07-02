---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614871"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a>.NET 4.7.2 için Windows Forms Denetimlerinde erişilebilirlik geliştirmeleri

#### <a name="details"></a>Ayrıntılar

Windows Forms Framework, Windows Forms müşterileri daha iyi desteklemek için erişilebilirlik teknolojileriyle nasıl çalıştığını geliştirmektir. Bunlar aşağıdaki değişiklikleri içerir:

- Yüksek Karşıtlık modunda görüntülemeyi artırmak için değişiklikler.
- DataGridView ve MenuStrip denetimlerinde klavye gezintisini geliştirmek için değişiklikler.
- Ekran okuyucusu ile etkileşim olarak değişir.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.2 hedeflemek için yeniden derlenir. Bu erişilebilirlik değişiklikleri, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilmiştir.
- [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) `<runtime>` Aşağıdaki örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve ' ı ' a ayarlayarak, .NET Framework 4.7.1 veya önceki bir sürümü, eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

.NET Framework 4.7.2 ' de eklenen erişilebilirlik özelliklerini kabul etmek için .NET Framework 4.7.1 'nin erişilebilirlik özelliklerini de kabul etmeniz gerektiğini unutmayın. .NET Framework 4.7.2 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .

**Yüksek Karşıtlık Temaları 'nda işletim sistemi tanımlı renklerin kullanımı**

- ' In aşağı açılan oku, <xref:System.Windows.Forms.ToolStripDropDownButton> yüksek karşıtlık teması içinde işletim sistemi tanımlı renkler kullanır.
- <xref:System.Windows.Forms.Button><xref:System.Windows.Forms.RadioButton>ve, <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.ButtonBase.FlatStyle> <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> Seçili olduğunda yüksek karşıtlık teması içinde işletim sistemi tanımlı renkler olarak ayarlanan veya artık kullanan denetimler. Daha önce, metin ve arka plan renkleri karşıt değildi ve okunması zor.
- Öğesinin <xref:System.Windows.Forms.GroupBox> özelliği olarak ayarlanmış olan içindeki denetimler <xref:System.Windows.Forms.Control.Enabled> `false` artık yüksek karşıtlık teması içinde işletim sistemi tanımlı renkleri kullanacaktır.
- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> Ve <xref:System.Windows.Forms.ToolStripDropDownButton> denetimleri yüksek karşıtlık modunda daha fazla parlaklık kontrast oranına sahiptir.
- <xref:System.Windows.Forms.DataGridViewLinkCell>Varsayılan olarak, özelliği için Yüksek Karşıtlık modunda işletim sistemi tanımlı renkler kullanır <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> .
NOTE: Windows 10, bazı yüksek karşıtlıklı sistem renklerinin değerlerini değiştirdi. Windows Forms Framework, Win32 çerçevesini temel alır. En iyi deneyim için, Windows 'un en son sürümünde çalıştırın ve bir test uygulamasına bir App. manifest dosyası ekleyerek ve aşağıdaki kodu açıklama atamasını yaparak en son işletim sistemi değişikliklerini kabul edin:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**İyileştirilmiş ekran okuyucusu desteği**

- Ekran okuyucusu artık <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> , ' a ait metin duyurusu yaparken özelliğin değerini duyurur <xref:System.Windows.Forms.ToolStripMenuItem> .
- Ekran okuyucusu artık <xref:System.Windows.Forms.ToolStripMenuItem> öğesinin <xref:System.Windows.Forms.Control.Enabled> özelliği olarak ne zaman ayarlandığını gösterir `false` .
- Artık ekran okuyucusu, özelliği olarak ayarlandığında onay kutusunun durumu hakkında geri bildirim sağlar <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> `true` .
- Ekran okuyucusu tarama modu odak sırası artık ClickOnce indirme iletişim kutusu penceresindeki denetimlerin görsel sırasıyla tutarlıdır.

**Geliştirilmiş DataGridView erişilebilirlik desteği**

- İçindeki satırlar <xref:System.Windows.Forms.DataGridView> artık klavye kullanılarak sıralanabilir. Artık bir Kullanıcı geçerli sütuna göre sıralamak için F3 tuşunu kullanabilir.
- , <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ' A ayarlandığında <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , sütun üst bilgisi, geçerli sütunu geçerli satırdaki hücreler aracılığıyla Kullanıcı sekmeleri olarak göstermek için rengi değiştirir.
- <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType>Özelliği şimdi doğru üst denetimi döndürüyor.

**Geliştirilmiş görsel ipuçları**

- <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Boş bir özelliği olan ve denetimleri <xref:System.Windows.Forms.ButtonBase.Text> artık odak aldıklarında bir odak göstergesi görüntüleyecektir.

**Geliştirilmiş özellik Kılavuzu desteği**

- <xref:System.Windows.Forms.PropertyGrid>Denetim alt öğeleri artık `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> yalnızca bir PropertyGrid öğesi etkinleştirildiğinde özelliği için bir döndürür.
- <xref:System.Windows.Forms.PropertyGrid>Denetim alt öğeleri artık `false` <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> yalnızca bir PropertyGrid öğesi Kullanıcı tarafından değiştirilebiliyorsa özelliği için bir döndürür.
UI Otomasyonu 'na genel bakış için bkz. [UI Otomasyonu genel bakış](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</p>**Geliştirilmiş Klavye gezintisi**

- <xref:System.Windows.Forms.ToolStripButton>Artık, <xref:System.Windows.Forms.ToolStripPanel> özelliği olarak ayarlanmış olan bir içinde yer alan odağa izin verir <xref:System.Windows.Forms.ToolStripPanel.TabStop> `true` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |
