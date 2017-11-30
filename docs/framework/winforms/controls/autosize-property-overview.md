---
title: "AutoSize Özelliğine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8216880ebdede03bbd01fe53b622c14ca8c514d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="autosize-property-overview"></a>AutoSize Özelliğine Genel Bakış
<xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği tarafından belirtilen değeri elde etmek gerekirse, boyutunu değiştirmek bir denetim sağlar <xref:System.Windows.Forms.Control.PreferredSize%2A> özelliği. Belirleyerek belirli denetimleri boyutlandırma davranışını ayarlama `AutoSizeMode` özelliği.  
  
## <a name="autosize-behavior"></a>AutoSize davranışı  
 Yalnızca bazı denetimler Destek <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği. Ayrıca, bazı denetimler destekleyen <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği de destek `AutoSizeMode` özelliği.  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği üreten belirli denetim türü ve değerine bağlı olarak biraz farklı bir davranış `AutoSizeMode` özellik varsa, özelliği. Aşağıdaki tabloda, her zaman true davranışları açıklar ve her kısa bir açıklaması verilmiştir:  
  
|Her zaman true davranışı|Açıklama|  
|--------------------------|-----------------|  
|Otomatik boyutlandırma bir çalışma zamanı özelliğidir.|Bu, hiçbir zaman büyüdükçe veya denetim küçültür ve ardından başka hiçbir etkisi olmaz anlamına gelir.|  
|Bir denetim boyutu, değeri değişirse, <xref:System.Windows.Forms.Control.Location%2A> özelliği her zaman sabittir.|Bir denetimin içeriği büyümesine neden olduğunda denetimi aşağı ve sağa doğru artar. Denetimleri sola büyümesine değil.|  
|<xref:System.Windows.Forms.Control.Dock%2A> Ve <xref:System.Windows.Forms.Control.Anchor%2A> özellikleri ne zaman kabul olan <xref:System.Windows.Forms.Control.AutoSize%2A> olan `true`.|Denetimin değerini <xref:System.Windows.Forms.Control.Location%2A> özelliği doğru değerine ayarlanmış.<br /><br /> **Not** <xref:System.Windows.Forms.Label> bu kural için özel bir denetimdir. Bir yerleşik değeri ayarlandığında <xref:System.Windows.Forms.Label> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`, <xref:System.Windows.Forms.Label> denetimi uzamaz.|  
|Bir denetimin <xref:System.Windows.Forms.Control.MaximumSize%2A> ve <xref:System.Windows.Forms.Control.MinimumSize%2A> özellikleri her zaman korunur, değeri bağımsız olarak kendi <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.|<xref:System.Windows.Forms.Control.MaximumSize%2A> Ve <xref:System.Windows.Forms.Control.MinimumSize%2A> özellikleri etkilenmez <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.|  
|Varsayılan olarak ayarlanan en düşük boyut yoktur.|Altında daraltmak için bir denetim ayarlarsanız buna <xref:System.Windows.Forms.Control.AutoSize%2A> ve hiç içerik değerini sahip kendi <xref:System.Windows.Forms.Control.Size%2A> 0,0 bir özelliktir. Bu durumda, denetiminiz bir noktasına küçülür ve kolaylıkla görünür olmaz.|  
|Bir denetim uygulamazsa <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi, <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi atanan son değeri döndürür <xref:System.Windows.Forms.Control.Size%2A> özelliği.|Bu ayar yani <xref:System.Windows.Forms.Control.AutoSize%2A> için `true` hiçbir etkisi olmaz.|  
|Bir denetimde bir <xref:System.Windows.Forms.TableLayoutPanel> hücre her zaman kadar hücresindeki sığacak şekilde küçültür kendi <xref:System.Windows.Forms.Control.MinimumSize%2A> ulaşıldı.|Bu boyut sınırını uygulanır. Hücrenin parçası olduğunda bu şekilde değilse bir <xref:System.Windows.Forms.SizeType.AutoSize> satır veya sütun.|  
  
## <a name="autosizemode-property"></a>AutoSizeMode özelliği  
 `AutoSizeMode` Özelliği, varsayılan üzerinde daha ayrıntılı denetim sağlar <xref:System.Windows.Forms.Control.AutoSize%2A> davranışı. `AutoSizeMode` Özelliği, nasıl bir denetim kendisini içeriğine boyutları belirtir. İçerik, örneğin, metnini olabilir bir <xref:System.Windows.Forms.Button> denetim veya alt denetimleri için bir kapsayıcı.  
  
 Aşağıdaki tabloda <xref:System.Windows.Forms.AutoSizeMode> ayarları ve davranışı açıklamasını her ayar verilmesini sağlar.  
  
|AutoSizeMode ayarı|Davranış|  
|--------------------------|--------------|  
|GrowAndShrink|Denetim büyüdüğünde veya küçüldüğünde içeriğinin kapsayacak şekilde.<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> Ve <xref:System.Windows.Forms.Control.MaximumSize%2A> değerlerini dikkate alınır, geçerli değeri <xref:System.Windows.Forms.Control.Size%2A> özelliği yoksayılır.<br /><br /> Denetimler ile aynı davranışı budur <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve Hayır `AutoSizeMode` özelliği.|  
|GrowOnly|Denetim içeriğinin kapsayacak şekilde gerektiği kadar büyür, ancak bunu tarafından belirtilen değerden daha küçük küçültme olmayacağı kendi <xref:System.Windows.Forms.Control.Size%2A> özelliği.<br /><br /> İçin varsayılan değer budur `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>AutoSize özelliği destekleyen denetimleri  
 Destekleyen denetimleri aşağıdaki tabloda listelenmektedir <xref:System.Windows.Forms.Control.AutoSize%2A> ve `AutoSizeMode` özellikleri.  
  
