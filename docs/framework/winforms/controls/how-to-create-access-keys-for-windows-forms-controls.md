---
title: 'Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: e6c829553163359301bad2cd896fc43562ee8069
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746859"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="bfa91-102">Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bfa91-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="bfa91-103">Bir *erişim anahtarı* menü, menü öğesi ya da bir düğme gibi bir denetimin etiket metninin altı çizili karakterdir.</span><span class="sxs-lookup"><span data-stu-id="bfa91-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="bfa91-104">Bir erişim anahtarı ile kullanıcı "bir düğme önceden tanımlanmış bir erişim anahtarı ile birlikte ALT tuşuna basarak tıklayabilirsiniz".</span><span class="sxs-lookup"><span data-stu-id="bfa91-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="bfa91-105">Örneğin, bir form yazdırma için bir yordam bir düğme çalıştırır ve bu nedenle kendi `Text` "P" harfi harfine çalışma zamanında düğmesi metnin altı çizili "P" neden olmadan önce ve işareti ekleme özelliği "Print," ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfa91-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="bfa91-106">Kullanıcı, ilişkili düğme ALT + P tuşlarına basarak komut çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfa91-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="bfa91-107">Bir erişim anahtarı için alamayan bir denetim sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="bfa91-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="bfa91-108">Bir denetim için erişim anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bfa91-108">To create an access key for a control</span></span>  
  
1. <span data-ttu-id="bfa91-109">Ayarlama `Text` özelliği kısayol olacak harfi önce ve işareti içeren bir dize (&).</span><span class="sxs-lookup"><span data-stu-id="bfa91-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bfa91-110">Bir erişim anahtarı oluşturmadan bir başlık ve işareti eklemek için iki işaretlerini Ekle (& &).</span><span class="sxs-lookup"><span data-stu-id="bfa91-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="bfa91-111">Tek bir ve işareti başlığı görüntülenir ve herhangi bir karakter altı çizili olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="bfa91-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa91-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfa91-112">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="bfa91-113">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="bfa91-113">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="bfa91-114">Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="bfa91-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="bfa91-115">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="bfa91-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
