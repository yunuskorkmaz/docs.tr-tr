---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 358b5ed2ad201b2dfb0fef7bb960a88234939bf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme
<xref:System.Windows.Forms.DataGridView> Denetimi bir görünümünü ve davranışını özellikleri, olayları kullanarak özelleştirebileceğiniz ve sınıfları Yahoo! companion için çeşitli yöntemler sağlar. Bazen, bu özellikler sağlamak ötesine gidin, hücreler için gereksinimleri olabilir. Kendi özel Oluştur <xref:System.Windows.Forms.DataGridViewCell> genişletilmiş işlevselliği sağlamak için sınıf.  
  
 Bir özel Oluştur <xref:System.Windows.Forms.DataGridViewCell> türetilen sınıf <xref:System.Windows.Forms.DataGridViewCell> temel sınıfı veya türetilmiş sınıflarından biri. Herhangi bir türde sütun hücre herhangi bir türde görüntüleyebilse de, genellikle de bir özel oluşturacağınız <xref:System.Windows.Forms.DataGridViewColumn> sınıfı özelleştirilmiş hücre türünüz görüntülemek için. Sütun sınıfları türetilen <xref:System.Windows.Forms.DataGridViewColumn> veya türetilmiş türlerinden biri.  
  
 Aşağıdaki kod örneğinde adlı bir özel hücre sınıf oluşturacak `DataGridViewRolloverCell` fare girer ve hücre kenarlıklarını çıktığında algılar. Fare hücrenin sınırları içinde olsa da, bir iç dikdörtgen çizilir. Bu yeni tür türetilen <xref:System.Windows.Forms.DataGridViewTextBoxCell> ve diğer tüm yönden devralınabilir. taban sınıf davranır. Yardımcı sütun sınıfı adlı `DataGridViewRolloverColumn`.  
  
 Bu sınıfların kullanmak için içeren bir form oluşturun bir <xref:System.Windows.Forms.DataGridView> denetlemek, bir veya daha fazla Ekle `DataGridViewRolloverColumn` nesneleri için <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu ve denetim değerler içeren satırları ile doldurabilirsiniz.  
  
> [!NOTE]
>  Boş satırlar eklerseniz, bu örnek düzgün çalışmaz. Boş satırlar oluşturulur, örneğin, ayarlayarak satırları denetimine eklediğinizde <xref:System.Windows.Forms.DataGridView.RowCount%2A> özelliği. Eklenen satır bu durumda otomatik olarak paylaşılır; yani olmasıdır `DataGridViewRolloverCell` ayrı hücrelere, böylelikle ilişkili satırları paylaşılmayan hale gelmesine yol tıklatıncaya kadar nesneleri örneği değil.  
  
 Bu tür hücre özelleştirme paylaşılmayan satırları gerektirdiğinden, büyük veri kümeleri ile kullanım için uygun değil. Satır paylaşma hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Türetilen zaman <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilen sınıfın yeni özellikler ekleme, geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntem. Temel sınıfın da çağırmalıdır `Clone` yöntemi böylece temel sınıfının özelliklerini yeni hücresinde veya sütununda kopyalanır.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Hücre ve sütunları DataGridView denetiminde özelleştirme  
  
1.  Adlı yeni bir hücre sınıf türetin `DataGridViewRolloverCell`, gelen <xref:System.Windows.Forms.DataGridViewTextBoxCell> türü.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> yönteminde `DataGridViewRolloverCell` sınıfı. Geçersiz kılmada barındırılan metin kutusunun işlevlerini işleme temel sınıf uygulamasını çağırın. Denetimin kullanmak <xref:System.Windows.Forms.Control.PointToClient%2A> imleç konumu (ekran koordinatları) dönüştürmek için yöntemi <xref:System.Windows.Forms.DataGridView> istemci alanının koordinatları. Fare koordinatları hücre sınırları içinde halindeyse dışarı dikdörtgen çizin.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Geçersiz kılma <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> ve <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> yöntemleri `DataGridViewRolloverCell` fare işaretçisini girdiğinde veya bunları bırakır kendilerini çizilecek hücreleri zorlamak için sınıf.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Adlı yeni bir sınıf türetin `DataGridViewRolloverCellColumn`, gelen <xref:System.Windows.Forms.DataGridViewColumn> türü. Oluşturucuda, yeni bir Ata `DataGridViewRolloverCell` nesnesini kendi <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Örnek  
 Tam kod örneği, özel hücre türünün davranışını gösteren küçük test form içerir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Windows.Forms ve System.Drawing derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView Denetimi Mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
