---
title: 'Nasıl Yapılır: DataRepeater Denetiminde Veri Arama (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 689990ee125c85c3151a4e965b619fde068d220e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetiminde Veri Arama (Visual Studio)
Kullanırken bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> belirli bir kayıt let kullanıcıları aramak istediğiniz çok sayıda kayıt içeren denetimi. Denetiminde veri arama yerine, bir arama arka plandaki sorgulayarak uygulayabileceğiniz <xref:System.Windows.Forms.BindingSource>. Öğe bulunursa, daha sonra kullanabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> özelliğini öğeyi seçin ve görünümüne gidin.  
  
### <a name="to-implement-search"></a>Arama uygulamak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> gelen denetim **araç** içeren forma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
2.  Özellikler penceresinde değiştirin **adı** özelliğine **SearchTextBox**.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içeren forma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
4.  Özellikler penceresinde değiştirin **adı** özelliğine **SearchButton**. Değişiklik **metin** özelliğine **arama**.  
  
5.  Çift <xref:System.Windows.Forms.Button> Kod Düzenleyicisi'ni açmak için Denetim ve aşağıdaki kodu ekleyin `SearchButton_Click` olay işleyicisi.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Değiştir *ProductsBindingSource* adıyla <xref:System.Windows.Forms.BindingSource> için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>ve Değiştir *ProductID* aramak istediğiniz alanın adı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
