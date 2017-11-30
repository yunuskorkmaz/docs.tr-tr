---
title: "Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [DataRepeater denetimine giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater denetiminde sorun giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: DataRepeater denetiminde veri bağlı](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
