---
title: HelpProvider Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 74d35dfa39a605cb1e1e85cc3aeda834e1c60669
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738718"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="0e256-102">HelpProvider Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0e256-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="0e256-103">Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) bileşeni, bir HTML Yardım 1. x yardım dosyasını (HTML yardım atölyiyle oluşturulan bir. chm dosyası ya da bir. htm dosyası) Windows uygulamanızla ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e256-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="0e256-104">Çeşitli yollarla yardım sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e256-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="0e256-105">Windows Forms denetimleri için bağlama duyarlı yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e256-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="0e256-106">Belirli bir iletişim kutusu veya iletişim kutusunda belirli denetimler üzerinde bağlama duyarlı yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e256-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="0e256-107">Bir Içindekiler tablosunun ana sayfası, dizin veya arama işlevi gibi belirli alanlara bir yardım dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="0e256-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="0e256-108">Yardım sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="0e256-108">Using the Help Provider</span></span>  
 <span data-ttu-id="0e256-109">Windows formunuza bir <xref:System.Windows.Forms.HelpProvider> bileşeni eklemek, formdaki diğer denetimlerin <xref:System.Windows.Forms.HelpProvider> bileşenin yardım özelliklerini kullanıma almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0e256-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="0e256-110">Bu, Windows formunuzdaki denetimler için yardım sağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e256-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="0e256-111"><xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliğini kullanarak bir yardım dosyasını <xref:System.Windows.Forms.HelpProvider> bileşeniyle ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e256-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="0e256-112"><xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> çağırarak ve belirtilen denetim için <xref:System.Windows.Forms.HelpNavigator> numaralandırmasından bir değer sağlayarak sağlanan yardım türünü belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e256-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="0e256-113"><xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> yöntemini çağırarak yardım için anahtar sözcüğünü veya konuyu sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="0e256-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="0e256-114">İsteğe bağlı olarak, belirli bir Yardım dizesini başka bir denetimle ilişkilendirmek için <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e256-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="0e256-115">Bu yöntemi kullanarak bir denetimle ilişkilendirdiğiniz dize, denetim odağa sahipken kullanıcı F1 tuşuna bastığında bir açılır pencerede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0e256-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="0e256-116"><xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ayarlanmamışsa, yardım metnini sağlamak için <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e256-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="0e256-117">Hem <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> hem de yardım dizesini ayarladıysanız, <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> temel alan yardım, öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="0e256-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e256-118"><xref:System.Windows.Forms.Help.ShowHelp%2A> yönteminde veya <xref:System.Windows.Forms.HelpProvider> denetiminin <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliğindeki yardım dosyasının yolunu belirtirken göreli yolu kullanarak sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e256-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="0e256-119">Bu nedenle, yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e256-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e256-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e256-120">See also</span></span>

- [<span data-ttu-id="0e256-121">Windows Forms Uygulamalarındaki Yardım Sistemleri</span><span class="sxs-lookup"><span data-stu-id="0e256-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
