---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730795"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Nasıl yapılır: (Visual Studio) DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme
Bağlama denetimleri ek olarak, diğer denetimler eklemek isteyebileceğiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>statik etiket veya her öğesine yinelenen görüntü gibi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
> [!NOTE]
>  Ayrıca en az bir bağlantılı denetim olmalıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> veya hiçbir şey çalışma zamanında görüntülenir.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Bağlanmamış denetimler için bir DataRepeater eklemek için  
  
1.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  Boyut ve konum tutamaçları boyutuna sürükleyin ve denetimi konumlandırın.  
  
     Ayrıca boyutu ve değiştirerek denetimin konumunu **boyutu** ve **konumu** özellikleri Özellikler penceresinde.  
  
3.  En az bir veri bağlama denetimine ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Bir denetimi **araç kutusu** öğe şablonu bölgesi üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
     Denetim dikdörtgen iki bölgeleri olduğuna dikkat edin. İç bölgesi *öğe şablonu*; şablonuna eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim. Dış bölgedir *Görünüm penceresi*, burada öğeler görüntülenir; bu bölgeye eklenen denetimlerin çalışma zamanında görüntülenmeyecek.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: (Visual Studio) iki DataRepeater denetimi kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
