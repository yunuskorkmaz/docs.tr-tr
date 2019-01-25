---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater denetiminde veri arama'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 514e72afc9570071f57e385574456ff7d716bad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654392"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Nasıl yapılır: (Visual Studio) DataRepeater denetiminde veri arama
Kullanırken bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> belirli bir kaydın arama isteyebileceğiniz birçok kayıtları içeren denetimi. Denetiminde veri arama yerine, bir arama temel alınan sorgulayarak uygulayabileceğiniz <xref:System.Windows.Forms.BindingSource>. Öğe bulunursa, ardından kullanabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> özellik öğe seçip görünümüne gidin.  
  
### <a name="to-implement-search"></a>Arama uygulamak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> denetimi **araç kutusu** içeren form üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
2.  Özellikler penceresinde değişiklik **adı** özelliğini **SearchTextBox**.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içeren form üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
4.  Özellikler penceresinde değişiklik **adı** özelliğini **SearchButton**. Değişiklik **metin** özelliğini **arama**.  
  
5.  Çift <xref:System.Windows.Forms.Button> Kod Düzenleyicisi'ni açmak için Denetim ve aşağıdaki kodu ekleyin `SearchButton_Click` olay işleyicisi.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Değiştirin *ProductsBindingSource* adıyla <xref:System.Windows.Forms.BindingSource> için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, değiştirin *ProductID* arama yapmak istediğiniz alanın adı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
