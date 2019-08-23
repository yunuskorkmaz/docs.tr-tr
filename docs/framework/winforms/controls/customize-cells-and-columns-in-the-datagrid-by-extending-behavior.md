---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 0976a0e07aead1bbaf951c6db8266c5de1a31cd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929697"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme
<xref:System.Windows.Forms.DataGridView> Denetim, özellikleri, olayları ve yardımcı sınıfları kullanarak görünümünü ve davranışını özelleştirmek için çeşitli yollar sağlar. Kimi zaman, bu özelliklerin sağlayabildiklerinden daha fazla geçen hücreler için gereksinimlerinize sahip olabilirsiniz. Genişletilmiş işlevsellik sağlamak için kendi özel <xref:System.Windows.Forms.DataGridViewCell> sınıfınızı oluşturabilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridViewCell> Temel sınıftan türeterek <xref:System.Windows.Forms.DataGridViewCell> veya türetilmiş sınıflarından biriyle özel bir sınıf oluşturursunuz. Herhangi bir sütun türünde herhangi bir hücre türünü görüntülemenizi mümkün olsa da, genellikle hücre türünü görüntülemek için özelleştirilmiş özel <xref:System.Windows.Forms.DataGridViewColumn> bir sınıf oluşturursunuz. Sütun sınıfları <xref:System.Windows.Forms.DataGridViewColumn> türetilmiş türlerinden biri veya ondan türetilir.  
  
 Aşağıdaki kod örneğinde, fare hücre sınırlarını girdiğinde ve ne zaman bırakılırsa algılayan `DataGridViewRolloverCell` adlı bir özel hücre sınıfı oluşturacaksınız. Fare hücrenin sınırları içinde olduğunda, bir iç içe dikdörtgen çizilir. Bu yeni tür öğesinden <xref:System.Windows.Forms.DataGridViewTextBoxCell> türetilir ve kendi temel sınıfı olarak diğer tüm gibi davranır. Yardımcı sütun sınıfı çağrılır `DataGridViewRolloverColumn`.  
  
 Bu sınıfları kullanmak için, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form oluşturun, <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyona bir veya daha `DataGridViewRolloverColumn` fazla nesne ekleyin ve denetimi değer içeren satırlarla doldurun.  
  
> [!NOTE]
> Boş satırlar eklerseniz bu örnek düzgün çalışmayacaktır. Boş satırlar, örneğin, <xref:System.Windows.Forms.DataGridView.RowCount%2A> özelliği ayarlayarak denetime satır eklediğinizde oluşturulur. Bunun nedeni, bu durumda eklenen satırların otomatik olarak paylaşılmasıdır, yani tek tek hücrelere `DataGridViewRolloverCell` tıklayana kadar nesneler örneklenemez ve bu sayede ilişkili satırların paylaşılmayan hale gelmesine neden olur.  
  
 Bu tür hücre özelleştirmesi paylaşılmayan satırlar gerektirdiğinden, büyük veri kümeleriyle kullanım için uygun değildir. Satır paylaşımı hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirmek Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Türetilmiş sınıfa türeten <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemi geçersiz kıldığınızdan emin olun. Ayrıca temel sınıfın özelliklerini yeni hücreye veya sütuna `Clone` kopyalamak için temel sınıfın yöntemini çağırmanız gerekir.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>DataGridView Denetimindeki hücreleri ve sütunları özelleştirmek için  
  
1. Türünden<xref:System.Windows.Forms.DataGridViewTextBoxCell> adlı `DataGridViewRolloverCell`yeni bir hücre sınıfı türetirsiniz.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> Sınıfında yöntemi`DataGridViewRolloverCell` geçersiz kılın. Geçersiz kılmada, önce barındırılan metin kutusu işlevini işleyen temel sınıf uygulamasını çağırın. Ardından, imleç konumunu ( <xref:System.Windows.Forms.Control.PointToClient%2A> Ekran koordinatlarında) <xref:System.Windows.Forms.DataGridView> istemci alanının koordinatlarına dönüştürmek için denetimin yöntemini kullanın. Fare koordinatları hücrenin sınırları içine düşerseniz, iç içe dikdörtgen çizin.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Fare işaretçisi onları <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> girdiğinde veya ayrıldığında `DataGridViewRolloverCell` hücreleri yenidençizmeyizorlamakiçinsınıfındakiveyöntemlerinigeçersizkılın.<xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Türünden<xref:System.Windows.Forms.DataGridViewColumn> adlı `DataGridViewRolloverCellColumn`yeni bir sınıf türetirsiniz. Oluşturucuda, `DataGridViewRolloverCell` <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> özelliğine yeni bir nesne atayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Örnek  
 Bütün kod örneği, özel hücre türünün davranışını gösteren küçük bir test formu içerir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Sisteme, System. Windows. Forms ve System. Drawing derlemelerine başvurular.  
 
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
