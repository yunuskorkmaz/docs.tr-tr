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
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="f0049-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="f0049-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="f0049-103">Bazen, kullanıcıların <xref:System.Windows.Forms.DataGridView> denetiinizden yeni veri satırları girmesini veya mevcut satırları silmelerini engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0049-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f0049-104">Yeni satırlar, denetimin alt kısmındaki Yeni kayıtlar için özel satıra girilir.</span><span class="sxs-lookup"><span data-stu-id="f0049-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="f0049-105">Satır eklemeyi devre dışı bıraktığınızda, yeni kayıtlar için satır görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="f0049-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="f0049-106">Daha sonra satır silme ve hücre düzenlemesini devre dışı bırakarak denetimi tamamen Salt okunabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0049-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="f0049-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f0049-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f0049-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f0049-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="f0049-109">Satır ekleme ve silmeyi engellemek için</span><span class="sxs-lookup"><span data-stu-id="f0049-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="f0049-110"><xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesinde bulunan Tasarımcı eylemleri simgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve sonra silmeyi **eklemeyi** ve **silmeyi** etkinleştir onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="f0049-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f0049-111">Denetimi tamamen Salt okunabilir hale getirmek için, **düzenlemeleri etkinleştir** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="f0049-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0049-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0049-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f0049-113">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0049-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="f0049-114">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="f0049-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
