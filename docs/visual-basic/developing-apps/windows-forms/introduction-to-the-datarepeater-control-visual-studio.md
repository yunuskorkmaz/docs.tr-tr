---
title: DataRepeater Denetimine Giriş (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: c9d95f41e9857d70e81cafc94e5e3bffd4cbc3d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580713"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater Denetimine Giriş (Visual Studio)
Visual Basic Power Packs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi, kaydırılabilir bir kapsayıcı için veri, örneğin, bir veritabanı tablosundaki satırları görüntüleyen denetimler yinelenir. Alternatif olarak kullanılabilir <xref:System.Windows.Forms.DataGridView> ne zaman veri yerleşimini üzerinde daha fazla denetime ihtiyacınız denetim. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "Kayan bir görünümde birden çok örneği oluşturarak bir ilgili denetimlerin grubunu yineler". Bu, kullanıcıların aynı anda birkaç kayıt görüntülemesine olanak sağlar.  
  
## <a name="overview"></a>Genel Bakış  
 Tasarım zamanında <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi iki bölümden oluşur. Dış bölümü *Görünüm penceresi*kaydırma verileri çalışma zamanında burada görüntülenir. Olarak bilinen iç (üst) bölümünde *öğe şablonu*, çalışma zamanında veri kaynağındaki her bir alan için genellikle bir denetimin yinelenen denetimleri konumlandırma nerede olduğunu. Öğe şablonu denetimler ve özellikleri, kapsüllenmiş <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> özelliği.  
  
 Çalışma zamanında <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> sanal bir kopyalanır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> her kaydı görünüme kaydırılan verileri görüntülemek için kullanılan nesne. Bireysel kayıtlar görünümünü özelleştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay, örneğin, içerdiği değerine göre bir alanı vurgulama. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 En yaygın kullanımı bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> bir veritabanı tablosu veya diğer bağlı veri kaynağından verileri görüntülemek için denetimidir. Ek olarak [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri nesneleri <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimini uygulayan herhangi bir sınıf için bağlama <xref:System.Collections.IList> (diziler de dahil olmak üzere) arabirimi, uygulayan sınıf <xref:System.ComponentModel.IListSource> arabirimi uygulayan sınıf <xref:System.ComponentModel.IBindingList> arabirim veya uygulayan sınıf <xref:System.ComponentModel.IBindingListView> arabirimi.  
  
### <a name="data-binding"></a>Veri Bağlama  
 Genellikle, alanları sürükleyerek veri bağlama gerçekleştirmek **veri kaynakları** penceresinden <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Büyük miktarlarda veri ile çalışırken, ayarlayabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğini `True` kullanılabilir verilerin bir alt kümesini görüntülemek için. Sanal mod, bir veri önbelleğinden uygulanmasını gerektirir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> doldurulur ve çalışma zamanında veri önbelleği ile tüm etkileşimler denetleyin. Daha fazla bilgi için [DataRepeater denetiminde sanal mod](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Bağlanmamış denetimler üzerinde görüntüleyebilirsiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Örneğin, her bir öğede yinelenen görüntü görüntüleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminde denetimleri ilişkisiz](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Olaylar  
 En önemli olayları <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> yeni öğeler görünüme kaydırılan gerçekleşmek üzereyken, olay ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> bir öğe seçildiğinde gerçekleşmek üzereyken olay. Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> öğesi görünümünü değiştirmek için olay. Örneğin, negatif değerler vurgulayabilirsiniz. Kullanım <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> bir öğe seçildiğinde, denetim değerlerinin erişmek için olay.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetimi tüm standart denetim olayları Kod Düzenleyicisi'nde kullanıma sunar. Ancak, bazı olaylar kullanılmamalıdır. Klavye ve olaylar gibi fare `KeyDown`, `Click`, ve `MouseDown` çalışma zamanında oluşturulmaz, çünkü <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetiminin kendisine hiçbir zaman odağa.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Yalnızca çalışma zamanında oluşturulduğundan tasarım zamanında olayı göstermiyor. Ekleyebileceğiniz klavye ve fare olayları işlemek istiyorsanız, bir <xref:System.Windows.Forms.Panel> denetimini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> , tasarım zamanı ve ardından olayları işlemek <xref:System.Windows.Forms.Panel>. Daha fazla bilgi için [DataRepeater denetiminde sorun giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Özelleştirmeleri  
 Görünümünü ve davranışını özelleştirmek için birçok yol vardır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek, çalışma zamanında hem tasarım zamanında. Özellikleri ayarlanabilir renkleri değiştirebilir, gizleme veya öğe üst bilgilerini değiştirme, yatay, dikey ve daha pek çok yönünü değiştirme. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [nasıl yapılır: DataRepeater denetiminde öğe üstbilgilerini görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), ve [nasıl yapılır: DataRepeater denetimi düzenini değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Bazı özellikler geçerli Not <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> diğerleri yalnızca geçerli ise denetiminin kendisini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Doğru bölümünü denetimi özellikleri ayarlanmadan önce seçili olduğundan emin olun. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Diğer özelleştirmeleri ekleme veya kayıt silme olanağı denetleme, arama yetenekleri ekleme ve bir ana ve ayrıntılı biçimde ilgili verileri görüntüleme içerir. Daha fazla bilgi için [nasıl yapılır: DataRepeater öğelerini eklemeyi ve silmeyi devre dışı](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [nasıl yapılır: DataRepeater denetiminde veri arama](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), ve [nasıl yapılır: (Visual Studio) iki DataRepeater denetimi kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataRepeater Denetimi](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)
- [İzlenecek yol: DataRepeater denetimindeki verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)
- [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
