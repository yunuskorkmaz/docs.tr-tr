---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: b65c83592334c84c7790da5877efdc9af84380f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708398"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="eb40e-102">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları gizleme</span><span class="sxs-lookup"><span data-stu-id="eb40e-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="eb40e-103">Bazen yalnızca bazı Windows Forms'ta mevcut olan sütunları görüntülemek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="eb40e-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="eb40e-104">Örneğin, bir çalışan görüntülemek isteyebilirsiniz maaş sütun diğer kullanıcılardan gizleyerek sırasında yönetim kimlik bilgilerine sahip kullanıcılar için.</span><span class="sxs-lookup"><span data-stu-id="eb40e-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="eb40e-105">Alternatif olarak, denetimi yalnızca bazılarının görüntülemek istediğiniz çok sayıda sütun içeren bir veri kaynağına bağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb40e-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="eb40e-106">Bu durumda, genellikle görüntüleme yerine gizlemeden ilgilenen olmayan sütunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="eb40e-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="eb40e-107">Daha fazla bilgi için [nasıl yapılır: Ekle ve Kaldır sütunları Windows Forms DataGridView Tasarımcısı'nı kullanarak denetiminde](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="eb40e-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="eb40e-108">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="eb40e-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="eb40e-109">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="eb40e-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb40e-110">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="eb40e-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="eb40e-111">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="eb40e-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="eb40e-112">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="eb40e-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="eb40e-113">Tasarımcı kullanarak bir sütunu gizlemek için</span><span class="sxs-lookup"><span data-stu-id="eb40e-113">To hide a column using the designer</span></span>  
  
1.  <span data-ttu-id="eb40e-114">Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **sütunları Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="eb40e-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="eb40e-115">Bir sütun seçin **seçili sütun** listesi.</span><span class="sxs-lookup"><span data-stu-id="eb40e-115">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="eb40e-116">İçinde **sütun özellikleri** kılavuz Ayarla <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="eb40e-116">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb40e-117">Bir sütunu kaldırarak eklerken gizleyebilirsiniz **görünür** onay kutusuna **Sütun Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="eb40e-117">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb40e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb40e-118">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="eb40e-119">Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma</span><span class="sxs-lookup"><span data-stu-id="eb40e-119">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="eb40e-120">Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb40e-120">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="eb40e-121">Nasıl yapılır: Windows Forms'a denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="eb40e-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
