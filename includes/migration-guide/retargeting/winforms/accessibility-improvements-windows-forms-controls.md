---
ms.openlocfilehash: c8e1c91f4fee8aa896b6617c815fe2a4b6d22f2a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614885"
---
### <a name="accessibility-improvements-in-windows-forms-controls"></a>Windows Forms Denetimlerinde erişilebilirlik geliştirmeleri

#### <a name="details"></a>Ayrıntılar

Windows Forms, Windows Forms müşterileri daha iyi desteklemek için erişilebilirlik teknolojileriyle nasıl çalıştığını geliştirmektir. Bunlar, .NET Framework 4.7.1 başlayarak aşağıdaki değişiklikleri içerir:

- Yüksek Karşıtlık modunda görüntülemeyi artırmak için değişiklikler.
- Özellik tarayıcı deneyimini geliştirmek için değişiklikler. Özellik tarayıcısı geliştirmeleri şunları içerir:
- Çeşitli açılan seçim pencereleri aracılığıyla daha iyi klavye gezintisi.
- Gereksiz sekme duraklarının azalması.
- Denetim türlerinin daha iyi raporlaması.
- İyileştirilmiş ekran okuyucusu davranışı.
- Denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.1 veya sonraki bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.1 hedeflemek için yeniden derlenir. Bu erişilebilirlik değişiklikleri, .NET Framework 4.7.1 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilmiştir.
- Aşağıdaki örnekte gösterildiği gibi, aşağıdaki [AppContext anahtarını](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` app.config dosyanın bölümüne ekleyerek ve olarak ayarlayarak eski erişilebilirlik davranışlarından daha fazla bilgi edinin `false` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .<p/>UI Otomasyonu 'na genel bakış için bkz. [UI Otomasyonu genel bakış](~/docs/framework/ui-automation/ui-automation-overview.md).<p/>**UI Otomasyonu desenleri ve özellikleri için destek eklendi**<br/>Erişilebilirlik istemcileri, yaygın, genel olarak açıklanan çağrı düzenlerini kullanarak yeni WinForms erişilebilirlik işlevlerinden faydalanabilir. Bu desenler, WinForms 'e özgü değildir. Örneğin, erişilebilirlik istemcileri bir IServiceProvider arabirimi almak için ıerişimli Arabirim (MAAS) üzerinde QueryInterface metodunu çağırabilir. Bu arabirim kullanılabiliyorsa, istemciler bir ıerişilebilirlik arabirimi istemek için QueryService metodunu kullanabilir. Daha fazla bilgi için, bkz. [bir Istemciden Ierişilebilir Bleex kullanma](https://docs.microsoft.com/windows/desktop/WinAuto/using-iaccessibleex-from-a-client). .NET Framework 4.7.1, IServiceProvider ve [ıeriþbleex](https://docs.microsoft.com/windows/desktop/WinAuto/iaccessibleex) (uygun olduğunda), WinForms erişilebilirlik nesneleri için kullanılabilir.<p/>.NET Framework 4.7.1, aşağıdaki UI Otomasyon desenleri ve özellikleri için destek ekler:

- <xref:System.Windows.Forms.ToolStripSplitButton>Ve <xref:System.Windows.Forms.ComboBox> denetimleri [Genişlet/Daralt modelini](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.
- <xref:System.Windows.Forms.ToolStripMenuItem>Denetimde bir [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) Özellik değeri vardır <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.ToolStripItem>Denetim, <xref:System.Windows.Automation.AutomationElement.NameProperty> özelliği ve[Genişlet/Daralt düzenlerini](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.
- <xref:System.Windows.Forms.ToolStripDropDownItem>Denetim, <xref:System.Windows.Forms.AccessibleEvents> açılan kutudan genişletildiği veya daraltılması durumunda StateChange ve NameChange 'in kullanılmasını destekler.
- <xref:System.Windows.Forms.ToolStripDropDownButton>Denetimde bir [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) özelliği değeri vardır <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>Denetim öğesini destekler <xref:System.Windows.Automation.TogglePattern> .
- <xref:System.Windows.Forms.NumericUpDown>Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri <xref:System.Windows.Automation.AutomationElement.NameProperty> özelliği destekler ve bir için bir [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md) vardır <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType> .</p>
**PropertyGrid denetimine yönelik iyileştirmeler** .NET Framework 4.7.1, PropertyBrowser denetimine aşağıdaki geliştirmeleri ekler:

- Kullanıcı denetimde yanlış bir değer girdiğinde görüntülenen hata iletişim **kutusu,** <xref:System.Windows.Forms.PropertyGrid> [genişletme/daraltma modelini](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md), durum ve ad değişikliği bildirimlerini ve değeri olan bir [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) özelliğini destekler <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- Hata iletişim kutusunun **Ayrıntılar** düğmesi genişletildiğinde görüntülenecek ileti bölmesi artık klavyeden erişilebilir olur ve Ekran okuyucusunun hata iletisinin içeriğini duyurduğunu sağlar.
- <xref:System.Windows.Forms.AccessibleRole> <xref:System.Windows.Forms.PropertyGrid> Denetimdeki satırların &quot; satır &quot; olarak &quot; hücreden hücreye değişmesi &quot; . Hücre &quot; &quot; , uygun klavye kısayollarını ve ekran okuyucusu bildirilerini desteklemeye izin veren Uia ControlType DataItem ile eşlenir.
- <xref:System.Windows.Forms.PropertyGrid> <xref:System.Windows.Forms.PropertyGrid> Denetimin bir <xref:System.Windows.Forms.PropertyGrid.PropertySort> özelliği bir <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) özelliği değerine sahip olacak şekilde ayarlanmış olduğunda Başlık öğelerini temsil eden denetim satırları <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.PropertyGrid> <xref:System.Windows.Forms.PropertyGrid> Denetimin <xref:System.Windows.Forms.PropertyGrid.PropertySort> <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> [genişletme/daraltma düzenlerini](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)desteklemek üzere ayarlanmış bir özelliği olduğunda Başlık öğelerini temsil eden denetim satırları.
- Kılavuz ve üzerindeki araç çubuğu arasında geliştirilmiş klavye gezintisi. &quot;Artık SHIFT-TAB tuşlarına basıldığında &quot; araç çubuğunun tamamı yerine Ilk araç çubuğu düğmesi seçilir.
- <xref:System.Windows.Forms.PropertyGrid>Yüksek Karşıtlık modunda gösterilecek denetimler artık, geçerli özellik değerine karşılık gelen araç çubuğu düğmesi etrafında bir odak dikdörtgeni çizer <xref:System.Windows.Forms.PropertyGrid.PropertySort> .
- <xref:System.Windows.Forms.PropertyGrid>Yüksek Karşıtlık modunda görüntülenen ve bir <xref:System.Windows.Forms.PropertyGrid.PropertySort> özelliği olarak ayarlanmış olan denetimler <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> artık kategori başlıklarının arka planını çok daha fazla bir renkte görüntüleyecek.
- <xref:System.Windows.Forms.PropertyGrid>denetimler, odak içeren araç çubuğu öğeleri ve özelliğin geçerli değerini gösteren araç çubuğu öğeleri arasında daha iyi ayrım yapar <xref:System.Windows.Forms.PropertyGrid.PropertySort> . Bu düzeltilme Yüksek Karşıtlık değişiklik ve Yüksek Karşıtlık olmayan senaryolara yönelik bir değişiklikten oluşur.
- <xref:System.Windows.Forms.PropertyGrid>özelliğin geçerli değerini desteklediğini belirten denetim çubuğu öğeleri <xref:System.Windows.Forms.PropertyGrid.PropertySort> <xref:System.Windows.Automation.TogglePattern> .
- Hizalama seçicideki seçili hizalamayı ayırt etmek için iyileştirilmiş ekran okuyucusu desteği.
- <xref:System.Windows.Forms.PropertyGrid>Form üzerinde boş bir denetim görüntülendiğinde, artık daha önce olmadığı yerde odak alınır.

**Yüksek Karşıtlık Temaları 'nda işletim sistemi tanımlı renklerin kullanımı**

- <xref:System.Windows.Forms.Button>Ve özellikleri, varsayılan stil olan ' a <xref:System.Windows.Forms.CheckBox> ayarlanmış olan ve denetimleri, <xref:System.Windows.Forms.ButtonBase.FlatStyle> <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> artık seçildiğinde yüksek karşıtlık teması içinde işletim sistemi tanımlı renkler kullanır. Daha önce, metin ve arka plan renkleri karşıt değildi ve okunması zor.
- <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.LinkLabel> <xref:System.Windows.Forms.GroupBox> Özelliği false olarak ayarlanmış olan,,,, ve denetimleri, <xref:System.Windows.Forms.Control.Enabled> yüksek karşıtlık **false** temalarında metin işlemek için gölgeli bir renk kullandı ve bu da arka planda düşük karşıtlığa neden olur. Bu denetimler artık &quot; &quot; işletim sistemi tarafından tanımlanan devre dışı metin rengini kullanır. Bu çözüm, `FlatStyle` özelliği dışında bir değere ayarlanmış denetimler için geçerlidir <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> . İkinci denetimler işletim sistemi tarafından işlenir.
- <xref:System.Windows.Forms.DataGridView>Şimdi, geçerli odağa sahip olan hücrenin içeriğinin etrafında görünür bir dikdörtgen oluşturur. Daha önce bu, bazı Yüksek Karşıtlık temalarda görünmez.
- <xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.ToolStripMenuItem.Enabled>özelliği **false** olarak ayarlanmış olan denetimler artık &quot; &quot; işletim sistemi tarafından tanımlanan devre dışı metin rengini kullanır.
- <xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.ToolStripMenuItem.Checked>özelliği **true** olarak ayarlanan denetimler artık, ilişkili onay işaretini bir karşıt sistem renginde işleyebilir.  Daha önce onay işaretinin rengi yeterince fazla değildi ve Yüksek Karşıtlık temalarda görünmez.
NOTE: Windows 10, bazı yüksek karşıtlıklı sistem renklerinin değerlerini değiştirdi. Windows Forms Framework, Win32 çerçevesini temel alır. En iyi deneyim için, Windows 'un en son sürümünde çalıştırın ve bir test uygulamasına bir App. manifest dosyası ekleyerek ve aşağıdaki kodu açıklama atamasını yaparak en son işletim sistemi değişikliklerini kabul edin:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Geliştirilmiş Klavye gezintisi**

- Bir <xref:System.Windows.Forms.ComboBox> denetimin <xref:System.Windows.Forms.ComboBox.DropDownStyle> özelliği olarak ayarlandığında <xref:System.Windows.Forms.ComboBoxStyle.DropDownList?displayProperty=nameWithType> ve formdaki sekme düzeninde ilk denetim olduğunda, artık üst form klavye kullanılarak açıldığında bir odak dikdörtgeni görüntülenir. Bu değişiklikten önce klavye odağı bu denetimde vardı, ancak odak göstergesi işlenmedi.

**İyileştirilmiş ekran okuyucusu desteği**

- <xref:System.Windows.Forms.MonthCalendar>Denetim, daha önce başarısız olduğunda ekran okuyucuyu denetim değerini okuma özelliği de dahil olmak üzere denetime erişmek için yardımcı teknolojiler desteği eklemiştir.

- <xref:System.Windows.Forms.CheckedListBox>Denetim artık bir özellik değiştirildiğinde ekran okuyucuyu bilgilendirir <xref:System.Windows.Forms.CheckBox.CheckState?displayProperty=nameWithType> . Daha önce, ekran okuyucusu bildirim almadı ve bir sonuç olarak, kullanıcıların <xref:System.Windows.Forms.CheckBox.CheckState> özelliğin güncelleştirildiğini bilgilendirmez.
- <xref:System.Windows.Forms.LinkLabel>Denetim, denetim okuyucuyu denetimde bildiren metnin bulunduğu şekilde değiştirdi. Daha önce, ekran okuyucusu bu metni iki kez duyuruyor ve &quot; &amp; &quot; bir kullanıcıya görünmese de sembolleri gerçek metin olarak okudu. Yinelenen metin, ekran okuyucusu duyurularından ve gereksiz &quot; &amp; &quot; simgelerle kaldırılmıştır.
- <xref:System.Windows.Forms.DataGridViewCell>Denetim türleri artık salt okuma durumunu ekran okuyucuya ve diğer yardımcı teknolojilere doğru şekilde bildirir.
- Ekran okuyucusu artık [çok belgeli arabirim] ~/doc/Framework/WinForms/Advanced/Multiple-Document-Interface-MDI-Applications.MD) uygulamalarında alt pencerelerin sistem menüsünü okuyabiliyor.
- Ekran okuyucusu artık <xref:System.Windows.Forms.ToolStripMenuItem> bir <xref:System.Windows.Forms.ToolStripItem.Enabled?displayProperty=nameWithType> özelliği **yanlış**olarak ayarlanmış denetimleri okuyabilir. Daha önce, ekran okuyucusu içeriği okumak için devre dışı menü öğelerine odaklanmadı.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType>
- [MonthCalendar. AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)
