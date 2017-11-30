---
title: "Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc7fd3d3012053d8c40edf5fdce8af45c62c98c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları
<xref:System.Windows.Forms.DataGridView> Denetim, üç farklı modda verileri görüntüleyebilir: ilişkili, ilişkisiz ve sanal. Gereksinimlerinize göre en uygun modu seçin.  
  
## <a name="unbound"></a>Bağlanmamış  
 İlişkisiz Modu görece küçük miktarda programlama yoluyla yönetilmesi veri görüntülemek için uygundur. Eklediğiniz değil <xref:System.Windows.Forms.DataGridView> denetimine doğrudan bağlı mod olduğu gibi bir veri kaynağı. Bunun yerine, Denetim kendiniz genellikle kullanarak doldurmanız gerekir <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemi.  
  
 İlişkisiz modu veya statik ve salt okunur veri için bir dış veri deposuyla etkileşime giren kendi kodunuzu sağlamak istediğinizde özellikle yararlı olabilir. Ancak, bir dış veri kaynağı ile etkileşim kurmak için kullanıcılarınızın istediğinizde, genellikle bağlı mod kullanır.  
  
 Salt okunur kullanan bir örnek için ilişkisiz <xref:System.Windows.Forms.DataGridView>, bkz: [nasıl yapılır: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Bağlı  
 Bağlı mod, veri deposu otomatik etkileşim kullanarak verileri yönetmek için uygundur. Ekleyebilir miyim <xref:System.Windows.Forms.DataGridView> denetim ayarlayarak doğrudan kendi veri kaynağına <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği. Denetim veri bağlı olduğunda, veriler satırlar gönderilir ve açık yönetim yapmanıza gerek kalmadan çekilen. Zaman <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özelliği `true`, her sütunun veri kaynağınızda denetiminde oluşturulacak karşılık gelen bir sütuna neden olur. Kendi sütunları oluşturmayı tercih ederseniz, bu özelliği ayarlayabilirsiniz `false` ve <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> her sütun, yapılandırdığınızda bağlamak için özellik. Sütun türü varsayılan olarak oluşturulan türleri dışında kullanmak istediğinizde kullanışlıdır. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sütun türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).  
  
 Bağımlı kullanan bir örnek <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Bağlanmamış sütunlar için de ekleyebilirsiniz bir <xref:System.Windows.Forms.DataGridView> ilişkili modunda denetimi. Bir sütunu düğmeler veya kullanıcıların belirli satırlarda eylemler gerçekleştirmesine olanak sağlayan bağlantıları görüntülemek istediğinizde kullanışlıdır. İlişkili sütunlardan hesaplanan değerler ile sütunları görüntülemek yararlıdır. İçin bir işleyici hesaplanan sütunlar için hücre değerlerinin doldurabilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting> olay. Kullanıyorsanız bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> veri kaynağı olarak Bununla birlikte, kullanmak istediğiniz <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> özelliği hesaplanmış bir sütun oluşturun. Bu durumda, <xref:System.Windows.Forms.DataGridView> denetim kabul et herhangi bir veri kaynağı sütununda gibi hesaplanan sütun.  
  
 İlişkili modunda ilişkisiz sütuna göre sıralama desteklenmiyor. Kullanıcı tarafından düzenlenebilir değerleri içeren ilişkili modunda bağlantısız sütun oluşturursanız, bu değerleri denetimi ilişkili bir sütuna göre sıralandığında korumak için sanal modu uygulamalıdır.  
  
## <a name="virtual"></a>Sanal  
 İle sanal modu, kendi veri yönetimi işlemleri uygulayabilirsiniz. Bu denetim ilişkili sütunlara göre sıralandığında bağlanmamış sütunlar değerlerini ilişkili modunda korumak gereklidir. Birincil sanal modu, ancak, büyük miktarlarda veri kullanılırken performansını iyileştirmek için kullanılır.  
  
 Eklediğiniz <xref:System.Windows.Forms.DataGridView> yönettiğiniz bir önbellek denetimine ve veri satırı gönderilir ve çekilen kod denetimleri. Bellek alanını küçük tutmak için önbellek boyutu şu anda görüntülenen satır sayısını benzer olmalıdır. Kullanıcı yeni satırlar görünüme kaydırdığında kodunuzu yeni verileri önbellekten ister ve isteğe bağlı olarak bellekten eski verileri temizler.  
  
 Sanal mod uygularken, yeni bir satır veri modelindeki ve geri alma sırasında yeni satır eklenmesi gerektiğinde izlemek gerekir. Bu işlevlerin tam uygulama ve veri modelinin uygulama ve veri modelinin işlem semantiği değişir; hücre veya satır düzeyinde tamamlama kapsamı olup olmadığı.  
  
 Sanal modu hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sanal mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md). Sanal mod olayların nasıl gösteren bir örnek için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView denetiminde verileri görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetiminde sütun türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [İzlenecek yol: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: veri bağlama Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [Sanal mod Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
