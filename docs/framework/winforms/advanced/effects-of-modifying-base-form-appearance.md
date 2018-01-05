---
title: "Bir taban formunu &#39;değiştirmenin etkileri; s görünümü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b808d10cd393d84ed29cb5e1cccfcff9c6c098d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="35f01-102">Bir taban formunu &#39;değiştirmenin etkileri; s görünümü</span><span class="sxs-lookup"><span data-stu-id="35f01-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="35f01-103">Uygulama geliştirme sırasında genellikle başka biçimlerde proje (veya diğer projeler) devralma taban form görünümü değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="35f01-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="35f01-104">Tasarım zamanında için taban formun görünüşünü değiştirir (ayarı özellikleri veya toplama ve çıkarma denetimlerinin olması) temel formu içeren proje yapılandırıldığında devralınan formlarında yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="35f01-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="35f01-105">Yalnızca temel formun değişiklikleri kaydetmek yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="35f01-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="35f01-106">Bir proje oluşturmak için seçin **yapı** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="35f01-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35f01-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="35f01-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="35f01-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="35f01-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="35f01-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="35f01-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
 <span data-ttu-id="35f01-110">Çalışma zamanında temel formda yapılan değişiklikler zaten örneği devralınan formlar üzerinde hiçbir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="35f01-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f01-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35f01-111">See Also</span></span>  
 [<span data-ttu-id="35f01-112">base</span><span class="sxs-lookup"><span data-stu-id="35f01-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="35f01-113">Nasıl yapılır: Windows Forms’u Devralma</span><span class="sxs-lookup"><span data-stu-id="35f01-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="35f01-114">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="35f01-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
