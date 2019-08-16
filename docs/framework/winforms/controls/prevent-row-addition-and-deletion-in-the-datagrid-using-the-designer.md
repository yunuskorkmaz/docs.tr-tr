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
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="7b46d-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="7b46d-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="7b46d-103">Bazen kullanıcıların yeni veri satırlarını girmesini veya denetiinizdeki <xref:System.Windows.Forms.DataGridView> mevcut satırları silmelerini engellemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7b46d-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7b46d-104">Yeni satırlar, denetimin alt kısmındaki Yeni kayıtlar için özel satıra girilir.</span><span class="sxs-lookup"><span data-stu-id="7b46d-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="7b46d-105">Satır eklemeyi devre dışı bıraktığınızda, yeni kayıtlar için satır görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="7b46d-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="7b46d-106">Daha sonra satır silme ve hücre düzenlemesini devre dışı bırakarak denetimi tamamen Salt okunabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b46d-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="7b46d-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b46d-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7b46d-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b46d-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="7b46d-109">Satır ekleme ve silmeyi engellemek için</span><span class="sxs-lookup"><span data-stu-id="7b46d-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="7b46d-110"><xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve sonra silmeyi **eklemeyi** ve **silmeyi** etkinleştir onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="7b46d-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7b46d-111">Denetimi tamamen Salt okunabilir hale getirmek için, **düzenlemeleri etkinleştir** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="7b46d-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b46d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b46d-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7b46d-113">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b46d-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="7b46d-114">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="7b46d-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
