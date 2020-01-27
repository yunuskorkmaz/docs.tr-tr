---
title: Tasarımcı kullanarak DataGridView denetiminde satır eklemeyi ve silmeyi engelleme
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cc9aff0f15d1bd6de5c469ee7069a99f3360837a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728712"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme
Bazen, kullanıcıların <xref:System.Windows.Forms.DataGridView> denetiinizden yeni veri satırları girmesini veya mevcut satırları silmelerini engellemek isteyebilirsiniz. Yeni satırlar, denetimin alt kısmındaki Yeni kayıtlar için özel satıra girilir. Satır eklemeyi devre dışı bıraktığınızda, yeni kayıtlar için satır görüntülenmez. Daha sonra satır silme ve hücre düzenlemesini devre dışı bırakarak denetimi tamamen Salt okunabilir hale getirebilirsiniz.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Satır ekleme ve silmeyi engellemek için

- <xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesindeki akıllı etiket glifi ' ne (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve sonra silmeyi **eklemeyi** ve **silmeyi** etkinleştir onay kutularını temizleyin.

    > [!NOTE]
    > Denetimi tamamen Salt okunabilir hale getirmek için, **düzenlemeleri etkinleştir** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
