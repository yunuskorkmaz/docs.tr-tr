---
title: DataRepeater Denetiminde Sorun Giderme (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 7b045e1c45221cbde82c88286da8e698a763d844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580609"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>DataRepeater Denetiminde Sorun Giderme (Visual Studio)
Bu konu ile çalışırken oluşabilecek genel sorunları listelemektedir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater klavye ve fare olayları harekete Geçirilmemesi  
 Bazı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> klavye ve fare olayları gibi olayları çoğalmaz. Bu tasarım gereğidir. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim kendisi için bir kapsayıcıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> nesneleri ve çalışma zamanında erişilemez. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Tasarım zamanında olayı göstermiyor. Bu nedenle, bir öğeye tıklandığında veya öğenin odağa sahip olduğunda bir tuşa basarak bir olayı oluşturmaz.  
  
 Özel durum olduğunda <xref:System.Windows.Forms.Control.Padding%2A> özelliği ayarlandığında büyük bir kenarlarına kullanıma sunmak için yeterli değer <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Bu durumda, kullanıma sunulan kenar boşluğunu tıklayarak fare olayları ortaya koyar.  
  
 Bu sorunu çözmek için ekleme bir <xref:System.Windows.Forms.Panel> denetimini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> bölümünü <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek ve diğer denetimlere ekleyin <xref:System.Windows.Forms.Panel>. Ardından kod ekleyebilirsiniz <xref:System.Windows.Forms.Panel> denetimin klavye ve fare olayları için olay işleyicileri.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater kısmen bağlama Gezgin gizlenmiştir  
 İlk eklediğinizde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek için bir form ve ardından gelen verilere bağlı denetimler ekleme **veri kaynakları** penceresinde <xref:System.Windows.Forms.BindingNavigator> denetimi üst kısmındaki görünebilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Bu bilinen bir sınırlaması, **veri kaynakları** penceresi ve gibi başka denetimler de davranışını tutarlı <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 Ya da hareket edebilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> tutardan <xref:System.Windows.Forms.BindingNavigator> denetimi tasarım zamanında ya da benzeyen aşağıdaki kodu ekleyin `Load` olay işleyicisi.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Denetimlerini çalışma zamanında düzgün görüntülenmiyor  
 Bazı denetimler bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında beklendiği gibi denetim gösterilmeyebilir. Denetimlerden kopyalamak için kullanılan işlem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> her zaman tüm denetimin tüm özelliklerini belirleyemiyor. İlişkisiz bir eklerseniz, örneğin, <xref:System.Windows.Forms.ListBox> denetimi bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> tasarım zamanında denetlemek ve doldurma kendi <xref:System.Windows.Forms.ListBox.Items%2A> dizeleri, bir liste koleksiyonunu <xref:System.Windows.Forms.ListBox> çalışma zamanında boş olacaktır. Kopyalama işlemi hesaba alınamıyor olmasıdır <xref:System.Windows.Forms.ListBox.Items%2A> özelliği.  
  
 Eksik Özellikler döndürerek bunun gibi sorunları düzeltebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> varsayılan kopyalama tamamlandıktan sonra oluşan olay. Aşağıdaki örnek, onarmak gösterilmiştir <xref:System.Windows.Forms.ListBox.Items%2A> koleksiyonunu bir <xref:System.Windows.Forms.ListBox> denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> olay işleyicisi.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Seçimi sembol üst öğesi eksik  
 Değiştirdiğinizde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> özelliği öğe üst bilgisinde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi, bazı rengi seçimleri kaybolmasını seçimi sembol karşılaşabilirsiniz. Değiştirme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özellik seçimi simge kayboluyor da neden olabilir.  
  
 Seçimi simge boyutu ve rengi değiştirilemez.  
  
-   Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, bir öğe seçildiğinde seçimi simgesi görünür olmaz.  
  
-   Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.Black%2A>, seçim sembol bir Denetim seçildiğinde ve bir denetim düzenleme modundayken kalem simgesi görünür olmaz görünür olmaz.  
  
-   Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlandığında, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.  
  
 Kullanarak öğesi kendi üst bilgi ve seçim sembol sağlayabilirsiniz bir <xref:System.Windows.Forms.PictureBox> denetim ve izleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> içinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olayı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetimi düzenini değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminde öğe üstbilgilerini görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater öğelerini eklemeyi ve silmeyi devre dışı bırak](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminde veri arama](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: (Visual Studio) iki DataRepeater denetimi kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
