---
title: 'Nasıl Yapılır: DataRepeater Denetimi Düzenini Değiştirme (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590848"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetimi Düzenini Değiştirme (Visual Studio)
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim görüntülenebilir bir (öğelerini kaydırma dikey) dikey veya yatay (öğelerini kaydırma yatay) yönlendirmesi. Tasarım zamanında veya çalışma zamanında yönlendirmesini değiştirerek değiştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği. Değiştirirseniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği çalışma zamanında de isteyebilirsiniz yeniden boyutlandırmak <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> ve alt denetimleri yeniden konumlandırmak.  
  
> [!NOTE]
>  Üzerinde denetimleri yeniden konumlandırmak varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> çalışma zamanında çağırmanız gerekir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> başına ve denetimleri yeniden konumlandırır kod bloğunun sonundaki yöntemleri.  
  
### <a name="to-change-the-layout-at-design-time"></a>Tasarım zamanında düzenini değiştirmek için  
  
1.  Windows Forms Tasarımcısı'nda seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
    > [!NOTE]
    >  Dış kenarlığı seçmelisiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> değil, üst denetimin alt bölgede tıklatarak denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> bölge.  
  
2.  Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> ya da özellik <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> veya <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.  
  
### <a name="to-change-the-layout-at-run-time"></a>Çalışma zamanında düzenini değiştirmek için  
  
1.  Aşağıdaki kod bir düğme veya menü ekleme `Click` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Çoğu durumda, kodu yeniden boyutlandırmak için örnek bölümünde gösterilen benzer eklemek istersiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> ve denetimleri yeni yönlendirmesini sığacak şekilde yeniden düzenleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yanıt gösterilmektedir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> olayı olay işleyicisi. Bu örnek sahip olmasını gerektiren bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> adlı Denetim `DataRepeater1` form ve, kendi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> iki içeren <xref:System.Windows.Forms.TextBox> adlı denetimleri `TextBox1` ve `TextBox2`.  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
