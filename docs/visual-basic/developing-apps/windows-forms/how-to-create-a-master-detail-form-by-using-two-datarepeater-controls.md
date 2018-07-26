---
title: 'Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak bir ana öğe-ayrıntı formu oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245549"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Nasıl Yapılır: İki DataRepeater Denetimi Kullanarak Ana Öğe/Ayrıntı Formu Oluşturma (Visual Studio)
İki veya daha fazla kullanarak, ilgili verileri görüntüleyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimleri ana/ayrıntı formu oluşturma. Örneğin, bir müşteri listesini görüntülemek isteyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>ve kullanıcı bir müşteri seçtiğinde, bir saniye içinde bu müşterinin siparişlerinin listesi görüntüleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Aynı ana tablo düğümünden paylaşma ayrıntı öğeleri sürükleyerek, ilgili verileri görüntüleyebilirsiniz **veri kaynakları** penceresinden bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Müşteriler tablosu ve ilgili Siparişler tablosundan sahip bir veri kaynağı varsa, örneğin, her iki tablonun en üst düzey düğümlerin ağaç görünümünde olarak gördüğünüz **veri kaynakları** penceresi. Sütunları görebilmeniz için müşterilerin düğümünü genişletin. Orders tablosunu temsil eden bir Genişletilebilir düğümü listedeki son sütun olduğuna dikkat edin. Bu düğüm, bir müşterinin ilgili siparişlerini temsil eder.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>İçinde iki DataRepeater denetimi ile ilgili verileri görüntülemek için  
  
1.  İki <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimler **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  Denetimleri ve bunları yan yana konumlandırmak için boyut ve konum tutamaçları sürükleyin.  
  
3.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
    > [!NOTE]
    >  Varsa **veri kaynakları** penceresi boş ise, bir veri kaynağı ekleyin. Daha fazla bilgi için [yeni veri kaynağı ekleme](/visualstudio/data-tools/add-new-data-sources).  
  
4.  İçinde **veri kaynakları** penceresinde ana tablo için üst düzey düğümü seçin.  
  
5.  Ana Tablo bırakma türünü tıklayarak Ayrıntılar olarak değiştirin. **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
6.  Ana Tablo düğümü ilk öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
7.  Ana Tablo düğümünü genişletin ve ilişkili tablo ayrıntı düğümünü seçin.  
  
8.  Ayrıntı tablosunu bırakma türünü tıklayarak Ayrıntılar olarak değiştirin. **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
9. Bu tablo düğümünü seçin ve ikinci öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: görüntü ilgili verileri bir Windows Forms uygulaması](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
