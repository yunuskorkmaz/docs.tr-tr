---
title: "Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana / ayrıntı formu oluşturma"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02f98cce74f99d8a00bc916b38e5c290045926a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [DataRepeater denetimine giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: DataRepeater denetiminde veri bağlı](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: görüntü Windows Forms uygulamalarındaki ilgili verileri](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)  
 [Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater denetiminde sorun giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
