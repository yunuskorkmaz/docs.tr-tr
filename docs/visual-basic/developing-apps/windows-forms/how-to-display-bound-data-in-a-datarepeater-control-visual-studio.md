---
title: 'Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: b96fb33a0dcf80a86d1fcb6e219e5f35b1f7351c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme (Visual Studio)
En yaygın kullanımı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimidir bir veritabanı veya başka bir veri kaynağını ilişkili verileri görüntülemek için.  
  
 Bağlama denetimleri ek olarak, statik bir etiket veya her öğe üzerinde yinelenen bir görüntü gibi diğer denetimleri eklemek isteyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Ayarlayarak çalışma zamanında bir veri kaynağına bağlayabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğine `True` ve bir veri kaynağına atama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> özelliği. Bu durumda, veri kaynağı ile tüm etkileşimi yönetmek gerekir. Daha fazla bilgi için bkz: [DataRepeater denetiminde sanal mod](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Veri bağlama DataRepeater oluşturmak için  
  
1.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  Boyutlandırma ve konumu tanıtıcıları boyuta sürükleyin ve denetim getirin.  
  
     Denetim iki dikdörtgen bölgeler olduğuna dikkat edin. Üst bölge *öğe şablonu*; şablona eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim. Alt bölge *görünüm penceresinin*, öğeleri burada görüntülenir.  
  
     Ayrıca boyut ve denetim veya öğe şablonu değiştirerek Yerleştir **boyutu** ve **konumu** Özellikleri penceresinde özellikler.  
  
3.  Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster**.  
  
    > [!NOTE]
    >  Varsa **veri kaynakları** penceresi boşsa, bir veri kaynağı ekleyin. Daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources).  
  
4.  İçinde **veri kaynakları** penceresi, üst düzey düğüm bağlamak istediğiniz verileri içeren bir tablo için seçin.  
  
5.  Tabloya açılan türünü değiştirme `Details` tıklayarak `Details` Tablo düğümü aşağı açılan listesinde.  
  
6.  Tablo düğümü seçin ve Madde şablonu bölgesini sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
     Hangi tür denetimler için her bir alan görüntülenen belirtebilirsiniz. Daha fazla bilgi için bkz: [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimini ayarlama](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
