---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütun Yeniden Sıralamayı Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 3864ce70f058259b597df904311bd4a48218b151
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040341"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="1a6f4-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütun Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1a6f4-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="1a6f4-103">Windows Forms <xref:System.Windows.Forms.DataGridView> denetimde görüntülenen veriler görüntülenirken, kullanıcılar bazen belirli sütunlardaki değerleri karşılaştırmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="1a6f4-104">Sütunları denetimde yaygın olarak ayrılırsa, özellikle ilgilendikleri tüm sütunları görmek için kullanıcıların otomatik olarak geri ve ileri kaydırılabilmesi durumunda bu durum kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="1a6f4-105">Kullanıcılarınızın sütunları yeniden sıralamak için sütun değerlerini karşılaştırma görevinin daha kolay olmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="1a6f4-106">Sütun yeniden sıralamayı etkinleştirdiğinizde, kullanıcılar sütun başlığını fareyle sürükleyerek bir sütunu yeni bir konuma taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="1a6f4-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1a6f4-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="1a6f4-109">Sütun yeniden sıralamayı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1a6f4-109">To enable column reordering</span></span>

- <span data-ttu-id="1a6f4-110"><xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket kabartmasını (![akıllı etiket karakteri](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklatın ve ardından **sütun yeniden sıralamayı etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a6f4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a6f4-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1a6f4-112">Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunları dondurma</span><span class="sxs-lookup"><span data-stu-id="1a6f4-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="1a6f4-113">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a6f4-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="1a6f4-114">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="1a6f4-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
