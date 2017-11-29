---
title: "Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7bbb13e8a2b877d0f503e091b5bb8b1e7e89d00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="76cfa-102">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="76cfa-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="76cfa-103">Geliştirme ve denetimleri dağıtmak gibi görünmesi bu denetimleri isteyebilirsiniz **araç kutusu öğelerini Seç** , sağ tıklattığınızda görüntülenen iletişim kutusunda, **araç** seçip  **Öğeleri seçin**.</span><span class="sxs-lookup"><span data-stu-id="76cfa-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="76cfa-104">AssemblyFoldersEx kayıt yordamı kullanarak bu iletişim kutusunda görünmesi denetiminizi etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cfa-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="76cfa-105">Araç kutusu öğelerini Seç iletişim kutusunda, Denetim görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="76cfa-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="76cfa-106">Denetim derleme genel derleme önbelleğine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="76cfa-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="76cfa-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="76cfa-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="76cfa-108">veya</span><span class="sxs-lookup"><span data-stu-id="76cfa-108">-or-</span></span>  
  
-   <span data-ttu-id="76cfa-109">Denetim ve onun ilişkili tasarım zamanı derlemeleri AssemblyFoldersEx kayıt yordamı kullanarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="76cfa-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="76cfa-110">AssemblyFoldersEx, üçüncü taraf satıcılar her destekledikleri framework sürümü için yollar depoladığınız bir kayıt defteri konumdur.</span><span class="sxs-lookup"><span data-stu-id="76cfa-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="76cfa-111">Tasarım zamanı çözümleme başvuru derlemeleri bulmak için bu kayıt defteri konumunda bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cfa-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="76cfa-112">Kayıt defteri komut dosyası araç kutusunda görünmesini istediğiniz denetimleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76cfa-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="76cfa-113">Daha fazla bilgi için bkz: [bir özel denetim ve tasarım zamanı derlemeleri (Visual Studio 2013) dağıtma](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="76cfa-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76cfa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76cfa-114">See Also</span></span>  
 [<span data-ttu-id="76cfa-115">Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="76cfa-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="76cfa-116">Özel bir denetim ve tasarım zamanı derlemeleri (Visual Studio 2013) dağıtma</span><span class="sxs-lookup"><span data-stu-id="76cfa-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="76cfa-117">Windows Forms denetimleri geliştirme tasarım zamanında</span><span class="sxs-lookup"><span data-stu-id="76cfa-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="76cfa-118">Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="76cfa-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="76cfa-119">İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma</span><span class="sxs-lookup"><span data-stu-id="76cfa-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
