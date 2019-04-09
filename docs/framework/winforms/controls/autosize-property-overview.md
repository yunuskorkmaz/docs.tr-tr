---
title: AutoSize Özelliğine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: 6d5c4a22f186ddc5811c4a4d5e79776decea9e50
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173634"
---
# <a name="autosize-property-overview"></a>AutoSize Özelliğine Genel Bakış
<xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği tarafından belirtilen değeri elde etmek gerekirse kendi boyutunu değiştirmek bir denetim sağlar <xref:System.Windows.Forms.Control.PreferredSize%2A> özelliği. Belirli denetimler için boyutlandırma davranışını belirleyerek ayarlama `AutoSizeMode` özelliği.  
  
## <a name="autosize-behavior"></a>AutoSize davranışı  
 Yalnızca bazı denetimler Destek <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği. Ayrıca, bazı denetimler destekleyen <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği de destek `AutoSizeMode` özelliği.  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği belirli denetim türü ve değerine bağlı olarak biraz farklı bir davranış üretir `AutoSizeMode` özelliği varsa, özelliği. Aşağıdaki tabloda, her zaman doğru davranışları açıklar ve her kısa bir açıklaması verilmiştir:  
  
|Her zaman doğru davranışı|Açıklama|  
|--------------------------|-----------------|  
|Otomatik boyutlandırma, bir çalışma zamanı özelliğidir.|Bu, hiçbir zaman büyüdükçe veya bir denetim daraltır ve ardından başka bir etkisi yoktur anlamına gelir.|  
|Bir denetim boyut değerini değiştiğinde kendi <xref:System.Windows.Forms.Control.Location%2A> özelliği her zaman sabittir.|Bir denetimin içeriği büyümesine neden olduğunda, denetimin aşağı ve sağa doğru genişler. Denetimleri sola büyütün değil.|  
|<xref:System.Windows.Forms.Control.Dock%2A> Ve <xref:System.Windows.Forms.Control.Anchor%2A> özellikleri ne zaman ödenmiş olan <xref:System.Windows.Forms.Control.AutoSize%2A> olduğu `true`.|Denetimin değerini <xref:System.Windows.Forms.Control.Location%2A> özelliği doğru değerine ayarlandı.<br /><br /> **Not** <xref:System.Windows.Forms.Label> bu kuralın istisnası denetimidir. Bir yerleşik değeri ayarladığınızda <xref:System.Windows.Forms.Label> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`, <xref:System.Windows.Forms.Label> denetimi uzamaz.|  
|Bir denetimin <xref:System.Windows.Forms.Control.MaximumSize%2A> ve <xref:System.Windows.Forms.Control.MinimumSize%2A> özellikleri her zaman dikkate alınır, değerine bakılmaksızın kendi <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.|<xref:System.Windows.Forms.Control.MaximumSize%2A> Ve <xref:System.Windows.Forms.Control.MinimumSize%2A> özellikleri tarafından etkilenmez <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.|  
|Varsayılan olarak en küçük boyut yok.|Bir denetimi altında daraltmak üzere ayarlanmışsa Bunun anlamı <xref:System.Windows.Forms.Control.AutoSize%2A> ve hiç içerik değeri olan kendi <xref:System.Windows.Forms.Control.Size%2A> 0,0 özelliğidir. Bu durumda, denetim bir noktaya kadar daraltılır ve kolayca görünür olmaz.|  
|Bir denetim uygulamazsa <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi atanan son değeri döndürür <xref:System.Windows.Forms.Control.Size%2A> özelliği.|Bu ayar başka bir deyişle <xref:System.Windows.Forms.Control.AutoSize%2A> için `true` hiçbir etkisi olmaz.|  
|Bir denetimde bir <xref:System.Windows.Forms.TableLayoutPanel> hücre her zaman kadar hücresine sığacak şekilde küçülür kendi <xref:System.Windows.Forms.Control.MinimumSize%2A> ulaşıldı.|Bu boyut sınırını uygulanır. Hücre parçası olduğunda bu durum değil bir <xref:System.Windows.Forms.SizeType.AutoSize> satır veya sütun.|  
  
## <a name="autosizemode-property"></a>AutoSizeMode özelliği  
 `AutoSizeMode` Özelliği varsayılan üzerinde daha ayrıntılı denetim sağlar <xref:System.Windows.Forms.Control.AutoSize%2A> davranışı. `AutoSizeMode` Özelliği, nasıl bir denetim kendisine içeriğine boyutları belirtir. İçeriği, örneğin, metni olabilir bir <xref:System.Windows.Forms.Button> denetim veya kapsayıcı için alt denetimler.  
  
 Aşağıdaki tabloda <xref:System.Windows.Forms.AutoSizeMode> ayarları ve davranışının bir açıklaması için her ayarın verilmesini sağlar.  
  
|AutoSizeMode ayarı|Davranış|  
|--------------------------|--------------|  
|GrowAndShrink|Denetim büyüyor veya içeriğini kapsayacak şekilde küçültür.<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> Ve <xref:System.Windows.Forms.Control.MaximumSize%2A> değerler kabul edilir, geçerli değeri <xref:System.Windows.Forms.Control.Size%2A> özelliği yok sayılır.<br /><br /> Denetimler ile aynı davranışı budur <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve Hayır `AutoSizeMode` özelliği.|  
|GrowOnly|Denetimin içeriğini kapsayacak şekilde gerektiği kadar büyür, ancak bu tarafından belirtilen değerden daha küçük küçültme olmayacağı kendi <xref:System.Windows.Forms.Control.Size%2A> özelliği.<br /><br /> İçin varsayılan değer budur `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>AutoSize özelliği destekleyen denetimleri  
 Aşağıdaki tabloda destekleyen denetimleri listeler <xref:System.Windows.Forms.Control.AutoSize%2A> ve `AutoSizeMode` özellikleri.  
  
