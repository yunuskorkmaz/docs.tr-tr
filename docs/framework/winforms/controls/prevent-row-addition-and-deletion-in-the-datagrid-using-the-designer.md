---
title: 'Nasıl yapılır: Satır eklemeyi ve tasarımcı kullanarak Windows Forms DataGridView denetiminde Silmeyi engelle'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 65f7e6834c71281e6824d319459f46c431110d4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493276"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="8556a-102">Nasıl yapılır: Satır eklemeyi ve tasarımcı kullanarak Windows Forms DataGridView denetiminde Silmeyi engelle</span><span class="sxs-lookup"><span data-stu-id="8556a-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="8556a-103">Bazen kullanıcıların yeni veri satırı girme veya var olan satır silme önlemek istersiniz, <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8556a-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8556a-104">Yeni satırlar, denetimin altındaki yeni kayıtlar için özel satırda girilir.</span><span class="sxs-lookup"><span data-stu-id="8556a-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="8556a-105">Yeni kayıtlar için satır satır eklemeyi devre dışı bıraktığınızda görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="8556a-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="8556a-106">Daha sonra denetim salt okunur tamamen silme satır ve hücre düzenleme devre dışı bırakarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8556a-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>  
  
 <span data-ttu-id="8556a-107">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8556a-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8556a-108">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8556a-108">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8556a-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8556a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8556a-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8556a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8556a-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8556a-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="8556a-112">Satır ekleme ve silme işlemlerini önlemek için</span><span class="sxs-lookup"><span data-stu-id="8556a-112">To prevent row addition and deletion</span></span>  
  
-   <span data-ttu-id="8556a-113">Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından temizleyin **eklemeyi etkinleştir** ve **silmeyi etkinleştir** onay kutuları.</span><span class="sxs-lookup"><span data-stu-id="8556a-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8556a-114">Salt okunur tamamen denetimi yapmak için Temizle **düzenlemeyi etkinleştir** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="8556a-114">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8556a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8556a-115">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8556a-116">Nasıl yapılır: Bir Windows uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8556a-116">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [<span data-ttu-id="8556a-117">Nasıl yapılır: Windows Forms'a denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="8556a-117">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
