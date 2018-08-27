---
title: 'Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: b96fb33a0dcf80a86d1fcb6e219e5f35b1f7351c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933412"
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme (Visual Studio)
En yaygın kullanımı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> bir veritabanı veya başka bir veri kaynağı ilişkili verileri görüntülemek için denetimidir.  
  
 Bağlama denetimleri ek olarak, statik bir etiket ya da her öğesine yinelenen görüntü gibi başka denetimler eklemek isteyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Daha fazla bilgi için [nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Ayarlayarak çalışma zamanında bir veri kaynağına bağlayabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğini `True` ve bir veri kaynağına atama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> özelliği. Bu durumda, tüm etkileşimi veri kaynağı ile yönetmek gerekir. Daha fazla bilgi için [DataRepeater denetiminde sanal mod](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Verilere bağlı DataRepeater oluşturmak için  
  
1.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  Boyut ve konum tutamaçları boyutuna sürükleyin ve denetimi konumlandırın.  
  
     Denetim dikdörtgen iki bölgeleri olduğuna dikkat edin. Üst bölgenin *öğe şablonu*; şablonuna eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim. Alt bölgenin *Görünüm penceresi*öğeleri burada görüntülenir.  
  
     Ayrıca boyutu ve denetimi veya öğe şablonu değiştirerek konumunu **boyutu** ve **konumu** özellikleri Özellikler penceresinde.  
  
3.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
    > [!NOTE]
    >  Varsa **veri kaynakları** penceresi boş ise, bir veri kaynağı ekleyin. Daha fazla bilgi için [yeni veri kaynağı ekleme](/visualstudio/data-tools/add-new-data-sources).  
  
4.  İçinde **veri kaynakları** penceresinde bağlamak istediğiniz verileri içeren bir tablo için üst düzey düğümü seçin.  
  
5.  Tabloya bırakma türünü değiştirme `Details` tıklayarak `Details` Tablo düğümü aşağı açılan listesinde.  
  
6.  Tablo düğümü seçin ve öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
     Tür denetimler her alan için görüntülenen belirtebilirsiniz. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
