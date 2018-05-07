---
title: 'Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: 698e518a4ed10ed6cf14ccafc6833b1acf8752db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme (Visual Studio)
Bağlama denetimleri ek olarak, diğer denetimler için eklemek isteyebilirsiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>statik bir etiket veya her öğe üzerinde yinelenen bir görüntü gibi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
> [!NOTE]
>  De en az bir ilişkili denetim olmalıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> veya hiçbir şey çalışma zamanında görüntülenir.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Bir DataRepeater bağlanmamış denetimler ekleme  
  
1.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  Boyutlandırma ve konumu tanıtıcıları boyuta sürükleyin ve denetim getirin.  
  
     Ayrıca boyut ve değiştirerek denetimi Yerleştir **boyutu** ve **konumu** Özellikleri penceresinde özellikler.  
  
3.  En az bir veri bağlama denetimine ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüle](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Denetimden sürükleyin **araç** öğesi şablonu bölgesini üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
     Denetim iki dikdörtgen bölgeler olduğuna dikkat edin. İç bölgesi *öğe şablonu*; şablona eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim. Dış bölgedir *görünüm penceresinin*, burada öğeleri görüntülenir; bu bölgeye eklenen denetimlerini çalışma zamanında görüntülenmeyecek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
