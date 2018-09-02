---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Sütununun Türünü Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 41ab0b36c5f3632ff4458d1289295ab2c9efe7c3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420483"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="3498a-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Sütununun Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3498a-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="3498a-103">Bazen bir Windows Forms için zaten eklenmiş bir sütun türünü değiştirmek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="3498a-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3498a-104">Örneğin, bazı denetim bir veri kaynağına bağlandığınızda otomatik oluşturulan sütunları türlerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3498a-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="3498a-105">Görüntü tablo ilişkili bir tablodaki satırlara yabancı anahtarlar içeren sütunlar olduğunda bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3498a-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="3498a-106">Bu durumda, bu yabancı anahtarları ile ilişkili tablodaki daha anlamlı değerleri gösteren birleşik giriş kutusu sütunları gösteren metin kutusu sütunları değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3498a-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>  
  
 <span data-ttu-id="3498a-107">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="3498a-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3498a-108">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3498a-108">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3498a-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3498a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3498a-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3498a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3498a-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3498a-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="3498a-112">Tasarımcı kullanarak bir sütun türünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="3498a-112">To change the type of a column using the designer</span></span>  
  
1.  <span data-ttu-id="3498a-113">Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **sütunları Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="3498a-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="3498a-114">Bir sütun seçin **seçili sütun** listesi.</span><span class="sxs-lookup"><span data-stu-id="3498a-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="3498a-115">İçinde **sütun özellikleri** kılavuz Ayarla `ColumnType` özelliğini yeni sütun türü.</span><span class="sxs-lookup"><span data-stu-id="3498a-115">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3498a-116">`ColumnType` Sütun türünü temsil eden sınıf gösteren bir tasarım zaman-özelliği salt okunur bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="3498a-116">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="3498a-117">Bir sütun sınıfta tanımlanan gerçek bir özellik değil.</span><span class="sxs-lookup"><span data-stu-id="3498a-117">It is not an actual property defined in a column class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3498a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3498a-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [<span data-ttu-id="3498a-119">Nasıl yapılır: bir Windows uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3498a-119">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="3498a-120">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="3498a-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
