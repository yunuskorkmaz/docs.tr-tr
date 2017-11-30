---
title: "Nasıl Yapılır: DataRepeater Öğelerini Eklemeyi ve Silmeyi Devre Dışı Bırakma (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b15fe6fb5190855126ffa60ac488aaa74ad9b5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Nasıl Yapılır: DataRepeater Öğelerini Eklemeyi ve Silmeyi Devre Dışı Bırakma (Visual Studio)
Varsayılan olarak, kullanıcılar ekleyebilir ve öğeleri silmek bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Kullanıcılar, CTRL + N tuşlarına basarak yeni bir öğe ekleyebilirsiniz olduğunda bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> odağa sahip veya tıklayarak **AddNew-Item** düğmesini <xref:System.Windows.Forms.BindingNavigator> denetim. Kullanıcıları, bir öğe tuşlarına basarak silebilir ne zaman silmek bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> odağa sahip veya tıklayarak **DeleteItem** düğmesini <xref:System.Windows.Forms.BindingNavigator> denetim.  
  
 Ekleme ve/veya tasarım zamanında veya çalışma zamanında silme devre dışı bırakabilirsiniz.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Eklemeyi ve tasarım zamanında silmeyi devre dışı bırakmak için  
  
1.  Windows Forms Tasarımcısı'nda seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
    > [!NOTE]
    >  Denetim alt bölümünü seçmeniz gerekir. Öğesi şablonu bölümüne seçerseniz, farklı bir özellikler kümesi görüntülenir.  
  
2.  Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> özelliğine **False**.  
  
3.  Ayarlama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> özelliğine **False**.  
  
4.  Windows Forms Tasarımcısı'nda seçin <xref:System.Windows.Forms.BindingNavigator> denetlemek ve ardından **AddNew-Item** düğmesini (düğmesi üzerindeki bir artı işareti olan).  
  
5.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğine **False**.  
  
6.  Windows Forms Tasarımcısı'nda seçin <xref:System.Windows.Forms.BindingNavigator> denetlemek ve ardından **DeleteItem** düğmesini (düğmesi, kırmızı bir X ile).  
  
7.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğine **False**.  
  
8.  Bileşen tepsisinde seçin <xref:System.Windows.Forms.BindingSource> hangi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> bağlıdır.  
  
9. Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.BindingSource.AllowNew%2A> özelliğine **False**.  
  
10. Windows Forms Tasarımcısı'nda çift **DeleteItem** düğmesi kod düzenleyicisini açın.  
  
11. Olayları aşağı açılan listesinde seçin `BindingNavigatorDeleteItem_EnabledChanged` olay.  
  
12. Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesini geçerli kayıt değişiklikleri her zaman.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Ekleme ve çalışma zamanında silme devre dışı bırakmak için  
  
1.  Windows Forms Tasarımcısı'nda formun Kod Düzenleyicisi'ni açmak için çift tıklayın.  
  
2.  Aşağıdaki kodu ekleyin `Form_Load` olay:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesini geçerli kayıt değişiklikleri her zaman.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater denetimine giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater denetiminde sorun giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
