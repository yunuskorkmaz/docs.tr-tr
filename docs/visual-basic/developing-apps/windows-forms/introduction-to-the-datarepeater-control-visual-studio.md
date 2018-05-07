---
title: DataRepeater Denetimine Giriş (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater Denetimine Giriş (Visual Studio)
Visual Basic Power Packs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimidir kaydırılabilir bir kapsayıcı verileri, örneğin, bir veritabanı tablosundaki satırları görüntüleyen denetimler yinelenen için. Alternatif olarak kullanılabilir <xref:System.Windows.Forms.DataGridView> veri düzeni üzerinde daha fazla denetim gerektiğinde denetim. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "İlgili denetimleri bir grup kayan bir görünümde birden çok örneği oluşturarak yineler". Bu, aynı anda birden fazla kayıtları görüntülemek kullanıcılar sağlar.  
  
## <a name="overview"></a>Genel Bakış  
 Tasarım zamanında <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi iki bölümden oluşur. Dış bölüm *görünüm penceresinin*, çalışma zamanında kayan veri burada görüntülenir. Olarak bilinen iç (üst) bölümünde, *öğe şablonu*, çalışma zamanında veri kaynağındaki her bir alan için genellikle bir denetim yinelenen denetimleri konumlandırmak nerede olduğunu. İçinde özellikler ve öğe şablonu denetimlerinde kapsüllenmiş <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> özelliği.  
  
 Çalışma zamanında <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> sanal bir kopyalanır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> her kayıt görünüme kaydırılan verileri görüntülemek için kullanılan nesne. Tek tek kayıtları görünümünü özelleştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay, örneğin, içerdiği değere göre bir alan vurgulama. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 En yaygın kullanımı bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimidir bir veritabanı tablosu veya diğer bağlı veri kaynağından verileri görüntülemek için. Ek olarak [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri nesneleri <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimini uygulayan herhangi bir sınıf bağlama <xref:System.Collections.IList> (diziler dahil) arabirimi, uygulayan herhangi bir sınıf <xref:System.ComponentModel.IListSource> arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingList> arabirim veya uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingListView> arabirimi.  
  
### <a name="data-binding"></a>Veri Bağlama  
 Genellikle, alanlardan sürükleyerek veri bağlama gerçekleştirmek **veri kaynakları** penceresi üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüle](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Büyük miktarlarda veri ile çalışırken, ayarlayabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğine `True` kullanılabilir verilerin bir alt kümesini görüntülemek için. Sanal mod gerektiren bir veri önbelleğinden uyarlamasını <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> doldurulur, ve tüm etkileşimleri veri önbelleği ile çalışma zamanında denetim. Daha fazla bilgi için bkz: [DataRepeater denetiminde sanal mod](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Üzerinde ilişkisiz denetimleri görüntüleyebilirsiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Örneğin, her bir öğede yinelenen bir görüntü görüntüleyebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Olaylar  
 En önemli olayları <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> yeni öğeler görünüme kaydırılan bağlandığınızda tetiklenir, olay ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> bir öğe seçildiğinde oluşan olayı,. Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> öğenin görünümünü değiştirmek için olay. Örneğin, negatif değerler vurgulayın. Kullanım <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> bir öğe seçildiğinde, denetimlerinin değerlerini erişmek için olay.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim tüm standart denetim olaylarını Kod Düzenleyicisi'nde kullanıma sunar. Ancak, bazı olaylar kullanılmamalıdır. Klavye ve olayları gibi fare `KeyDown`, `Click`, ve `MouseDown` çalışma zamanında oluşturulmaz, çünkü <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi kendisini hiçbir zaman odağa.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Yalnızca çalışma zamanında oluşturduğundan olayları tasarım zamanında kullanıma sunmuyor. Ekleyebileceğiniz klavye ve fare olayları işlemek istiyorsanız, bir <xref:System.Windows.Forms.Panel> denetimini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> adresindeki tasarım zamanı ve olayları işlemek <xref:System.Windows.Forms.Panel>. Daha fazla bilgi için bkz: [DataRepeater denetiminde sorun giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Özelleştirmeleri  
 Görünümünü ve davranışını özelleştirmek için birçok yolu vardır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek, hem çalışma zamanında hem tasarım zamanında. Özellikler ayarlanabilir renkleri değiştirmek, Gizle veya öğe üstbilgilerini değiştirmek, dikey yatay olarak ve çok daha fazlasını yönünü değiştirin. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [nasıl yapılır: DataRepeater denetiminde öğe üstbilgilerini görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), ve [nasıl yapılır: düzenini değiştirme bir DataRepeater denetimi](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Bazı özellikler geçerli Not <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> bazılar yalnızca geçerli ise denetimi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Doğru bölümünü denetimi özellikleri ayarlamadan önce seçili olduğundan emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Diğer özelleştirmeleri ekleme veya kayıt silme olanağı denetleme, arama yetenekleri ekleme ve bir ana ve ayrıntı biçiminde ilgili verileri görüntüleme içerir. Daha fazla bilgi için bkz: [nasıl yapılır: devre dışı ekleme ve silme DataRepeater öğelerini](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [nasıl yapılır: DataRepeater denetiminde veri arama](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), ve [nasıl yapılır: kullanarak iki tarafından ana/ayrıntı formu oluşturma DataRepeater denetimi (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataRepeater Denetimi](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [İzlenecek Yol: DataRepeater Denetimindeki Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
