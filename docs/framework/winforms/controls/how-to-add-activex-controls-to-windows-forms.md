---
title: 'Nasıl yapılır: Windows Formlarına ActiveX Denetimleri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 7d6514c679187e9ec193f6dda8336c8bd56fac81
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078427"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="f2964-102">Nasıl yapılır: Windows Formlarına ActiveX Denetimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="f2964-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="f2964-103">Windows Form Tasarımcısı ana bilgisayar Windows Forms denetimleri için iyileştirilmiştir, ancak Windows Forms ActiveX denetimleri de koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2964-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f2964-104">ActiveX denetimleri kendilerine eklenen zaman Windows Forms için performans sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="f2964-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="f2964-105">ActiveX denetimleri formunuza eklemeden önce araç kutusuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2964-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="f2964-106">Daha fazla bilgi için [COM bileşenlerini, özelleştirme araç kutusu iletişim kutusunda](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span><span class="sxs-lookup"><span data-stu-id="f2964-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2964-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f2964-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f2964-108">Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f2964-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f2964-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f2964-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="f2964-110">ActiveX denetimi Windows formunuza eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2964-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="f2964-111">Araç kutusu denetimi çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f2964-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="f2964-112">Visual Studio denetim için tüm başvuruları projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="f2964-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="f2964-113">Windows Forms ActiveX denetimlerinde kullanırken göz önünde bulundurmanız gereken noktalar hakkında daha fazla bilgi için bkz. [bir Windows formunda bir ActiveX denetimi Barındırmayla ilgili konular](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="f2964-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2964-114">Windows Forms ActiveX denetim içeri Aktarıcı (AxImp.exe) ActiveX dinamik bağlantı kitaplıkları içeri aktarma sırasında beklenenden farklı türde olay bağımsız değişkenlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2964-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="f2964-115">AxImp.exe tarafından oluşturulan bağımsız değişkenleri aşağıdakine benzer: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenir.</span><span class="sxs-lookup"><span data-stu-id="f2964-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="f2964-116">Bu tutarsızlığı kod normal çalışmasını engellemez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f2964-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="f2964-117">Ayrıntılar için bkz [Windows Forms ActiveX denetim içeri Aktarıcı (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="f2964-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2964-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2964-118">See Also</span></span>  
 [<span data-ttu-id="f2964-119">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="f2964-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="f2964-120">Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan</span><span class="sxs-lookup"><span data-stu-id="f2964-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="f2964-121">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="f2964-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="f2964-122">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f2964-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="f2964-123">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="f2964-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="f2964-124">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="f2964-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="f2964-125">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="f2964-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
