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
ms.openlocfilehash: 3988c16746606de9f20f9a66b87539b6cea04758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700812"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater Denetiminde Sanal Mod (Visual Studio)
Büyük miktarlarda içindeki tablosal verileri görüntülemek istediğinizde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi ayarlayarak performansını iyileştirebilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğini `True` ve açıkça kendi veri kaynağı denetimin etkileşim yönetme. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim veri kaynağınızla etkileşim kuran ve çalışma zamanında gerektiğinde verileri görüntülemek için işleyebilir çeşitli olayları sağlar.  
  
## <a name="how-virtual-mode-works"></a>Nasıl sanal modu çalışır  
 En yaygın senaryo için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimidir, alt denetimlerini bağlamak için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> bir veri kaynağı tasarım zamanında ve izin <xref:System.Windows.Forms.BindingSource> kazandırdığından gerektiği şekilde veri aktarmak için. Sanal modunu kullanırken, denetimleri bir veri kaynağına bağlı olmayan ve verileri çalışma zamanında temel alınan veri kaynağına ve geriye geçirilir.  
  
 Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliği `True`, denetimleri ekleyerek kullanıcı arabirimi oluşturma **araç kutusu** ilişkili denetimleri eklemek yerine **veri kaynakları** penceresi.  
  
 Olaylar denetimi tarafından denetimi olarak oluşturulur ve veri görüntüsünü işlemek için kod eklemeniz gerekir. Yeni bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> görünüme kaydırılan <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> olayı her denetim için bir kez oluşturulur ve her bir denetimde değerlerini sağlamalısınız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> olay işleyicisi.  
  
 Denetimleri birindeki verileri kullanıcı tarafından değiştirilirse <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> olayı tetiklenir ve verileri doğrulama ve veri kaynağınıza kaydetmeniz gerekir.  
  
 Kullanıcı yeni bir öğe eklerse <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> olayı oluşturulur. Bu olay işleyicisi, veri kaynağınıza yeni bir kayıt oluşturmak için kullanın. İstenmeden yapılmış olabilecek değişiklikleri önlemek için de izlemeniz gereken <xref:System.Windows.Forms.Control.KeyDown> olay her denetimi ve arama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> kullanıcı ESC tuşuna bastığında.  
  
 Veri kaynağı, yenileyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çağırarak denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> yöntemleri. Sırayla her iki yöntem çağrılmalıdır.  
  
 Son olarak, için olay işleyicileri uygulamalıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> bir öğe silindiğinde ve isteğe bağlı olarak için gerçekleşen olay <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> DELETE tuşuna basarak bir kullanıcı bir öğeyi siler zaman oluşan olaylar.  
  
## <a name="implementing-virtual-mode"></a>Sanal modu uygulama  
 Sanal mod uygulamak için gereken adımlar aşağıda verilmiştir.  
  
#### <a name="to-implement-virtual-mode"></a>Sanal modu uygulama  
  
1.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için. Ayarlama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğini `True`.  
  
2.  Sürükleyin denetimlerden **araç kutusu** öğe şablonu bölgesi (üst bölge) üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Veri kaynağınızdaki görüntülemek istediğiniz her bir alan için bir denetim gerekir.  
  
3.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> olayı her denetim için değerler sağlayın. Bu olay, yeni bir tetiklenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> görünüme kaydırılan. Adlı bir veri kaynağı için aşağıdaki örnek, kod andıracaktır `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> olay verileri depolamak için. Kullanıcı için bir alt denetimin değişiklikleri kaydeder. Bu olay tetiklenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Adlı bir veri kaynağı için aşağıdaki örnek, kod andıracaktır `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Her bir alt denetimin için bir işleyici uygulamak <xref:System.Windows.Forms.Control.KeyDown> olay ve ESC tuşuna İzleyici. Çağrı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> önlemek için yöntemi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> gerçekleştirilen gelen olay. Kod, aşağıdaki örneğe benzer.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> olay. Kullanıcı için yeni bir öğe eklediğinde, bu olay tetiklenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Adlı bir veri kaynağı için aşağıdaki örnek, kod andıracaktır `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Uygulama için bir işleyici <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> olay. Bu olay, var olan bir öğeye bir kullanıcıyı siler oluşur. Adlı bir veri kaynağı için aşağıdaki örnek, kod andıracaktır `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Denetim düzeyi doğrulamasını işleyicileri için isteğe bağlı olarak uygulama <xref:System.Windows.Forms.Control.Validating> alt denetimlerin olaylarını. Kod, aşağıdaki örneğe benzer.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
