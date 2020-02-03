---
title: Denetimler için erişim tuşları oluşturma
ms.date: 08/20/2019
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
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731163"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="4f3bb-102">Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma</span><span class="sxs-lookup"><span data-stu-id="4f3bb-102">How to: Create access keys for Windows Forms controls</span></span>

<span data-ttu-id="4f3bb-103">*Erişim tuşu* , bir menü, menü öğesi veya düğme gibi bir denetimin etiketi içindeki altı çizili bir karakterdir.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="4f3bb-104">Bir erişim anahtarı ile Kullanıcı, önceden tanımlanmış erişim anahtarı ile birlikte alt tuşuna basarak bir düğmeyi "tıklaedebilir".</span><span class="sxs-lookup"><span data-stu-id="4f3bb-104">With an access key, the user can "click" a button by pressing the Alt key in combination with the predefined access key.</span></span> <span data-ttu-id="4f3bb-105">Örneğin, bir düğme bir formu yazdırmak için bir yordam çalıştırıyorsa ve bu nedenle `Text` özelliği "Yazdır" olarak ayarlanırsa, "P" harfinden önce bir ampersan eklemek "P" harfinin çalışma zamanında düğme metninde altı çizili olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="4f3bb-106">Kullanıcı, alt + P tuşlarına basarak düğmeyle ilişkili komutu çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-106">The user can run the command associated with the button by pressing Alt+P.</span></span>

<span data-ttu-id="4f3bb-107">Odak alamayan denetimler erişim anahtarlarına sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-107">Controls that cannot receive focus can't have access keys.</span></span>

## <a name="programmatic"></a><span data-ttu-id="4f3bb-108">Programlı</span><span class="sxs-lookup"><span data-stu-id="4f3bb-108">Programmatic</span></span>

<span data-ttu-id="4f3bb-109">`Text` özelliğini, kısayol olacak harften önce bir ve işareti (&) içeren bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>

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
> <span data-ttu-id="4f3bb-110">Bir e-posta kutusunda bir erişim anahtarı oluşturmadan bir ve işareti kullanmak için, iki ve işaretleri (& &) dahil edin.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-110">To use an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="4f3bb-111">Başlıkta tek bir ve işareti görüntülenmediğinde, hiçbir karakter altı çizili değildir.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>

## <a name="designer"></a><span data-ttu-id="4f3bb-112">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="4f3bb-112">Designer</span></span>

<span data-ttu-id="4f3bb-113">Visual Studio 'nun **Özellikler** penceresinde, **metin** özelliğini, erişim tuşu olacak harften önce bir ve işareti (' & ') içeren bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-113">In the **Properties** window of Visual Studio, set the **Text** property to a string that includes an ampersand ('&') before the letter that will be the access key.</span></span> <span data-ttu-id="4f3bb-114">Örneğin, "P" harfini erişim anahtarı olarak ayarlamak için **& Yazdır**yazın.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-114">For example, to set the letter "P" as the access key, enter **&Print**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f3bb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f3bb-115">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="4f3bb-116">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="4f3bb-116">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="4f3bb-117">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4f3bb-117">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="4f3bb-118">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="4f3bb-118">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
