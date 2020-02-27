---
title: Tasarımcı kullanarak DataGridView denetiminde satır eklemeyi ve silmeyi engelleme
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cca497aeaedd0c9f988241092eed707ecc259859
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628897"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme
Bazen, kullanıcıların <xref:System.Windows.Forms.DataGridView> denetiinizden yeni veri satırları girmesini veya mevcut satırları silmelerini engellemek isteyebilirsiniz. Yeni satırlar, denetimin alt kısmındaki Yeni kayıtlar için özel satıra girilir. Satır eklemeyi devre dışı bıraktığınızda, yeni kayıtlar için satır görüntülenmez. Daha sonra satır silme ve hücre düzenlemesini devre dışı bırakarak denetimi tamamen Salt okunabilir hale getirebilirsiniz.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Satır ekleme ve silmeyi engellemek için

- <xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesinde bulunan Tasarımcı eylemleri simgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve sonra silmeyi **eklemeyi** ve **silmeyi** etkinleştir onay kutularını temizleyin.

    > [!NOTE]
    > Denetimi tamamen Salt okunabilir hale getirmek için, **düzenlemeleri etkinleştir** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
