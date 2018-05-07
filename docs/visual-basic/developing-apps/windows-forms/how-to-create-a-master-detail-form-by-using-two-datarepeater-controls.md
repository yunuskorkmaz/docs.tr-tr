---
title: 'Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana / ayrıntı formu oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Nasıl Yapılır: İki DataRepeater Denetimi Kullanarak Ana Öğe/Ayrıntı Formu Oluşturma (Visual Studio)
İki veya daha fazla kullanarak ilgili verileri görüntüleyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimleri ana/ayrıntı formu oluşturma. Örneğin, müşterilerin listesini birinde görüntülemek isteyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>ve kullanıcı bir müşteri seçtiğinde, ikinci bir müşterinin siparişleri listesini görüntülemek <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Aynı ana tablo düğümünden paylaşma ayrıntı öğeleri sürükleyerek ilgili verileri görüntüleyebilir **veri kaynakları** penceresi üzerine bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Müşteriler tablosu ile ilişkili bir sipariş tabloda sahip bir veri kaynağı varsa, örneğin, her iki tabloyu ağaç görünümünde üst düzey düğüm şeklinde gördüğünüz **veri kaynakları** penceresi. Sütunları görebilmeniz için müşteriler düğümünü genişletin. Listedeki son sütunun Siparişler tablosundaki temsil eden bir Genişletilebilir düğümü olduğuna dikkat edin. Bu düğüm, bir müşteri için ilgili siparişleri temsil eder.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>İçinde iki DataRepeater denetimi ilgili verileri görüntülemek için  
  
1.  İki <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetimleri **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  Denetimleri boyut ve yan yana konumlandırmak için boyutlandırma ve konumu tanıtıcıları sürükleyin.  
  
3.  Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster**.  
  
    > [!NOTE]
    >  Varsa **veri kaynakları** penceresi boşsa, bir veri kaynağı ekleyin. Daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources).  
  
4.  İçinde **veri kaynakları** penceresi, üst düzey düğüm için ana tablo seçin.  
  
5.  Tıklatarak ana tablo bırakma türü için ayrıntıları değiştirin **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
6.  Ana Tablo düğümü ilk öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
7.  Ana Tablo düğümünü genişletin ve ilişkili tablo ayrıntı düğümünü seçin.  
  
8.  Tıklayarak ayrıntıları ayrıntı tablosunu açılan türünü değiştirme **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
9. Bu tablo düğümü seçin ve ikinci öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: görüntü Windows Forms uygulamalarındaki ilgili verileri](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
