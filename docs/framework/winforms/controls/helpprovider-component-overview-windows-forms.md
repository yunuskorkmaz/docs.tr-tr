---
title: HelpProvider Bileşenine Genel Bakış (Windows Forms)
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
ms.openlocfilehash: 177b61cab99d21a844298632020244fa424d8d2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176585"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="fe232-102">HelpProvider Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fe232-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="fe232-103">Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) bileşeni, bir HTML Yardım 1.x Yardım dosyası (HTML Help Workshop ile üretilen bir .chm dosyası veya bir .htm dosyasının), Windows uygulama ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe232-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="fe232-104">Çeşitli şekillerde Yardım sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe232-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="fe232-105">Windows Forms'da denetimleri için bağlama duyarlı Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe232-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="fe232-106">Bağlama duyarlı Yardım belirli iletişim kutusu ya da belirli bir iletişim kutusu denetimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe232-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="fe232-107">Ana sayfasında içindekiler tablosu, dizin veya bir arama işlevi gibi belirli alanları için bir Yardım dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fe232-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="fe232-108">Yardım sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="fe232-108">Using the Help Provider</span></span>  
 <span data-ttu-id="fe232-109">Ekleme bir <xref:System.Windows.Forms.HelpProvider> Windows formunuza bileşen Yardım özelliklerini göstermek için form üzerindeki diğer denetimler sağlar <xref:System.Windows.Forms.HelpProvider> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="fe232-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="fe232-110">Bu, Windows formundaki denetimler için Yardım vermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe232-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="fe232-111">Yardım dosyası ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.HelpProvider> bileşenini kullanarak <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fe232-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="fe232-112">Yardım çağırarak sağlanan türünü belirtin <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> ve değeri elde <xref:System.Windows.Forms.HelpNavigator> belirtilen denetimi için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="fe232-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="fe232-113">Anahtar sözcük veya konuda Yardım almak için çağırarak sağladığınız <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe232-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="fe232-114">İsteğe bağlı olarak belirli bir Yardım dizeyi başka bir denetimle ilişkilendirilecek kullanın <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe232-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="fe232-115">Kullanıcı F1 tuşuna bastığında denetim odağa sahip ancak bu yöntemi kullanarak bir denetimle ilişkilendirme dize açılan bir pencerede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fe232-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="fe232-116">Varsa <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> , kullanmanız gerekir, ayarlanmış durumda <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> Yardım metnini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="fe232-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="fe232-117">Her ikisi de ayarladıysanız <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ve Yardım temel Yardım dizesi <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="fe232-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe232-118">Yardım dosyasında da yolunu belirtirken göreli yolu kullanarak sorunlarla karşılaşabilirsiniz <xref:System.Windows.Forms.Help.ShowHelp%2A> yöntemi veya <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği <xref:System.Windows.Forms.HelpProvider> denetimi.</span><span class="sxs-lookup"><span data-stu-id="fe232-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="fe232-119">Bu nedenle, Yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fe232-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe232-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe232-120">See also</span></span>

- [<span data-ttu-id="fe232-121">Windows Forms Uygulamalarındaki Yardım Sistemleri</span><span class="sxs-lookup"><span data-stu-id="fe232-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
