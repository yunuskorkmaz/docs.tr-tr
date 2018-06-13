---
title: DataRepeater Denetiminde Sanal Mod (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
ms.openlocfilehash: 7aa462f670c95f2d5996cf04b676bf09e9ec62b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592242"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater Denetiminde Sanal Mod (Visual Studio)
Tablo verileri büyük miktarlarda görüntülemek istediğinizde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi ayarlayarak performansı artırabilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğine `True` ve açıkça kendi veri kaynağı ile denetimin etkileşimi yönetme. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim veri kaynağınız ile etkileşim kurmanızı ve çalışma zamanında gerektiği gibi verileri görüntülemek için işleyebilirsiniz birkaç olay sağlar.  
  
## <a name="how-virtual-mode-works"></a>Nasıl sanal modu çalışır  
 En yaygın bir senaryo için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimidir alt denetimlerin bağlamak için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> bir veri kaynağı tasarım zamanında ve izin <xref:System.Windows.Forms.BindingSource> geri ve İleri gerektiği gibi veri iletmek için. Sanal modunu kullanırken, denetimlerin bir veri kaynağına bağlı değildir ve veri çalışma zamanında veri kaynağındaki ve geriye geçirilir.  
  
 Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliği ayarlanmış `True`, kullanıcı arabirimi denetimlerini ekleyerek oluşturma **araç** ilişkili denetimlerden eklemek yerine **veri kaynakları** penceresi.  
  
 Bir denetimi denetimi temelinde olaylar oluşturulur ve verilerin görünümünü işlemek için kod eklemeniz gerekir. Yeni bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> görünüme, kaydırılan <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> olayı her denetim için bir kez oluşturulur ve her denetim için değerleri sağlamalısınız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> olay işleyicisi.  
  
 Veri denetimleri birinde kullanıcı tarafından değiştirilirse <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> olayı oluşturulur ve veri doğrulama ve veri kaynağınıza kaydetmeniz gerekir.  
  
 Kullanıcı yeni bir öğe eklerse <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> olayı oluşturulur. Veri kaynağınıza yeni bir kayıt oluşturmak için bu olay işleyicisi kullanın. İstenmeyen değişiklikleri önlemek için de izlemeniz gereken <xref:System.Windows.Forms.Control.KeyDown> her denetim ve çağrısı için olay <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> kullanıcı ESC tuşuna basarsa.  
  
 Veri kaynağı, değiştiyse, yenileyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çağırarak denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> yöntemleri. Her iki yöntem sırayla çağrılmalıdır.  
  
 Son olarak, olay işleyicileri için uygulamanız gereken <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> bir öğe silindiğinde ve isteğe bağlı olarak oluşur olay <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> DELETE tuşuna basarak bir kullanıcı bir öğeyi siler her oluşan olaylar.  
  
## <a name="implementing-virtual-mode"></a>Sanal modu uygulama  
 Sanal mod uygulamak için gereken adımlar şunlardır.  
  
#### <a name="to-implement-virtual-mode"></a>Sanal mod uygulamak için  
  
1.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için. Ayarlama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğine `True`.  
  
2.  Sürükleme denetimlerden **araç** öğesi şablonu bölgesi (üst bölge) üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Veri kaynağınızda görüntülemek istediğiniz her bir alan için bir denetim gerekir.  
  
3.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> olay her denetim için değerler sağlayın. Bu olay yeni bir tetiklenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> görünüme kaydırılan. Adlı bir veri kaynağı için aşağıdaki örnek kod benzeyecektir `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> verileri depolamak için olay. Kullanıcı değişiklikleri alt denetimi için kaydeder. Bu olay tetiklenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Adlı bir veri kaynağı için aşağıdaki örnek kod benzeyecektir `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Her alt denetim için bir işleyici uygulamak <xref:System.Windows.Forms.Control.KeyDown> olay ve izleme ESC tuşuna. Çağrı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> önlemek için yöntemi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> gerçekleştirilen gelen olay. Aşağıdaki örnek kod benzeyecektir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> olay. Kullanıcı için yeni bir öğe ekler. Bu olay tetiklenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Adlı bir veri kaynağı için aşağıdaki örnek kod benzeyecektir `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> olay. Bu olay, varolan bir kullanıcıyı siler oluşur. Adlı bir veri kaynağı için aşağıdaki örnek kod benzeyecektir `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Denetim düzeyi doğrulama için isteğe bağlı olarak uygulamak için işleyiciler <xref:System.Windows.Forms.Control.Validating> alt denetimlerin olayları. Aşağıdaki örnek kod benzeyecektir.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
