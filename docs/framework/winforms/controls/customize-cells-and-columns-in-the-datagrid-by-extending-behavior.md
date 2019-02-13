---
title: 'Nasıl yapılır: Davranış ve görünümünü genişleterek hücre ve sütunları Windows Forms DataGridView denetiminde özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: fbeb161a9813b2d1b479b76360149ed08212459f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220712"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Nasıl yapılır: Davranış ve görünümünü genişleterek hücre ve sütunları Windows Forms DataGridView denetiminde özelleştirme
<xref:System.Windows.Forms.DataGridView> Denetimi, çeşitli yollarla görünümünü ve davranışını özellikleri, olayları kullanarak özelleştirip Yahoo! companion sınıfları sağlar. Bazen, bu özellikleri sağlamak ötesine gidin, hücre için gereksinimlerine sahip olabilir. Kendi özel oluşturabilirsiniz <xref:System.Windows.Forms.DataGridViewCell> genişletilmiş işlevselliği sağlamak için sınıf.  
  
 Bir özel Oluştur <xref:System.Windows.Forms.DataGridViewCell> türetilen sınıf <xref:System.Windows.Forms.DataGridViewCell> temel sınıfı veya türetilmiş sınıflarının biri. Hücre herhangi bir türde herhangi bir türde sütun görüntüleyebilse de, genellikle de bir özel oluşturacağınız <xref:System.Windows.Forms.DataGridViewColumn> sınıfı özel hücre türünüz görüntülemek için. Sütun sınıflar türetilen <xref:System.Windows.Forms.DataGridViewColumn> veya türetilmiş türlerini biri.  
  
 Aşağıdaki kod örneğinde adlı bir özel hücre sınıf oluşturacağınız `DataGridViewRolloverCell` fare girer ve hücre sınırları dışına algılar. Fare hücrenin sınırları içinde olsa da, bir iç dikdörtgen çizilir. Bu yeni türü türetilen <xref:System.Windows.Forms.DataGridViewTextBoxCell> ve diğer tüm açılardan taban sınıfı davranır. Yardımcısı sütun sınıfa `DataGridViewRolloverColumn`.  
  
 Bu sınıfların kullanmak için içeren bir form oluşturun bir <xref:System.Windows.Forms.DataGridView> denetiminde, bir veya daha fazla Ekle `DataGridViewRolloverColumn` nesneleri için <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu ve denetimi doldurma değerler içeren satırları ile.  
  
> [!NOTE]
>  Boş satırları eklerseniz, bu örnekte düzgün çalışmaz. Boş bir satır oluşturulur, örneğin, ayarlayarak satır denetimi eklediğinizde <xref:System.Windows.Forms.DataGridView.RowCount%2A> özelliği. Eklenen satırları bu durumda otomatik olarak paylaşılır, yani olmasıdır `DataGridViewRolloverCell` tek tek hücreleri, böylece ilişkili satırları paylaşılmayan duruma neden tıklayana kadar nesne örneği değil.  
  
 Bu tür bir hücre özelleştirme paylaşılmayan satırları gerektirdiğinden, büyük veri kümeleri ile kullanım için uygun değil. Satır paylaşma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Olduğunda, türetilen <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıf için yeni özellikler eklemek için geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi. Ayrıca temel sınıfın çağırmalıdır `Clone` yöntemi, böylece yeni hücresinde veya sütununda için temel sınıf özelliklerini kopyalanır.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Hücre ve sütunları DataGridView denetiminde özelleştirme  
  
1.  Adlı yeni bir hücre sınıf türetmek `DataGridViewRolloverCell`, gelen <xref:System.Windows.Forms.DataGridViewTextBoxCell> türü.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> yönteminde `DataGridViewRolloverCell` sınıfı. Geçersiz kılma seçeneğinde barındırılan metin kutusu işlevlerini işleyen temel sınıf uygulamasına çağırın. Ardından denetimin kullanın <xref:System.Windows.Forms.Control.PointToClient%2A> imleç konumu (ekran koordinatlarında) dönüştürmek için yöntemi <xref:System.Windows.Forms.DataGridView> istemci alanının koordinatları. Fare koordinatları hücrenin sınırları içinde düşersek iç dikdörtgen çizin.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Geçersiz kılma <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> ve <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> yöntemleri `DataGridViewRolloverCell` fare işaretçisi girdiğinde veya bunları bırakır kendilerini repaint hücrelere zorlamak için sınıf.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Adlı yeni bir sınıf türetin `DataGridViewRolloverCellColumn`, gelen <xref:System.Windows.Forms.DataGridViewColumn> türü. Yeni bir oluşturucuda atama `DataGridViewRolloverCell` nesnesini kendi <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Örnek  
 Özel hücresi türü davranışını gösteren bir küçük test form tam kod örneği içerir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Windows.Forms ve System.Drawing derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
