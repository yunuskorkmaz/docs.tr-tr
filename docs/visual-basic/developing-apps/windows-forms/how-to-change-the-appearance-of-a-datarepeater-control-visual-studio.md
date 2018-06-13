---
title: 'Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: 9863d9343ffcecc1e4aae7f6bc16dae39ef76385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590127"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme (Visual Studio)
Görünümünü değiştirme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> özellikleri ayarlayarak tasarım zamanında veya işleme tarafından çalışma zamanında denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay.  
  
 Denetim öğesi şablon bölümünü seçildiğinde tasarım zamanında ayarlama özellikleri yinelenen her biri için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> çalışma zamanında. Görünüm ilgili özelliklerini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimin kendisini görünmeyecektir sınamayla eksikse bir kapsayıcı kısmını değişmeden çalışma zamanında (örneğin, <xref:System.Windows.Forms.Control.Padding%2A> özelliği, büyük bir değere ayarlanır).  
  
 Çalışma zamanında, görünüm ilgili özellikler koşullara göre ayarlanabilir. Örneğin, bir zamanlama uygulamasında öğeyi vadesi geçmiş olduğunda kullanıcıları uyarmak için bir öğe arka plan rengini değiştirebilirsiniz. İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> bir özelliği bir koşullu ifade gibi ayarlarsanız olay işleyicisi `If…Then`, ayrıca kullanmanız gerekir bir `Else` koşulu karşılanmadı ne zaman görünümünü belirtmek için yan tümcesi.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Tasarım zamanında görünümünü değiştirmek için  
  
1.  Windows Forms Tasarımcısı'nda öğesi şablonu (üst) bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
2.  Özellikleri penceresinde bir özellik seçin ve değeri değiştirin. Görünüm etkileyen ortak özellikler dahil <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, ve <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Çalışma zamanında görünümünü değiştirmek için  
  
1.  Kod Düzenleyicisi'nde olay açılan listesinde, **DrawItem**.  
  
2.  İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi özelliklerini ayarlamak için kodu ekleyin:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Örnek  
 Bazı yaygın özelleştirmeler için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim dahil renkleri değişen ve bir koşula göre bir alan rengi değiştirme satırları görüntüleme. Aşağıdaki örnek, bu özelleştirmeler gerçekleştirmek gösterilmektedir. Bu örnek, sahibi olduğunuzu varsayar. bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Northwind veritabanı Ürünler tablosuna bağlı denetimi.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Her iki bu özelleştirmeler için iki tarafı da koşul özelliklerini ayarlamak için kodu sağlamalısınız unutmayın. Belirtmezseniz, `Else` koşul, çalışma zamanında beklenmeyen sonuçlar görürsünüz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Öğe Üst Bilgilerini Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
