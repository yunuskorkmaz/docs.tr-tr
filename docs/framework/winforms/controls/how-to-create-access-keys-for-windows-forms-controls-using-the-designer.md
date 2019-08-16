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
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039517"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="4e49f-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e49f-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="4e49f-103">*Erişim tuşu* , bir menü, menü öğesi veya düğme gibi bir denetimin etiketi içindeki altı çizili bir karakterdir.</span><span class="sxs-lookup"><span data-stu-id="4e49f-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="4e49f-104">Daha önceden tanımlanmış erişim anahtarıyla birlikte ALT tuşuna basarak, kullanıcının bir düğmeye tıklamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e49f-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="4e49f-105">Örneğin, bir düğme bir formu yazdırmak için bir yordam çalıştırıyorsa ve bu nedenle `Text` özelliği "Yazdır" olarak ayarlanırsa, "p" harfinden önce bir ampersan (&) eklemek "p" harfinin çalışma zamanında düğme metninde altı çizili olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4e49f-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="4e49f-106">Kullanıcı, ALT + P tuşlarına basarak düğmeyle ilişkili komutu çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="4e49f-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="4e49f-107">Odak alamayan bir denetim için erişim anahtarınız olamaz.</span><span class="sxs-lookup"><span data-stu-id="4e49f-107">You cannot have an access key for a control that cannot receive focus.</span></span>

## <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="4e49f-108">Bir denetim için erişim anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4e49f-108">To create an access key for a control</span></span>

1. <span data-ttu-id="4e49f-109">**Özellikler** penceresinde, `Text` özelliği, erişim anahtarı olacak harften önce bir ve işareti (&) içeren bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4e49f-109">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="4e49f-110">Örneğin, "P" harfini erişim anahtarı olarak ayarlamak için kılavuza **&** yazın.</span><span class="sxs-lookup"><span data-stu-id="4e49f-110">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e49f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e49f-111">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="4e49f-112">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme</span><span class="sxs-lookup"><span data-stu-id="4e49f-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="4e49f-113">Nasıl yapılır: Windows Forms denetimi tarafından görünen metni ayarlama</span><span class="sxs-lookup"><span data-stu-id="4e49f-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="4e49f-114">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="4e49f-114">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
