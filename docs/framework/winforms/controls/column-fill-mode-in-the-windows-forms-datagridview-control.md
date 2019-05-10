---
title: Windows Forms DataGridView Denetiminde Sütun Doldurma Modu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 344f9856c1f3b1483bfda6f36a7e025ff2e5c78d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593435"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Doldurma Modu
Sütun doldurma modu içinde <xref:System.Windows.Forms.DataGridView> denetimi, böylece bunlar kullanılabilir görüntüleme alanının genişliğini dolgu sütunlarını otomatik olarak yeniden boyutlandırır. Denetimi dışında her bir sütunun genişliğini eşit tutmak gerekli veya daha büyük olduğunda yatay kaydırma çubuğunun görüntülemez, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özellik değeri.  
  
 Her bir sütunun boyutlandırma davranışını bağlıdır, <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliği. Bu özelliğin değeri, sütunun devralınan <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliği veya denetimin <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> sütun değeri ise özellik <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (varsayılan değer).  
  
 Her sütun bir başka bir boyutu modu, ancak hiçbir sütun boyutu modu olabilir <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> diğer sütunlara göre kullanılmaz görüntüleme alanı genişliğini paylaşır. Bu genişlik arasındaki göreli oranları dolgu modunu sütunları bölünmüştür bunların <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri. Örneğin, iki sütun varsa <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100 ve 200 değerlerini, ilk sütun olacaktır yarısı olarak ikinci sütun olarak geniş.  
  
## <a name="user-resizing-in-fill-mode"></a>Kullanıcı dolgu modunda yeniden boyutlandırma  
 Hücre içeriklerini temel alarak yeniden boyutlandırma modları boyutlandırma aksine doldurma modu kullanıcıların olan sütunları yeniden boyutlandırmasını engellemez <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özellik değerlerini `true`. Bir kullanıcı, sonra yeniden boyutlandırılan sütun doldurma modu sütun doldurma modu sütun ne zaman yeniden boyutlandırır (doğru halinde <xref:System.Windows.Forms.Control.RightToLeft%2A> olduğu `false`; Aksi takdirde sola) de kullanılabilir genişliğini değişikliği dengelemek için yeniden boyutlandırılır. Sonra yeniden boyutlandırılan sütun doldurma modu sütun varsa, diğer tüm dolgu modunu sütunlar denetiminde dengelemek için boyutlandırılır. Denetimde hiç bir dolgu modunu sütun varsa, yeniden boyutlandırma göz ardı edilir. Dolgu modunda değil bir sütun boyutlandırılırsa, denetimdeki tüm dolgu modunu sütunları dengelemek için boyutları değiştirin.  
  
 Sütun doldurma modu yeniden boyutlandırma sonra <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerleri değiştirilmiş tüm sütunları orantılı olarak ayarlanır. Örneğin, dört dolgu modunu sütun varsa <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> yarı özgün genişliği ikinci sütunda yeniden boyutlandırma, 100 değerini neden olur <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100 ve 50, 125 ve 125 değerleri. Dolgu modunda değil bir sütunu yeniden boyutlandırma değişmeyecek herhangi <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> dolgu modunu sütunları yalnızca aynı oranını korurken dengelemek için boyutlandırma için değerler.  
  
## <a name="content-based-fillweight-adjustment"></a>İçerik tabanlı FillWeight ayarlama  
 Başlatmak <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kullanarak sütun doldurma modu değerleri <xref:System.Windows.Forms.DataGridView> otomatik yöntemleri gibi yeniden boyutlandırma <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> yöntemi. Bu yöntem ilk sütuna göre içeriklerini görüntülemek için gerekli genişlikleri hesaplar. Ardından, denetimin ayarlar <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> böylece kendi oranlarını hesaplanan sütunların oranlarını eşleşen tüm dolgu modunu sütunlar için değer. Son olarak, denetimi kullanarak yeni bir dolgu modunu sütunları yeniden boyutlandırır <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kullanılabilir yatay boşluğu denetimdeki tüm sütunları doldurun, böylece oranları.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 İçin uygun değerleri kullanarak <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, ve <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özellikleri, birçok farklı senaryo için sütun boyutlandırma davranışları özelleştirebilirsiniz.  
  
 Aşağıdaki tanıtım kod için farklı değerlerle denemenizi etkinleştirir <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, ve <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özellikleri farklı sütun. Bu örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimin bağlı kendi <xref:System.Windows.Forms.DataGridView.Columns%2A> toplama ve bir sütuna bağlı her biri <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özellikleri. Her sütun da bir satır denetimi tarafından temsil edilen ve satır değerleri değiştirme değerleri nasıl etkileşim görebilmeniz için karşılık gelen sütun özelliklerini güncelleştirir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Açıklamalar  
 Bu Tanıtım uygulamasını kullanmak için:  
  
- Formun boyutunu değiştirin. Oranlarını koruma tarafından gösterilen sırada sütun genişliklerini nasıl değiştiğini gözlemlersiniz <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri.  
  
- Fare ile sütun ayırıcılarını sürükleyerek sütunu boyutları değiştirin. Gözlemleyin nasıl <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerleri değiştiğinde.  
  
- Değişiklik <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değer için bir sütun ve formu yeniden boyutlandırmak için sürükleyin. Gözlemleyin nasıl formun yeterince, küçük yaptığınızda <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> değerlerin değil aşağıda Git <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerleri.  
  
- Değişiklik <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerleri büyük sayılar tüm sütunları ve böylece birleşik değerleri denetiminin genişliğini aşıyor. Yatay kaydırma çubuğunun nasıl göründüğünü gözlemleyin.  
  
- Değişiklik <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> bazı sütunları için değerler. Sütunları veya formunu yeniden boyutlandırdığınızda etkisi gözlemleyin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
- Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
