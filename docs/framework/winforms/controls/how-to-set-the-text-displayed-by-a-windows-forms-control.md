---
title: Denetim tarafından görünen metni ayarla
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: eb02cbc3b335b0d5856f786b21d1d202cf444211
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738428"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="02409-102">Nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek metni ayarlama</span><span class="sxs-lookup"><span data-stu-id="02409-102">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="02409-103">Windows Forms denetimleri genellikle denetimin birincil işleviyle ilgili bazı metinleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="02409-103">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="02409-104">Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğme tıklandığında gerçekleştirilecek eylemi belirten bir başlık görüntüler.</span><span class="sxs-lookup"><span data-stu-id="02409-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="02409-105">Tüm denetimler için <xref:System.Windows.Forms.Control.Text%2A> özelliğini kullanarak metni ayarlayabilir veya döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02409-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="02409-106"><xref:System.Windows.Forms.Control.Font%2A> özelliğini kullanarak yazı tipini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02409-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="02409-107">Ayrıca, [tasarımcıyı](#designer)kullanarak metni de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02409-107">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="02409-108">Programatik</span><span class="sxs-lookup"><span data-stu-id="02409-108">Programmatic</span></span>

1. <span data-ttu-id="02409-109"><xref:System.Windows.Forms.Control.Text%2A> özelliğini bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="02409-109">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="02409-110">Altı çizili erişim anahtarı oluşturmak için, erişim tuşu olacak harften önce bir ve işareti (&) içerir.</span><span class="sxs-lookup"><span data-stu-id="02409-110">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="02409-111"><xref:System.Windows.Forms.Control.Font%2A> özelliğini <xref:System.Drawing.Font>türünde bir nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="02409-111">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > <span data-ttu-id="02409-112">Bir kaçış karakteri kullanarak, normalde bunları farklı şekilde yorumlayacak Kullanıcı arabirimi öğelerinde menü öğeleri gibi özel bir karakter görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02409-112">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="02409-113">Örneğin, aşağıdaki kod satırı menü öğesinin metnini "tamamen farklı bir şey Için şimdi & okunacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="02409-113">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="02409-114">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="02409-114">Designer</span></span>

1. <span data-ttu-id="02409-115">Visual Studio 'daki **Özellikler** penceresinde, denetimin **Text** özelliğini uygun bir dize olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="02409-115">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="02409-116">Altı çizili kısayol tuşu oluşturmak için, kısayol tuşu olacak harften önce bir ve işareti (&) içerir.</span><span class="sxs-lookup"><span data-stu-id="02409-116">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="02409-117">**Özellikler** penceresinde, **yazı tipi** özelliğinin yanındaki üç nokta düğmesini (![üç nokta düğmesini (...) Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi) seçin.</span><span class="sxs-lookup"><span data-stu-id="02409-117">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="02409-118">Standart yazı tipi iletişim kutusunda yazı tipi, yazı tipi stili, boyut, efekt (üstü çizili veya altı çizili) ve istediğiniz betiği seçin.</span><span class="sxs-lookup"><span data-stu-id="02409-118">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="02409-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02409-119">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="02409-120">Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02409-120">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="02409-121">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="02409-121">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
