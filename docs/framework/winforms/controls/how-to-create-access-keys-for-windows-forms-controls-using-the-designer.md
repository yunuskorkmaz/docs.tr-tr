---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimleri için Erişim Tuşları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19c47c21526ca6e7aa4046a1853f3d1743438d17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="abeb6-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="abeb6-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="abeb6-103">Bir *erişim tuşu* altı çizili bir karakter menü, menü öğesi ya da bir düğmesi gibi denetimin etiket metnini,'dir.</span><span class="sxs-lookup"><span data-stu-id="abeb6-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="abeb6-104">"Bir düğme önceden tanımlanmış erişim anahtarı ile birlikte ALT tuşuna basarak tıklayın" kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="abeb6-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="abeb6-105">Örneğin, bir düğme bir form yazdırma için bir yordam çalıştırıyorsa ve bu nedenle, `Text` "P" neden harfi "altı çizili P" düğmesi metni çalışma zamanında harf önce "ve işareti ekleme Yazdır," (&) özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="abeb6-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="abeb6-106">Kullanıcı ilişkili düğme ALT + S tuşlarına basarak komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abeb6-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="abeb6-107">Odağı alamayan bir denetim için erişim tuşu sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="abeb6-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abeb6-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="abeb6-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="abeb6-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="abeb6-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="abeb6-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="abeb6-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="abeb6-111">Bir denetim için erişim anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="abeb6-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="abeb6-112">İçinde **özellikleri** penceresindeki ayarlayın `Text` özellik erişim tuşu olacaktır harf önce ve işareti içeren bir dize için (&).</span><span class="sxs-lookup"><span data-stu-id="abeb6-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="abeb6-113">Örneğin, harf "P" erişim tuşu olarak ayarlamak için şunu yazın **& Yazdırma** kılavuz içine.</span><span class="sxs-lookup"><span data-stu-id="abeb6-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abeb6-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abeb6-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="abeb6-115">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="abeb6-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="abeb6-116">Nasıl yapılır: tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="abeb6-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="abeb6-117">Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma</span><span class="sxs-lookup"><span data-stu-id="abeb6-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
