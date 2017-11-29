---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Sütununun Türünü Değiştirme"
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
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d4f27c9dcdc1bc7e00b0c809c62889b6c61cd16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="85a91-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Sütununun Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="85a91-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="85a91-103">Bazen bir Windows Forms zaten eklenmiş bir sütunun türünü değiştirmek istersiniz <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="85a91-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="85a91-104">Örneğin, bir veri kaynağına denetimi bağladığınızda otomatik oluşturulan sütunları bazıları türlerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85a91-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="85a91-105">Görüntü tablosu yabancı anahtarları ilgili tablodaki satırları içeren sütunlar olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="85a91-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="85a91-106">Bu durumda, bu yabancı anahtarları ilişkili tablo daha anlamlı değerleri görüntülemek birleşik giriş kutusu sütunlarla görüntülemek metin kutusu sütunları değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85a91-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>  
  
 <span data-ttu-id="85a91-107">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="85a91-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="85a91-108">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="85a91-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85a91-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="85a91-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="85a91-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="85a91-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="85a91-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="85a91-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="85a91-112">Tasarımcı kullanarak bir sütunun türünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="85a91-112">To change the type of a column using the designer</span></span>  
  
1.  <span data-ttu-id="85a91-113">Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Edit Columns**.</span><span class="sxs-lookup"><span data-stu-id="85a91-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="85a91-114">Bir sütun seçin **seçili sütun** listesi.</span><span class="sxs-lookup"><span data-stu-id="85a91-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="85a91-115">İçinde **sütun özellikleri** kılavuzunu, ayarlamak `ColumnType` yeni sütun türü için özellik.</span><span class="sxs-lookup"><span data-stu-id="85a91-115">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85a91-116">`ColumnType` Sütun türünü temsil eden sınıf gösteren bir tasarım-zamanı-yalnızca özellik bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="85a91-116">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="85a91-117">Bir sütun sınıfında tanımlanan gerçek bir özellik değil.</span><span class="sxs-lookup"><span data-stu-id="85a91-117">It is not an actual property defined in a column class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a91-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85a91-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [<span data-ttu-id="85a91-119">Nasıl yapılır: bir Windows uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="85a91-119">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="85a91-120">Nasıl yapılır: Windows formlarına denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="85a91-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
