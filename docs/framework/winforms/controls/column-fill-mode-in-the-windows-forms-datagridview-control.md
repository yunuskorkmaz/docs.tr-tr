---
title: DataGridView denetiminde sütun dolgusu modu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 43b8915efe303b6f56cd4adf5fdbd69f51b0b754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736881"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Doldurma Modu
Sütun dolgusu modunda, <xref:System.Windows.Forms.DataGridView> denetimi sütunları otomatik olarak yeniden boyutlandırır, böylece kullanılabilir görüntü alanının genişliği doldurulur. Denetim, her sütunun genişliğini <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özellik değerine eşit veya ondan büyük tutmak için gerekli olduğu durumlar dışında yatay kaydırma çubuğunu görüntülemez.  
  
 Her sütunun boyutlandırma davranışı <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliğine bağlıdır. Bu özelliğin değeri sütunun <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğinden veya sütunun değeri <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (varsayılan değer) olduğunda denetimin <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğinden devralınır.  
  
 Her sütun farklı bir boyut moduna sahip olabilir, ancak <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> boyut modu olan sütunlar, diğer sütunlarda kullanılmayan görüntü alanı genişliğini paylaşır. Bu genişlik, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerlerine göre orantıdaki Fill-Mode sütunları arasında bölünür. Örneğin, iki sütunda 100 ve 200 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerler varsa, ilk sütun ikinci sütun kadar geniş olur.  
  
## <a name="user-resizing-in-fill-mode"></a>Fill modunda Kullanıcı yeniden boyutlandırma  
 Hücre içeriğine göre yeniden boyutlandırılan boyutlandırma modlarının aksine, Fill modu, kullanıcıların `true`<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özellik değerlerine sahip sütunları yeniden boyutlandırmasını engellemez. Bir Kullanıcı bir Fill-Mode sütununu yeniden boyutlandırdığında, yeniden boyutlandırılan sütundan sonra (<xref:System.Windows.Forms.Control.RightToLeft%2A> `false`, yoksa sola) tüm Fill modu sütunları, kullanılabilir genişlikteki değişikliği dengelemek için de yeniden boyutlandırılır. Yeniden boyutlandırılmış sütundan sonra Fill-Mode sütunları yoksa, denetimdeki diğer tüm Fill modu sütunları telafi için yeniden boyutlandırılır. Denetimde başka bir Fill-Mode sütunu yoksa yeniden boyutlandırma yok sayılır. Fill modunda olmayan bir sütun yeniden boyutlandırılırsa, denetimdeki tüm Fill modu sütunları, dengelemek için Boyutlar değişir.  
  
 Bir Fill Mode sütununu yeniden boyutlandırdıktan sonra, değiştirilen tüm sütunların <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerleri orantılı olarak ayarlanır. Örneğin, dört Fill-Mode sütununda 100 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değer varsa, ikinci sütunu özgün genişliğinin yarısı olacak şekilde yeniden boyutlandırılması, 100, 50, 125 ve 125 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerlerine neden olur. Fill modunda olmayan bir sütunun yeniden boyutlandırılması, tüm <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerlerini değiştirmez, çünkü Fill-Mode sütunları aynı oranları korurken yalnızca dengelemek için yeniden boyutlandırılacak.  
  
## <a name="content-based-fillweight-adjustment"></a>İçerik tabanlı FillWeight ayarlaması  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> yöntemi gibi <xref:System.Windows.Forms.DataGridView> otomatik yeniden boyutlandırma yöntemlerini kullanarak, Fill-Mode sütunları için <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerlerini başlatabilirsiniz. Bu yöntem ilk olarak, içeriklerinin gösterilmesi için sütunların gerektirdiği genişlikleri hesaplar. Daha sonra Denetim, tüm Fill modundaki sütunlar için <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerlerini ayarlar ve bu sayede oranlar hesaplanan genişliklerin oranlarına uyacak şekilde ayarlanır. Son olarak, denetim, denetim içindeki tüm sütunların kullanılabilir yatay alanı doldurmasını sağlamak için, yeni <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> oranlarını kullanarak Fill modundaki sütunları yeniden boyutlandırır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>ve <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özellikleri için uygun değerleri kullanarak, birçok farklı senaryo için sütun boyutlandırma davranışlarını özelleştirebilirsiniz.  
  
 Aşağıdaki gösterim kodu farklı sütunların <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>ve <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özellikleri için farklı değerlerle denemeler yapmanızı sağlar. Bu örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimi kendi <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonuna bağlanır ve bir sütun <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliklerinden her birine bağlanır. Sütunların her biri denetimdeki bir satır tarafından da temsil edilir ve bir satırdaki değerlerin değiştirilmesi karşılık gelen sütunun özelliklerini güncelleyerek değerlerin nasıl etkileşime gireceğini görebilirsiniz.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Açıklamalar  
 Bu demo uygulamasını kullanmak için:  
  
- Formun boyutunu değiştirin. <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri tarafından belirtilen oranları korurken sütunların genişliklerini nasıl değiştirdiğini gözlemleyin.  
  
- Sütun bölücüleri fareyle sürükleyerek sütun boyutlarını değiştirin. <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değerlerinin nasıl değiştiğini gözlemleyin.  
  
- Bir sütunun <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerini değiştirip formu yeniden boyutlandırmak için sürükleyin. Formu yeterince küçük yaptığınızda <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> değerleri <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerlerinin altına dönmeyeceği konusunda gözlemleyin.  
  
- Tüm sütunlar için <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değerlerini, Birleşik değerlerin denetimin genişliğini aşması için büyük sayı olarak değiştirin. Yatay kaydırma çubuğunun nasıl göründüğünü gözlemleyin.  
  
- Bazı sütunların <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> değerlerini değiştirin. Sütunları veya formu yeniden boyutlandırdığınızda etkiyi gözlemleyin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
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