|AutoSize desteği|Denetim türü|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A>desteklenen özelliği.<br />-Hiçbir `AutoSizeMode` özelliği.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox>(<xref:System.Windows.Forms.TextBox> temel)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A>desteklenen özelliği.<br />-   `AutoSizeMode`desteklenen özelliği.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-Hiçbir <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>Tasarım ortamında AutoSize  
 Aşağıdaki tabloda, değerine göre tasarım zamanında denetimi boyutlandırma davranışını tanımlar, <xref:System.Windows.Forms.Control.AutoSize%2A> ve `AutoSizeMode` özellikleri.  
  
 Geçersiz kılma <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> belirli bir denetim kullanıcı yeniden boyutlandırılabilir bir durumda olup olmadığını belirlemek için özellik. Aşağıdaki tabloda, "anlamına gelir olamaz" <xref:System.Windows.Forms.Design.SelectionRules.Moveable> yalnızca "anlamına gelir olabilir" <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> ve <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|AutoSize ayarları|Tasarım zamanı boyutlandırma hareketi|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-Hiçbir `AutoSizeMode` özelliği.|Kullanıcı denetimi aşağıdaki denetimleri dışında tasarım zamanında boyutlandırılamıyor:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|Kullanıcı denetimi tasarım zamanında boyutlandırılamaz.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|Kullanıcı denetimi tasarım zamanında genişletebilir. Zaman <xref:System.Windows.Forms.Control.Size%2A> özelliği ayarlanmışsa, kullanıcı yalnızca denetimi boyutunu artırabilirsiniz.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, veya <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği gizlenir.|Kullanıcı denetimi tasarım zamanında genişletebilir.|  
  
> [!NOTE]
>  Windows Form Tasarımcısı gölgeleri üretkenliği en üst düzeye çıkarmak için <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği için <xref:System.Windows.Forms.Form> sınıfı. Tasarım zamanında form olarak ancak davranır <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ayarlanmış `false`ne olursa olsun, gerçek ayarı. Hiçbir özel Konaklama çalışma zamanında yapılmış ve <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği uygulanır özellik ayarı tarafından belirtildiği gibi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.PreferredSize%2A>  
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
