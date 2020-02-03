---
title: DataGridView Denetimindeki veri görüntüleme modları
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: ad6be647e3a36904b055fd6771f539df28938fab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744013"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları
<xref:System.Windows.Forms.DataGridView> denetim verileri üç farklı modda görüntüleyebilir: bağlı, ilişkisiz ve sanal. Gereksinimlerinize göre en uygun modu seçin.  
  
## <a name="unbound"></a>Kaldır  
 İlişkisiz mod, programlama yoluyla yönettiğiniz görece küçük miktarlarda veriyi görüntülemek için uygundur. <xref:System.Windows.Forms.DataGridView> denetimini, bağlama modunda olduğu gibi doğrudan bir veri kaynağına iliştiremez. Bunun yerine, genellikle <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemini kullanarak denetimi kendiniz doldurmanız gerekir.  
  
 İlişkisiz mod özellikle statik, salt okuma verileri için veya bir dış veri deposuyla etkileşim kuran kendi kodunuzu sağlamak istediğinizde yararlı olabilir. Kullanıcılarınızın bir dış veri kaynağıyla etkileşime geçmesini istediğinizde, genellikle sınırlı modu kullanırsınız.  
  
 Salt biçimli ilişkisiz <xref:System.Windows.Forms.DataGridView>kullanan bir örnek için bkz. [nasıl yapılır: ilişkisiz Windows Forms DataGridView denetimi oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Bound  
 Sınırlı mod, veri deposuyla otomatik etkileşim kullanılarak verilerin yönetilmesi için uygundur. <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlayarak <xref:System.Windows.Forms.DataGridView> denetimini doğrudan kendi veri kaynağına ekleyebilirsiniz. Denetim veri bağladığında, veri satırları, sizin bölüminizdeki açık yönetime gerek olmadan itilir ve çekilir. <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> Özellik `true`olduğunda, veri kaynağınızdaki her sütun denetimde ilgili bir sütunun oluşturulmasına neden olur. Kendi sütunlarınızı oluşturmayı tercih ediyorsanız, bu özelliği `false` olarak ayarlayabilir ve <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> özelliğini kullanarak her sütunu yapılandırdığınızda bağlayabilirsiniz. Bu, varsayılan olarak oluşturulan türlerden farklı bir sütun türü kullanmak istediğinizde yararlıdır. Daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki sütun türleri](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Bağlantılı <xref:System.Windows.Forms.DataGridView> denetimi kullanan bir örnek için bkz. [Walkthrough: Windows Forms DataGridView Denetimindeki verileri doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Ayrıca, bağlı moddaki bir <xref:System.Windows.Forms.DataGridView> denetimine ilişkisiz sütunlar ekleyebilirsiniz. Bu, kullanıcıların belirli satırlarda eylem gerçekleştirmesini sağlayan düğmelerin veya bağlantıların bir sütununu göstermek istediğinizde yararlıdır. Ayrıca, ilişkili sütunlardan hesaplanan değerlere sahip sütunları göstermek de yararlı olur. <xref:System.Windows.Forms.DataGridView.CellFormatting> olayı için bir işleyicide hesaplanan sütunların hücre değerlerini doldurabilirsiniz. Ancak veri kaynağı olarak bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> kullanıyorsanız, bunun yerine bir hesaplanmış sütun oluşturmak için <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> özelliğini kullanmak isteyebilirsiniz. Bu durumda, <xref:System.Windows.Forms.DataGridView> denetimi hesaplanmış sütunu veri kaynağındaki diğer sütunlara benzer şekilde değerlendirir.  
  
 İlişkisiz sütunlara göre sıralama, ilişkili modda desteklenmez. Bağlı modda, Kullanıcı tarafından düzenlenebilir değerler içeren ilişkisiz bir sütun oluşturursanız, denetim bir ilişkili sütuna göre sıralandığında bu değerleri korumak için sanal modu uygulamanız gerekir.  
  
## <a name="virtual"></a>Sanal  
 Sanal mod ile kendi veri yönetimi işlemlerinizi uygulayabilirsiniz. Bu, Denetim bağlantılı sütunlara göre sıralandığında, bağlı moddaki ilişkisiz sütunların değerlerini korumak için gereklidir. Ancak, sanal modun birincil kullanımı, büyük miktarlarda verilerle etkileşim kurarken performansı optimize etmek için kullanılır.  
  
 Yönettiğiniz bir önbelleğe <xref:System.Windows.Forms.DataGridView> denetimini iliştirmiş ve veri satırları itilmiş ve çekildiğinde kod denetimleriniz. Bellek ayak izini küçük tutmak için, önbelleğin boyut olarak şu anda görüntülenen satır sayısına benzer olması gerekir. Kullanıcı yeni satırları görünüme kaydırdığında, kodunuz önbellekteki yeni verileri ister ve isteğe bağlı olarak bellekten eski verileri temizler.  
  
 Sanal modu uygularken, veri modelinde yeni bir satır gerekli olduğunda ve yeni satırın eklenmesi ne zaman geri alınması gerektiğini izlemeniz gerekecektir. Bu işlevin tam olarak uygulanması, veri modelinin uygulamasına ve veri modelinin işlem semantiğine bağlıdır; kayıt kapsamının hücre veya satır düzeyinde olup olmadığı.  
  
 Sanal mod hakkında daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki sanal mod](virtual-mode-in-the-windows-forms-datagridview-control.md)' a bakın. Sanal mod olaylarının nasıl kullanılacağını gösteren bir örnek için, bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](implementing-virtual-mode-wf-datagridview-control.md)
