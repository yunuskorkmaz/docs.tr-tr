---
title: Bir taban formunu değiştirmenin etkileri&#39;görünümünü
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: adaf9224fd340c6ea4342e2591806a7c877e83ff
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533901"
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="2e7dc-102">Bir taban formunu değiştirmenin etkileri&#39;görünümünü</span><span class="sxs-lookup"><span data-stu-id="2e7dc-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="2e7dc-103">Uygulama geliştirme sırasında genellikle diğer forms projesinde (veya diğer projelerde) devraldığını taban formun görünüşünü değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="2e7dc-104">Taban formun görünüşünü için tasarım zamanında değiştirir (ayar ve özellikleri ekleme ve denetimleri çıkarılmasının olması) temel formu içeren bir proje derlenirken devralınan formlar üzerinde yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="2e7dc-105">Yalnızca temel forma değişiklikleri kaydetmek yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="2e7dc-106">Bir proje oluşturmak için Seç **derleme** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e7dc-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2e7dc-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2e7dc-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2e7dc-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
 <span data-ttu-id="2e7dc-110">Çalışma zamanında temel formda yapılan değişiklikleri zaten örneği devralınan formlar üzerinde hiçbir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7dc-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e7dc-111">See Also</span></span>  
 [<span data-ttu-id="2e7dc-112">base</span><span class="sxs-lookup"><span data-stu-id="2e7dc-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="2e7dc-113">Nasıl yapılır: Windows Forms’u Devralma</span><span class="sxs-lookup"><span data-stu-id="2e7dc-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="2e7dc-114">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="2e7dc-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
