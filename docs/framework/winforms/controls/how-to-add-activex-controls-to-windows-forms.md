---
title: 'Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 780411949c543a2178de5e7c531bd2202703f27a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166056"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="8d8e0-102">Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="8d8e0-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="8d8e0-103">Windows Form Tasarımcısı ana bilgisayar Windows Forms denetimleri için iyileştirilmiştir, ancak Windows Forms ActiveX denetimleri de koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8d8e0-104">ActiveX denetimleri kendilerine eklenen zaman Windows Forms için performans sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="8d8e0-105">ActiveX denetimleri formunuza eklemeden önce araç kutusuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="8d8e0-106">Daha fazla bilgi için [COM bileşenlerini, özelleştirme araç kutusu iletişim kutusunda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8d8e0-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d8e0-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8d8e0-108">Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8d8e0-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8d8e0-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="8d8e0-110">ActiveX denetimi Windows formunuza eklemek için</span><span class="sxs-lookup"><span data-stu-id="8d8e0-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="8d8e0-111">Araç kutusu denetimi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="8d8e0-112">Visual Studio denetim için tüm başvuruları projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="8d8e0-113">Windows Forms ActiveX denetimlerinde kullanırken göz önünde bulundurmanız gereken noktalar hakkında daha fazla bilgi için bkz. [bir Windows formunda bir ActiveX denetimi Barındırmayla ilgili konular](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="8d8e0-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8d8e0-114">Windows Forms ActiveX denetim içeri Aktarıcı (AxImp.exe) ActiveX dinamik bağlantı kitaplıkları içeri aktarma sırasında beklenenden farklı türde olay bağımsız değişkenlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="8d8e0-115">AxImp.exe tarafından oluşturulan bağımsız değişkenleri aşağıdakine benzer: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenir.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="8d8e0-116">Bu tutarsızlığı kod normal çalışmasını engellemez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="8d8e0-117">Ayrıntılar için bkz [Windows Forms ActiveX denetim içeri Aktarıcı (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="8d8e0-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8e0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d8e0-118">See also</span></span>

- [<span data-ttu-id="8d8e0-119">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="8d8e0-119">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="8d8e0-120">[Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8d8e0-120">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="8d8e0-121">Nasıl yapılır: Windows Forms'a denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="8d8e0-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="8d8e0-122">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="8d8e0-122">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="8d8e0-123">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="8d8e0-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="8d8e0-124">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="8d8e0-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="8d8e0-125">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="8d8e0-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
