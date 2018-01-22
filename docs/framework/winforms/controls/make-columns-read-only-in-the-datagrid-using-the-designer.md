---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Salt Okunur Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa78d8afe59a147a37b1c827e8c755bf74e95633
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="e6db6-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="e6db6-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="e6db6-103">Varsayılan olarak, kullanıcılar metin ve Windows Forms'ta görüntülenen sayısal verileri değiştirebilir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="e6db6-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e6db6-104">Değiştirilmek üzere tasarlanmamıştır verileri görüntülemek istiyorsanız, salt okunur verileri içeren sütunları yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6db6-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="e6db6-105">Salt okunur tamamen denetimi yapma hakkında daha fazla bilgi için bkz [nasıl yapılır: satır ekleme önlemek ve Windows Forms DataGridView denetimi kullanarak Tasarımcı silinmesine](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e6db6-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="e6db6-106">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="e6db6-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e6db6-107">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e6db6-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6db6-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e6db6-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e6db6-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e6db6-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e6db6-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e6db6-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="e6db6-111">Tasarımcı kullanarak bir sütun salt okunur yapmak için</span><span class="sxs-lookup"><span data-stu-id="e6db6-111">To make a column read-only by using the designer</span></span>  
  
1.  <span data-ttu-id="e6db6-112">Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Edit Columns**.</span><span class="sxs-lookup"><span data-stu-id="e6db6-112">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="e6db6-113">Bir sütun seçin **seçili sütun** listesi.</span><span class="sxs-lookup"><span data-stu-id="e6db6-113">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="e6db6-114">İçinde **sütun özellikleri** kılavuzunu, ayarlamak <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="e6db6-114">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e6db6-115">Seçerek eklediğinizde, bir sütun salt okunur de yapabilirsiniz **salt okunur** onay kutusuna **Sütun Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e6db6-115">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6db6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6db6-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e6db6-117">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="e6db6-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="e6db6-118">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Eklemeyi ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="e6db6-118">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="e6db6-119">Nasıl yapılır: bir Windows uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6db6-119">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="e6db6-120">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="e6db6-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
