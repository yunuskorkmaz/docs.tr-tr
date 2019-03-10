---
title: "Nasıl yapılır: Windows Forms'a ActiveX denetimleri ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 68e25cb2cd7e1f1c63954b20d24f028a49431553
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707995"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="2bf7e-102">Nasıl yapılır: Windows Forms'a ActiveX denetimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="2bf7e-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="2bf7e-103">Windows Form Tasarımcısı ana bilgisayar Windows Forms denetimleri için iyileştirilmiştir, ancak Windows Forms ActiveX denetimleri de koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2bf7e-104">ActiveX denetimleri kendilerine eklenen zaman Windows Forms için performans sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="2bf7e-105">ActiveX denetimleri formunuza eklemeden önce araç kutusuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="2bf7e-106">Daha fazla bilgi için [COM bileşenlerini, özelleştirme araç kutusu iletişim kutusunda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2bf7e-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bf7e-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2bf7e-108">Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2bf7e-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2bf7e-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="2bf7e-110">ActiveX denetimi Windows formunuza eklemek için</span><span class="sxs-lookup"><span data-stu-id="2bf7e-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="2bf7e-111">Araç kutusu denetimi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="2bf7e-112">Visual Studio denetim için tüm başvuruları projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="2bf7e-113">Windows Forms ActiveX denetimlerinde kullanırken göz önünde bulundurmanız gereken noktalar hakkında daha fazla bilgi için bkz. [bir Windows formunda bir ActiveX denetimi Barındırmayla ilgili konular](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="2bf7e-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2bf7e-114">Windows Forms ActiveX denetim içeri Aktarıcı (AxImp.exe) ActiveX dinamik bağlantı kitaplıkları içeri aktarma sırasında beklenenden farklı türde olay bağımsız değişkenlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="2bf7e-115">AxImp.exe tarafından oluşturulan bağımsız değişkenleri aşağıdakine benzer: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenir.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="2bf7e-116">Bu tutarsızlığı kod normal çalışmasını engellemez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="2bf7e-117">Ayrıntılar için bkz [Windows Forms ActiveX denetim içeri Aktarıcı (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="2bf7e-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf7e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bf7e-118">See also</span></span>
- [<span data-ttu-id="2bf7e-119">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="2bf7e-119">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="2bf7e-120">[Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2bf7e-120">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="2bf7e-121">Nasıl yapılır: Windows Forms'a denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="2bf7e-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="2bf7e-122">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="2bf7e-122">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="2bf7e-123">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="2bf7e-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="2bf7e-124">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="2bf7e-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="2bf7e-125">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="2bf7e-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
