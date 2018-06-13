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
ms.openlocfilehash: 372ee5b0eb0101a13e7eb458ee8a8bcc06d3baff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528850"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Doldurma Modu
Sütun doldurma modu içinde <xref:System.Windows.Forms.DataGridView> denetim, böylece bunlar kullanılabilir ekran alanının genişliğini kaplayacak sütunlarını otomatik olarak yeniden boyutlandırır. Her sütunun genişliği eşit tutmak gerekli veya daha büyük olduğu durumların dışında yatay kaydırma çubuğu denetimi görüntülemez kendi <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özellik değeri.  
  
 Her sütun boyutlandırma davranışını bağlıdır, <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliği. Bu özelliğin değeri sütunun devralınan <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliği veya denetimin <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> sütun değeri ise özelliği <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (varsayılan değer).  
  
 Her sütun boyutu modu ile herhangi bir sütundan ancak bir boyutu farklı modu olabilir <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> diğer sütunlara göre kullanılmaz görüntü alanının genişliğini paylaşır. Bu genişliği göreli oranları doldurma modu sütunları arasında bölünür kendi <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri. Örneğin, iki sütun varsa <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100 ve 200 değerlerini, ilk sütun olacaktır yarısı kadar geniş ikinci sütun olarak.  
  
## <a name="user-resizing-in-fill-mode"></a>Kullanıcı dolgu modunda yeniden boyutlandırma  
 Boyutlandırma hücre içeriğine göre yeniden boyutlandırma modlarını aksine doldurma modu kullanıcıların sahip sütunları yeniden boyutlandırma engellemez <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özellik değerlerini `true`. Bir kullanıcı bir doldurma modu sütun doldurma modu sütunlar yeniden boyutlandırılan sütun sonra ne zaman yeniden boyutlandırır (sağ yoksa <xref:System.Windows.Forms.Control.RightToLeft%2A> olan `false`; tersi durumda, sol) de kullanılabilir genişliği değişikliği dengelemek için yeniden boyutlandırılır. Sonra yeniden boyutlandırılan sütun doldurma modu sütun varsa, tüm diğer doldurma modu sütunlardaki denetimi dengelemek için boyutlandırılır. Denetimde hiç bir doldurma modu sütun varsa, yeniden boyutlandırma göz ardı edilir. Dolgu modunda değil bir sütunu yeniden boyutlandırılabilir varsa, tüm doldurma modu sütunları denetiminde dengelemek için boyutları değiştirin.  
  
 Doldurma modu sütun bir yeniden boyutlandırmadan sonra <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerleri değiştirilen tüm sütunları orantılı olarak ayarlanır. Örneğin, dört doldurma modu sütun varsa <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> yarım orijinal genişliğiyle ikinci sütun yeniden boyutlandırma 100 değerini neden olur <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100, 50, 125 ve 125 değerleri. Dolgu modunda değil bir sütunu yeniden boyutlandırma değiştirmez herhangi <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> doldurma modu sütunları yalnızca aynı oranlarını koruyarak dengelemek için boyutlandırılır çünkü değerleri.  
  
## <a name="content-based-fillweight-adjustment"></a>İçerik tabanlı FillWeight ayarlama  
 Başlatmak <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kullanarak doldurma modu sütunların değerlerini <xref:System.Windows.Forms.DataGridView> otomatik yöntemleri, aşağıdaki gibi yeniden boyutlandırma <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> yöntemi. Bu yöntem ilk sütunlara göre içeriklerini görüntülemek için gereken genişlikleri hesaplar. Ardından, Denetim ayarlar <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kendi oranları hesaplanan genişlikleri oranlarını eşleşmesi için tüm doldurma modu sütunları değerleri. Son olarak, denetimi kullanarak yeni doldurma modu sütunları yeniden boyutlandırır <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> denetimdeki tüm sütunları kullanılabilir yatay alanı dolduracak böylece oranları.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 İçin uygun değerleri kullanarak <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, ve <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özellikleri, birçok farklı senaryolar için sütun boyutlandırma davranışları özelleştirebilirsiniz.  
  
 Aşağıdaki gösterim kodu için farklı değerler deneme sağlar <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, ve <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> farklı sütun özelliklerini. Bu örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimin bağlı kendi <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu ve bir sütuna bağlı her biri için <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özellikleri. Sütunların her biri de bir satır denetiminde tarafından temsil edilen ve değerlerin nasıl etkileşim görebilmeniz için bir satır değerleri değiştirme karşılık gelen sütunun özelliklerini güncelleştirmek.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Açıklamalar  
 Bu Demo uygulamayı kullanmak için:  
  
-   Formun boyutunu değiştirin. Oranları koruma tarafından gösterilen sırada sütun genişliklerini nasıl değiştiğini gözlemleyin <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri.  
  
-   Sütun boyutlarını fareyle sütun Bölücü sürükleyerek değiştirebilirsiniz. Gözlemlemek nasıl <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerlerini değiştirin.  
  
-   Değişiklik <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değer için bir sütun ve formu yeniden boyutlandırmak için sürükleyin. Gözlemlemek nasıl, formun yeteri kadar küçük yaptığınızda <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> değerleri değil altına gidin <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerleri.  
  
-   Değişiklik <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerleri büyük sayılar için tüm sütunlar için böylece birleştirilmiş değerleri denetiminin genişliğini aşıyor. Yatay kaydırma çubuğu görünme gözlemleyin.  
  
-   Değişiklik <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> bazı sütunlar için değerleri. Sütun veya formu yeniden boyutlandırdığınızda etkisi gözlemleyin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
-   Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
