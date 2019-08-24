---
title: 'Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987066"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="53e25-102">Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="53e25-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="53e25-103">Visual Studio 'daki Windows Form Tasarımcısı Windows Forms denetimleri barındırmak için iyileştirilirken, ActiveX denetimlerini Windows Forms de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53e25-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="53e25-104">ActiveX denetimleri bunlara eklendiğinde Windows Forms için performans sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="53e25-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="53e25-105">Formunuza ActiveX denetimleri eklemeden önce, bunları araç kutusuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="53e25-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="53e25-106">Daha fazla bilgi için bkz. [com bileşenleri, araç kutusunu özelleştirme Iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="53e25-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="53e25-107">Windows formunuza ActiveX denetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="53e25-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="53e25-108">Windows formunuza ActiveX denetimi eklemek için araç kutusu üzerindeki denetime çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53e25-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="53e25-109">Visual Studio, tüm başvuruları projenizdeki denetime ekler.</span><span class="sxs-lookup"><span data-stu-id="53e25-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="53e25-110">Windows Forms üzerinde ActiveX denetimleri kullanırken aklınızda bulundurmanız gerekenler hakkında daha fazla bilgi için bkz. [bir Windows formunda ActiveX denetimi barındırırken dikkat edilecek noktalar](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="53e25-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="53e25-111">Windows Forms ActiveX denetim Içeri aktarıcı (AxImp. exe), ActiveX dinamik bağlantı kitaplıklarının içe aktarılması işlemini üzerinde beklenenden farklı bir türde olay bağımsız değişkenleri oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="53e25-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="53e25-112">Aximp. exe tarafından oluşturulan bağımsız değişkenler aşağıdakine benzerdir: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, ne zaman `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="53e25-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="53e25-113">Bu ırdüzenleyen 'in kodun normal şekilde çalışmasını önleyemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="53e25-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="53e25-114">Ayrıntılar için bkz. [Windows Forms ActiveX denetim Içeri aktarıcı (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="53e25-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53e25-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53e25-115">See also</span></span>

- [<span data-ttu-id="53e25-116">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="53e25-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="53e25-117">[Çeşitli dillerde ve kitaplıklarda karşılaştırılan denetimler ve programlanabilir nesneler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53e25-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="53e25-118">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="53e25-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="53e25-119">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="53e25-119">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="53e25-120">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="53e25-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="53e25-121">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="53e25-121">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
