---
title: DataRepeater Denetiminde Sorun Giderme (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 092bbe89bb73a40dee7161f014d40a581b0ddc06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591904"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>DataRepeater Denetiminde Sorun Giderme (Visual Studio)
Bu konu ile çalışırken oluşabilecek yaygın sorunları listeler <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater klavye ve fare olayları oluşmaz  
 Bazı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim olaylarına klavye ve fare olayları oluşmaz. Bu tasarım gereğidir. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim kendisi için bir kapsayıcıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> nesneleri ve çalışma zamanında erişilemez. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Olayları tasarım zamanında kullanıma sunmuyor. Bu nedenle, bir öğeyi tıklatarak veya öğenin odağa sahip olduğunda bir tuşuna basarak bir olayı oluşturmaz.  
  
 Bunun özel durumu olduğunda <xref:System.Windows.Forms.Control.Padding%2A> özelliği ayarlanmış büyük bir kenarlarına kullanıma sunmak için yeterli değeri <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Bu durumda, sunulan kenar boşluğunda tıklatarak fare olaylarını ortaya koyar.  
  
 Bu sorunu çözmek için ekleme bir <xref:System.Windows.Forms.Panel> denetimini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> bölümünü <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek ve denetimlere kalan eklemek <xref:System.Windows.Forms.Panel>. Ardından kod ekleyebilirsiniz <xref:System.Windows.Forms.Panel> denetimin klavye ve fare olayları için olay işleyicileri.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater kısmen bağlama Gezgini gizli  
 İlk eklediğinizde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek için bir form ve veri bağlama denetimleri ekleme **veri kaynakları** penceresinde <xref:System.Windows.Forms.BindingNavigator> denetim üstünde görünebilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Bu bir bilinen kısıtlamasıdır **veri kaynakları** penceresi ve diğer denetimlerin davranışını tutarlı olduğu gibi <xref:System.Windows.Forms.DataGridView> denetim.  
  
 Her iki taşıma için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> değerinden daha düşük <xref:System.Windows.Forms.BindingNavigator> tasarım zamanında denetim veya benzeyen aşağıdaki kodu ekleyin `Load` olay işleyicisi.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Denetimleri çalışma zamanında düzgün görüntülenmiyor  
 Bazı denetimler bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında beklendiği gibi denetim gösterilmeyebilir. Denetimleri kopyalamak için kullanılan işlem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> her zaman tüm denetimler tüm özelliklerini belirleyemiyor. İlişkisiz bir eklerseniz, örneğin, <xref:System.Windows.Forms.ListBox> denetimini bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> tasarım zamanında denetim ve doldurmak kendi <xref:System.Windows.Forms.ListBox.Items%2A> dizeleri listesiyle koleksiyonu <xref:System.Windows.Forms.ListBox> çalışma zamanında boş olacaktır. Kopyalama işlemi dikkate alınamıyor olmasıdır <xref:System.Windows.Forms.ListBox.Items%2A> özelliği.  
  
 Eksik özelliklerinde geri yükleyerek bu gibi sorunları düzeltebilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> varsayılan kopyalama tamamlandıktan sonra gerçekleşen olay. Aşağıdaki örnek, onarmak gösterilmiştir <xref:System.Windows.Forms.ListBox.Items%2A> koleksiyonu bir <xref:System.Windows.Forms.ListBox> denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> olay işleyicisi.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Öğe başlığındaki seçimi simgesi eksik.  
 Değiştirdiğinizde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> öğesi üstbilgisinde özelliğinin bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim, bazı rengi seçimleri neden olabilir seçimi simge kaybolur. Değiştirme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özellik seçimi simge kayboluyor da neden olabilir.  
  
 Seçim simgesi boyutu ve rengi değiştirilemez.  
  
-   Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, bir öğe seçildiğinde seçimi simgesi görünür olmaz.  
  
-   Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.Black%2A>, seçim simgenin bir Denetim seçildiğinde ve bir denetim düzenleme modunda olduğunda kalem simgesi görünür olmaz görünür olmaz.  
  
-   Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlamak, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.  
  
 Kullanarak kendi madde üstbilgi ve seçim simgesi sağlayabilirsiniz bir <xref:System.Windows.Forms.PictureBox> denetim ve izleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> içinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olayı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimi Düzenini Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Öğe Üst Bilgilerini Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Öğelerini Eklemeyi ve Silmeyi Devre Dışı Bırakma](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Veri Arama](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
