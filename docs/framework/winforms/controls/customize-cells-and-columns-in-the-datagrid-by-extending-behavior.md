---
title: DataGridView Denetimindeki Hücreleri ve Sütunları Davranış larını ve Görünümlerini Genişleterek Özelleştirin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: e111f0bce812fc0851fabd1fde0fc2a6d44dd25f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182387"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme
Denetim <xref:System.Windows.Forms.DataGridView> özellikleri, olayları ve eşlik eden sınıfları kullanarak görünümünü ve davranışını özelleştirmek için çeşitli yollar sağlar. Bazen, hücreleriniz için bu özelliklerin sağlayabileceğinin ötesine geçme gereksinimleriniz olabilir. Genişletilmiş işlevsellik sağlamak <xref:System.Windows.Forms.DataGridViewCell> için kendi özel sınıfınızı oluşturabilirsiniz.  
  
 Taban sınıftan <xref:System.Windows.Forms.DataGridViewCell> <xref:System.Windows.Forms.DataGridViewCell> veya türetilmiş sınıflarından birinden türeerek özel bir sınıf oluşturursunuz. Herhangi bir sütun türünde herhangi bir hücre türünü görüntüleseniz de, genellikle hücre türünü görüntülemek için özelleştirilmiş özel <xref:System.Windows.Forms.DataGridViewColumn> bir sınıf da oluşturursunuz. Sütun sınıfları <xref:System.Windows.Forms.DataGridViewColumn> türetilmiş türlerinden birinden veya türetilmiş türlerinden birinden türetilmiştir.  
  
 Aşağıdaki kod örneğinde, fare hücre sınırlarına `DataGridViewRolloverCell` girip ne zaman ayrıldığını algılayan özel bir hücre sınıfı oluşturursunuz. Fare hücrenin sınırları içindeyken, bir gelen dikdörtgen çizilir. Bu yeni tür, <xref:System.Windows.Forms.DataGridViewTextBoxCell> taban sınıf olarak diğer tüm yönlerden türetilmiştir ve böyle bir şekilde de öyle bir şekilde iş yapmalıdır. Eşlik eden sütun `DataGridViewRolloverColumn`sınıfı denir.  
  
 Bu sınıfları kullanmak için denetim <xref:System.Windows.Forms.DataGridView> içeren bir form `DataGridViewRolloverColumn` oluşturun, <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyona bir veya daha fazla nesne ekleyin ve denetimi değerleri içeren satırlarla doldurun.  
  
> [!NOTE]
> Boş satırlar eklerseniz, bu örnek düzgün çalışmaz. Boş satırlar, örneğin, <xref:System.Windows.Forms.DataGridView.RowCount%2A> özelliği ayarlayarak denetime satır eklediğinizde oluşturulur. Bunun nedeni, bu durumda eklenen satırların otomatik olarak `DataGridViewRolloverCell` paylaşılmasıdır, bu da siz tek tek hücreleri tıklayana kadar nesnelerin anlık olarak anlık olarak kullanılmaması ve böylece ilişkili satırların paylaşılmamasına neden olmasıdır.  
  
 Bu tür hücre özelleştirmesi paylaşılmayan satırlar gerektirdiğinden, büyük veri kümeleriyle kullanmak uygun değildir. Satır paylaşımı hakkında daha fazla bilgi için [Windows Formlarını Veri GridView Denetimini Ölçekleme için En İyi Uygulamalar'a](best-practices-for-scaling-the-windows-forms-datagridview-control.md)bakın.  
  
> [!NOTE]
> Türemiş <xref:System.Windows.Forms.DataGridViewCell> sınıfa <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler türetdiğinizde veya yeni özellikler `Clone` eklediğinizde, klonlama işlemleri sırasında yeni özellikleri kopyalama yöntemini geçersiz kıldığınızdan emin olun. Taban sınıfın özelliklerinin yeni `Clone` hücreye veya sütuna kopyalanabilmesi için taban sınıfın yöntemini de aramalısınız.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>DataGridView denetimindeki hücreleri ve sütunları özelleştirmek için  
  
1. Türden , adı verilen `DataGridViewRolloverCell`yeni <xref:System.Windows.Forms.DataGridViewTextBoxCell> bir hücre sınıfı türetin.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. `DataGridViewRolloverCell` Sınıftayöntemi <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> geçersiz kılın. Geçersiz kılmada, önce barındırılan metin kutusu işlevini işleyen taban sınıf uygulamasını çağırın. Ardından imleç konumunu <xref:System.Windows.Forms.Control.PointToClient%2A> (ekran koordinatlarında) istemci alanının koordinatlarına <xref:System.Windows.Forms.DataGridView> dönüştürmek için denetim yöntemini kullanın. Fare koordinatları hücrenin sınırları içinde kalıyorsa, gelen dikdörtgeni çizin.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Fare işaretçisi `DataGridViewRolloverCell` girdiğinde veya onları terk ettiğinde hücreleri kendilerini yeniden boyamaya zorlamak için sınıftaki <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> yöntemleri geçersiz kılın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Türden , adı `DataGridViewRolloverCellColumn`verilen yeni <xref:System.Windows.Forms.DataGridViewColumn> bir sınıf türetin. Oluşturucuolarak, özelliğine <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> yeni `DataGridViewRolloverCell` bir nesne atayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Örnek  
 Tam kod örneği, özel hücre türünün davranışını gösteren küçük bir test formu içerir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Sistem, System.Windows.Forms ve System.Drawing derlemelerine yapılan atıflar.  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetim Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
