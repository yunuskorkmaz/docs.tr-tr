---
title: 'Nasıl yapılır: Windows Forms’da Dayama Çizgileri ve Kılavuz ile Denetimleri Düzenleme'
ms.date: 03/30/2017
f1_keywords:
- GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
ms.openlocfilehash: 122c20e7c3e48eaa4b4986ce2cb45411dae00723
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011014"
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="776a8-102">Nasıl yapılır: Windows Forms’da Dayama Çizgileri ve Kılavuz ile Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="776a8-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="776a8-103">Visual Studio düzen özelliklerini kullanarak, bir form üzerinde denetimleri yerleştirildiği tam olarak yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="776a8-103">Using the layout features of Visual Studio, you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="776a8-104">Bir forma eklendiğinde veya taşınan bir form üzerinde denetimleri otomatik olarak satır ve sütunları Windows Forms Tasarımcısı kılavuzunun hizalanabilir ya da dayama çizgileri özelliğini kullanarak denetimleri hizalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="776a8-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="776a8-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="776a8-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="776a8-106">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="776a8-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="776a8-107">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="776a8-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="776a8-108">Tüm denetimleri kılavuza Yasla</span><span class="sxs-lookup"><span data-stu-id="776a8-108">To snap all controls to the grid</span></span>  
  
- <span data-ttu-id="776a8-109">Seçin **LayoutMode** Düzen modu Windows Forms Tasarımcısı'nda **seçenekleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="776a8-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="776a8-110">Daha fazla bilgi için [genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="776a8-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).</span></span> <span data-ttu-id="776a8-111">Tüm denetimleri artık kendilerini noktalarında kılavuz boyunca hizalar.</span><span class="sxs-lookup"><span data-stu-id="776a8-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="776a8-112">Tek denetimleri kılavuza yerinde kilitleyerek yaslayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="776a8-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="776a8-113">Kilitli olduğunu, ancak bununla birlikte, bunlar yeniden boyutlandırılabilir veya taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="776a8-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="776a8-114">Kilitleme denetimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms'a denetimleri kilitleme](how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="776a8-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="776a8-115">Dayama çizgileri kullanarak denetimleri hizalama</span><span class="sxs-lookup"><span data-stu-id="776a8-115">To align controls using snaplines</span></span>  
  
- <span data-ttu-id="776a8-116">Seçin **dayama çizgileri** Düzen modu Windows Forms Tasarımcısı'nda **seçenekleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="776a8-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="776a8-117">Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="776a8-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="776a8-118">Dayama çizgileri, hizalama ve Formunuza denetim düzenleme için şimdi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="776a8-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776a8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="776a8-119">See also</span></span>

- <span data-ttu-id="776a8-120">[Genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="776a8-120">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- [<span data-ttu-id="776a8-121">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="776a8-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="776a8-122">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="776a8-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="776a8-123">Nasıl yapılır: Windows Forms'a denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="776a8-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="776a8-124">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="776a8-124">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="776a8-125">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="776a8-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="776a8-126">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="776a8-126">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="776a8-127">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="776a8-127">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
