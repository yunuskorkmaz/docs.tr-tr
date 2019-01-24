---
title: Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 6800294f2bd3a126f9606a7877455248ec76f758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688179"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları
<xref:System.Windows.Forms.DataGridView> Denetim, üç ayrı modda veri görüntüleyebilir: ilişkili, bağlantısız ve sanal. Gereksinimlerinize göre en uygun modu seçin.  
  
## <a name="unbound"></a>Bağlanmamış  
 İlişkisiz Modu görece küçük miktarlarda programlama yoluyla yönetme veri görüntülemek için uygundur. Eklediğiniz değil <xref:System.Windows.Forms.DataGridView> bağımlı modu olduğu gibi veri kaynağına doğrudan denetimi. Bunun yerine, denetime kendiniz genellikle kullanarak doldurmanız gerekir <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemi.  
  
 İlişkisiz modu veya statik ve salt okunur veriler için bir dış veri deposuyla etkileşime giren kendi kodunuzu sağlamak istediğinizde özellikle yararlı olabilir. Ancak, bir dış veri kaynağı ile etkileşim kurmak için kullanıcılarınızın istediğinizde, genellikle bağımlı mod kullanır.  
  
 Salt okunur kullanan bir örnek için ilişkisiz <xref:System.Windows.Forms.DataGridView>, bkz: [nasıl yapılır: Bir bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>bağlı  
 Bağlı mod, verileri veri deposuna otomatik olarak etkileşim kullanarak yönetmek için uygundur. İliştirebilirsiniz <xref:System.Windows.Forms.DataGridView> ayarlayarak doğrudan kendi veri kaynağı için Denetim <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği. Denetimi veri bağımlı olduğunda, veri satırları gönderildi ve açık yönetim yapmanıza gerek olmadan çekilir. Zaman <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özelliği `true`, her sütun, veri kaynağınızda denetiminde oluşturulacak karşılık gelen bir sütun neden olur. Kendi sütunlar oluşturmak isterseniz, bu özelliği ayarlayın `false` ve <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> her sütun, yapılandırdığınızda bağlamak için özellik. Varsayılan olarak oluşturulan türler dışında bir sütun türü kullanmak istediğinizde bu kullanışlıdır. Daha fazla bilgi için [Windows Forms DataGridView denetiminde sütun türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).  
  
 Bağımlı kullanan bir örnek için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [izlenecek yol: Doğrulama verileri Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Bağlanmamış sütunlar için de ekleyebilirsiniz bir <xref:System.Windows.Forms.DataGridView> ilişkili modunda denetimi. Düğmeler veya kullanıcıların belirli bir satırda eylemleri gerçekleştirmek bağlantılar içeren bir sütun görüntülemek istediğinizde bu kullanışlıdır. İlişkili sütunlardan hesaplanan değerlerle sütunları görüntülemek yararlıdır. İçin bir işleyici hesaplanmış sütunlar için hücre değerlerinin doldurabilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting> olay. Kullanıyorsanız bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> veri kaynağı olarak, ancak kullanmak isteyebileceğiniz <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> özelliği bunun yerine hesaplanmış bir sütun oluşturun. Bu durumda, <xref:System.Windows.Forms.DataGridView> denetimi işlemek gibi herhangi bir veri kaynağı sütununda hesaplanmış sütun.  
  
 Bağlanmamış sütunlar ilişkili modunda sıralama desteklenmiyor. Kullanıcı tarafından düzenlenebilir değerleri içeren ilişkili modunda bağlantısız sütun oluşturursanız, bu değerler, Denetim, ilişkili bir sütuna göre sıralanmış korumak için sanal mod uygulamalıdır.  
  
## <a name="virtual"></a>Sanal  
 İle sanal modu, kendi veri yönetimi işlemleri uygulayabilir. Bu denetim, ilişkili sütunlara göre sıralandığında ilişkili modunda bağlanmamış sütunlar değerlerini korumak gereklidir. Birincil sanal modu ancak büyük miktarda veriyle etkileşim kurulurken performansı iyileştirmek için kullanılır.  
  
 Eklediğiniz <xref:System.Windows.Forms.DataGridView> yönettiğiniz bir önbellek denetimi ve kod denetimlerinizi veri satırları gönderildi ve çekilir. Bellek Ayak izi küçük tutmak için önbellek boyutu şu anda görüntülenen satırların sayısı için benzer olmalıdır. Kullanıcı, yeni satır, görünüme kaydırdığında, kodunuzu yeni verileri önbellekten ister ve isteğe bağlı olarak eski verileri bellekten temizler.  
  
 Sanal mod uygularken, yeni bir satır veri modeline geri alma, yeni satır eklenmesi gerektiğinde izlemek gerekir. Bu işlevlerin tam uygulama, veri modelinin uygulanması ve veri modeline işlem semantiği bağlıdır; işleme kapsamı bir veya daha fazla satır düzeyinde olup olmadığı.  
  
 Sanal mod hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sanal mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md). Sanal modu olaylarını kullanmayı gösteren bir örnek için bkz: [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Bağlantısız bir Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
