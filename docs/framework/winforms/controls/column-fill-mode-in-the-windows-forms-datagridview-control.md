---
title: DataGridView denetiminde sütun dolgusu modu
description: Sütun dolgusu modundaki Windows Forms DataGridView denetiminin, kullanılabilir görüntü alanının genişliğini dolduracak şekilde sütunlarının otomatik olarak nasıl yeniden boyutlandırılacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 766a58954250d78ce6e44404730332b3158e1fad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622828"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Doldurma Modu
Sütun dolgusu modunda, <xref:System.Windows.Forms.DataGridView> Denetim sütunlarını otomatik olarak yeniden boyutlandırır, böylece kullanılabilir görüntü alanının genişliğini dolduracak. Denetim, her sütunun genişliğini özellik değerine eşit veya ondan daha büyük tutmak için gerekli olduğu durumlar dışında yatay kaydırma çubuğunu görüntülemez <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> .  
  
 Her sütunun boyutlandırma davranışı, <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliğine bağlıdır. Bu özelliğin değeri sütunun <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğinden veya <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> sütunun değeri <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (varsayılan değer) ise denetimin özelliğinden devralınır.  
  
 Her sütunda farklı bir boyut modu olabilir, ancak boyut modu olan sütunlar <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> diğer sütunlarda kullanılmayan görüntü alanı genişliğini paylaşır. Bu genişlik, özellik değerlerine göre orantıdaki Fill-Mode sütunları arasında bölünür <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> . Örneğin, iki sütun <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100 ve 200 değerlerini içeriyorsa, ilk sütun ikinci sütun kadar geniş olur.  
  
## <a name="user-resizing-in-fill-mode"></a>Fill modunda Kullanıcı yeniden boyutlandırma  
 Hücre içeriğine göre yeniden boyutlandırdığınız boyutlandırma modlarının aksine, Fill modu kullanıcıların özellik değerleri olan sütunları yeniden boyutlandırmasını engellemez <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> `true` . Bir Kullanıcı bir Fill-Mode sütununu yeniden boyutlandırdığında, yeniden boyutlandırılan sütundan sonraki tüm Fill-Mode sütunları (varsa sağa <xref:System.Windows.Forms.Control.RightToLeft%2A> ) ve diğer bir deyişle `false` solda), kullanılabilir genişlikdeki değişikliği dengelemek için de yeniden boyutlandırılır. Yeniden boyutlandırılmış sütundan sonra Fill-Mode sütunları yoksa, denetimdeki diğer tüm Fill modu sütunları telafi için yeniden boyutlandırılır. Denetimde başka bir Fill-Mode sütunu yoksa yeniden boyutlandırma yok sayılır. Fill modunda olmayan bir sütun yeniden boyutlandırılırsa, denetimdeki tüm Fill modu sütunları, dengelemek için Boyutlar değişir.  
  
 Bir Fill Mode sütununu yeniden boyutlandırdıktan sonra, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> değiştirilen tüm sütunların değerleri orantılı olarak ayarlanır. Örneğin, dört Fill-Mode sütununda <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100 değeri varsa, ikinci sütunu özgün genişliğinin yarısı olacak şekilde yeniden boyutlandırılması <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 100, 50, 125 ve 125 değerlerine neden olur. Aynı oranları korurken, Fill modunda olmayan bir sütunun yeniden boyutlandırılması herhangi bir değeri değiştirmez, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> çünkü Fill modundaki sütunlar yalnızca dengelemek için yeniden boyutlandırılacak.  
  
## <a name="content-based-fillweight-adjustment"></a>İçerik tabanlı FillWeight ayarlaması  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> <xref:System.Windows.Forms.DataGridView> Yöntemi gibi otomatik yeniden boyutlandırma yöntemlerini kullanarak, Fill-Mode sütunlarının değerlerini başlatabilirsiniz <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> . Bu yöntem ilk olarak, içeriklerinin gösterilmesi için sütunların gerektirdiği genişlikleri hesaplar. Daha sonra Denetim, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> Tüm Fill-Mode sütunlarının değerlerini, hesaplanan genişlikler oranlarına uyacak şekilde ayarlar. Son olarak, denetim, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> denetimin tüm sütunlarının kullanılabilir yatay alanı doldurmasını sağlamak için, yeni oranları kullanarak Fill modundaki sütunları yeniden boyutlandırır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 ,,, Ve özellikleri için uygun değerleri kullanarak, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> birçok farklı senaryo için sütun boyutlandırma davranışlarını özelleştirebilirsiniz.  
  
 Aşağıdaki tanıtım kodu, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> farklı sütunların,, ve özellikleri için farklı değerlerle denemeler yapmanızı sağlar <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> . Bu örnekte, bir <xref:System.Windows.Forms.DataGridView> Denetim kendi <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonuna bağlanır ve bir sütun,,,, <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A> <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliklerinden her birine bağlanır. Sütunların her biri denetimdeki bir satır tarafından da temsil edilir ve bir satırdaki değerlerin değiştirilmesi karşılık gelen sütunun özelliklerini güncelleyerek değerlerin nasıl etkileşime gireceğini görebilirsiniz.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Yorumlar  
 Bu demo uygulamasını kullanmak için:  
  
- Formun boyutunu değiştirin. Özellik değerleri tarafından belirtilen oranları korurken sütunların genişliklerini nasıl değiştirdiğini gözlemleyin <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> .  
  
- Sütun bölücüleri fareyle sürükleyerek sütun boyutlarını değiştirin. Değerlerin nasıl değiştiğini gözlemleyin <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> .  
  
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>Bir sütun için değeri değiştirin ve sonra formu yeniden boyutlandırmak için sürükleyin. Formu yeterince küçük yaptığınızda <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> değerlerin altına gitmediğinden emin olun <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> .  
  
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>Birleşik değerlerin denetimin genişliğini aşması için tüm sütunların değerlerini büyük sayılarla değiştirin. Yatay kaydırma çubuğunun nasıl göründüğünü gözlemleyin.  
  
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>Bazı sütunlar için değerleri değiştirin. Sütunları veya formu yeniden boyutlandırdığınızda etkiyi gözlemleyin.  
  
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