|AutoSize desteği|Denetim türü|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> desteklenen özellik.<br />-Hiçbir `AutoSizeMode` özelliği.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> temel)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> desteklenen özellik.<br />-   `AutoSizeMode` desteklenen özellik.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-Hiçbir <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>Tasarım ortamında Otomatik Boyutlandır  
 Aşağıdaki tablo, değerini temel alarak tasarım zamanında denetiminin boyutlandırma davranışını açıklar, <xref:System.Windows.Forms.Control.AutoSize%2A> ve `AutoSizeMode` özellikleri.  
  
 Geçersiz kılma <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> özelliği belirli bir denetim kullanıcı yeniden boyutlandırılabilir bir durumda olup olmadığını belirlemek için. Aşağıdaki tabloda, "anlamına gelir olamaz" <xref:System.Windows.Forms.Design.SelectionRules.Moveable> yalnızca anlamına gelir "için" <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> ve <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|AutoSize ayarları|Tasarım zamanı boyutlandırma hareket|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-Hiçbir `AutoSizeMode` özelliği.|Kullanıcı denetimi aşağıdaki denetimleri dışında tasarım zamanında yeniden boyutlandıramazsınız:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|Kullanıcı denetiminin tasarım zamanında yeniden boyutlandıramazsınız.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|Kullanıcı denetiminin tasarım zamanında yeniden boyutlandırabilirsiniz. Zaman <xref:System.Windows.Forms.Control.Size%2A> özelliği ayarlandığında, kullanıcının yalnızca denetiminin boyutunu artırabilirsiniz.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, veya <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği gizlenir.|Kullanıcı denetiminin tasarım zamanında yeniden boyutlandırabilirsiniz.|  
  
> [!NOTE]
>  Üretkenlik, Windows Form Tasarımcısı'shadows ' en üst düzeye çıkarmak <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği <xref:System.Windows.Forms.Form> sınıfı. Tasarım zamanında, gibi ancak form davranışını <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği `false`gerçek ayarına bakılmaksızın. Hiçbir özel Konaklama çalışma zamanında yapılmış ve <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği uygulanan özellik ayarı tarafından belirtildiği gibi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.PreferredSize%2A>
- <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
