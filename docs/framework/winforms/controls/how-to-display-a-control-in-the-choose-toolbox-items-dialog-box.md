---
title: 'Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 4ed3f6ffdf8a86d050b81311c9211767d8b179b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623608"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="99ec6-102">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="99ec6-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="99ec6-103">Geliştirin ve denetimleri dağıtmak gibi bu denetimlerin görünmesini isteyebilirsiniz **araç kutusu öğelerini Seç** , sağ tıkladığınızda görüntülenen iletişim kutusunda, **araç kutusu** seçip  **Öğeleri seçmek**.</span><span class="sxs-lookup"><span data-stu-id="99ec6-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="99ec6-104">Denetiminiz AssemblyFoldersEx kayıt yordamı kullanarak bu iletişim kutusunda görüntülenecek etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99ec6-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="99ec6-105">Denetiminiz araç kutusu öğelerini Seç iletişim kutusunda görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="99ec6-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
- <span data-ttu-id="99ec6-106">Denetim derlemeyi genel derleme önbelleğine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="99ec6-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="99ec6-107">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="99ec6-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="99ec6-108">-veya-</span><span class="sxs-lookup"><span data-stu-id="99ec6-108">-or-</span></span>  
  
- <span data-ttu-id="99ec6-109">Denetim ve onun ilişkili tasarım zamanı derlemeleri AssemblyFoldersEx kayıt yordamı kullanarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="99ec6-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="99ec6-110">AssemblyFoldersEx, üçüncü taraf satıcılarla destekledikleri framework'ün her sürümü için yollar depoladığınız bir kayıt defteri konumdur.</span><span class="sxs-lookup"><span data-stu-id="99ec6-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="99ec6-111">Tasarım zamanı çözümleme başvuru derlemelerini bulmak için bu kayıt defteri konumuna bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99ec6-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="99ec6-112">Kayıt betiği denetimleri araç kutusunda görünmesini istediğiniz belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99ec6-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="99ec6-113">Daha fazla bilgi için [bir özel denetim ve tasarım zamanı derlemeleri dağıtma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="99ec6-113">For more information, see [Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ec6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99ec6-114">See also</span></span>

- <span data-ttu-id="99ec6-115">[Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="99ec6-115">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- <span data-ttu-id="99ec6-116">[Özel bir denetim ve tasarım zamanı derlemeleri dağıtma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="99ec6-116">[Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span></span>
- [<span data-ttu-id="99ec6-117">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="99ec6-117">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="99ec6-118">Nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="99ec6-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [<span data-ttu-id="99ec6-119">İzlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma</span><span class="sxs-lookup"><span data-stu-id="99ec6-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
