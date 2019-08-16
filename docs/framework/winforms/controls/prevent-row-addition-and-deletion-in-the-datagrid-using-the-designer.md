---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038197"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme
Bazen kullanıcıların yeni veri satırlarını girmesini veya denetiinizdeki <xref:System.Windows.Forms.DataGridView> mevcut satırları silmelerini engellemek isteyeceksiniz. Yeni satırlar, denetimin alt kısmındaki Yeni kayıtlar için özel satıra girilir. Satır eklemeyi devre dışı bıraktığınızda, yeni kayıtlar için satır görüntülenmez. Daha sonra satır silme ve hücre düzenlemesini devre dışı bırakarak denetimi tamamen Salt okunabilir hale getirebilirsiniz.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

## <a name="to-prevent-row-addition-and-deletion"></a>Satır ekleme ve silmeyi engellemek için

- <xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve sonra silmeyi **eklemeyi** ve **silmeyi** etkinleştir onay kutularını temizleyin.

    > [!NOTE]
    >  Denetimi tamamen Salt okunabilir hale getirmek için, **düzenlemeleri etkinleştir** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
