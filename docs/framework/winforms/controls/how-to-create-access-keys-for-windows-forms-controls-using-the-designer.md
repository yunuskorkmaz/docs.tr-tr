---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimleri için Erişim Tuşları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 410fc0134046c5fa7e05bfcd38ce6818244a0a54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307879"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="d591d-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d591d-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="d591d-103">Bir *erişim anahtarı* menü, menü öğesi ya da bir düğme gibi bir denetimin etiket metninin altı çizili karakterdir.</span><span class="sxs-lookup"><span data-stu-id="d591d-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="d591d-104">Bunu, "bir düğme önceden tanımlanmış bir erişim anahtarı ile birlikte ALT tuşuna basarak tıklayın" kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="d591d-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="d591d-105">Örneğin, bir form yazdırma için bir yordam bir düğme çalıştırır ve bu nedenle kendi `Text` "P" neden harfin altı çizili "P" düğme metni çalışma zamanında harf önce "ve işareti ekleme Yazdır," (&) özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d591d-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="d591d-106">Kullanıcı, ilişkili düğme ALT + P tuşlarına basarak komut çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d591d-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="d591d-107">Bir erişim anahtarı için alamayan bir denetim sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="d591d-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d591d-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d591d-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d591d-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d591d-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d591d-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d591d-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="d591d-111">Bir denetim için erişim anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d591d-111">To create an access key for a control</span></span>  
  
1. <span data-ttu-id="d591d-112">İçinde **özellikleri** penceresinde `Text` özellik erişim tuşu olacak harfi önce ve işareti içeren bir dize (&).</span><span class="sxs-lookup"><span data-stu-id="d591d-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="d591d-113">Harfi "P" erişim anahtarı olarak ayarlamak için örneğin **& Yazdır** kılavuza.</span><span class="sxs-lookup"><span data-stu-id="d591d-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d591d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d591d-114">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="d591d-115">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="d591d-115">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="d591d-116">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d591d-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="d591d-117">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="d591d-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
