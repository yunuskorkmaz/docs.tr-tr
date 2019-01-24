---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater denetiminin görünümünü değiştirme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716641"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Nasıl yapılır: (Visual Studio) DataRepeater denetiminin görünümünü değiştirme
Görünümünü değiştirebilirsiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim özelliklerini ayarlayarak, tasarım zamanında ya da işlem tarafından çalışma zamanında <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay.  
  
 Denetim öğesi şablon bölümü seçili olduğunda tasarım zamanında ayarlama özellikleri yinelenen her biri için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> çalışma zamanında. Görünüm ile ilgili özellikleri <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetiminin kendisinin görünmeyecektir olgunlaştıkça yalnızca şu durumlarda bir kapsayıcının bölümü sola çalışma zamanında (örneğin, <xref:System.Windows.Forms.Control.Padding%2A> özelliği, büyük bir değere ayarlanır).  
  
 Çalışma zamanında, görünüm ilgili özellikler koşullara göre ayarlanabilir. Örneğin, bir zamanlama uygulamasında, süresi geçmiş bir öğe olduğunda kullanıcıları uyarmak için bir öğe arka plan rengini değişebilir. İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi, bir özelliği bir koşullu deyimde gibi ayarlarsanız `If…Then`, de kullanmanız gerekir bir `Else` koşul karşılanmadığında görünümünü belirtmek için yan tümcesi.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Tasarım zamanında görünümünü değiştirmek için  
  
1.  Windows Form Tasarımcısı'nda öğe şablonu (üst) bölgesi seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
2.  Özellikler penceresinde, bir özellik seçin ve değeri değiştirin. Görünüm etkileyen yaygın özellikler dahil <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, ve <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Çalışma zamanında görünümünü değiştirmek için  
  
1.  Kod Düzenleyicisi'nde olay açılan listesinde, **DrawItem**.  
  
2.  İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi özelliklerini ayarlamak için kodu ekleyin:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Örnek  
 Sık karşılaşılan bazı özelleştirmeler için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi içeren satırları rengini değiştirme ve bir koşula göre bir alanın rengi değiştirme görüntüleme. Aşağıdaki örnekte şu özelleştirmeleri yapmak nasıl gösterir. Bu örnekte, sahibi olduğunuzu varsayar bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Northwind veritabanındaki ürünleri tabloya bağlı denetim.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Her iki bu özelleştirmeler için her iki tarafında bir koşul için özellikleri ayarlamak üzere kod sağlamalısınız unutmayın. Siz belirtmezseniz `Else` koşulu, çalışma zamanında beklenmeyen sonuçlar görürsünüz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminde öğe üstbilgilerini görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
