---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater öğelerini eklemeyi ve silmeyi devre dışı bırak'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: 3a304132d0514da4c19811be2536c9516e2838f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618548"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Nasıl yapılır: (Visual Studio) DataRepeater öğelerini eklemeyi ve silmeyi devre dışı bırak
Varsayılan olarak, kullanıcılar ekleyebilir ve öğeleri silmek bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Kullanıcılar, CTRL + N tuşlarına basarak yeni bir öğe ekleyebilir, bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tıklayabilir veya odaklı **AddNew-Item** düğmesini <xref:System.Windows.Forms.BindingNavigator> denetimi. Kullanıcılar, bir öğe tuşlarına basarak silebilirsiniz SİLİNECEĞİNİ bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tıklayabilir veya odaklı **DeleteItem** düğmesini <xref:System.Windows.Forms.BindingNavigator> denetimi.  
  
 Ekleme ve/veya tasarım zamanında veya çalışma zamanında silmek, devre dışı bırakabilirsiniz.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Ekleme ve silme tasarım zamanında devre dışı bırakmak için  
  
1.  Windows Form Tasarımcısı'nda seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
    > [!NOTE]
    >  Denetimi alt bölümünü seçmeniz gerekir. Farklı bir özellikler kümesini öğesi şablon bölümü seçtiğinizde görüntülenir.  
  
2.  Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> özelliğini **False**.  
  
3.  Ayarlama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> özelliğini **False**.  
  
4.  Windows Form Tasarımcısı'nda seçin <xref:System.Windows.Forms.BindingNavigator> denetlemek ve ardından **AddNew-Item** düğme (düğme, bir artı işareti ile).  
  
5.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini **False**.  
  
6.  Windows Form Tasarımcısı'nda seçin <xref:System.Windows.Forms.BindingNavigator> denetlemek ve ardından **DeleteItem** düğme (düğme, kırmızı bir X ile).  
  
7.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini **False**.  
  
8.  Bileşen tepsisinde seçin <xref:System.Windows.Forms.BindingSource> hangi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> bağlıdır.  
  
9. Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.BindingSource.AllowNew%2A> özelliğini **False**.  
  
10. Windows Form Tasarımcısı'nda çift **DeleteItem** düğmesine Kod Düzenleyicisi'ni açın.  
  
11. Olayları aşağı açılan listesinde seçin `BindingNavigatorDeleteItem_EnabledChanged` olay.  
  
12. Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesi geçerli kayıtta değişiklikleri her zaman.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Ekleme ve silme çalışma zamanında devre dışı bırakmak için  
  
1.  Windows Form Tasarımcısı'nda, formun Kod Düzenleyicisi'ni açmak için çift tıklayın.  
  
2.  Aşağıdaki kodu ekleyin `Form_Load` olay:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesi geçerli kayıtta değişiklikleri her zaman.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
