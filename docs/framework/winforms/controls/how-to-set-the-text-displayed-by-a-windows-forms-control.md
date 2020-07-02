---
title: Denetim tarafından görünen metni ayarla
description: Windows Forms denetimi tarafından görüntülenecek metni ayarlamayı öğrenin. Text özelliğini kullanarak metni ayarlayın veya döndürün ya da Font özelliğini kullanarak yazı tipini değiştirin.
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
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622854"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="4f5f7-104">Nasıl yapılır: Windows Forms denetimi tarafından görüntülenecek metni ayarlama</span><span class="sxs-lookup"><span data-stu-id="4f5f7-104">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="4f5f7-105">Windows Forms denetimleri genellikle denetimin birincil işleviyle ilgili bazı metinleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-105">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="4f5f7-106">Örneğin, bir <xref:System.Windows.Forms.Button> denetim genellikle düğme tıklandığında gerçekleştirilecek eylemi belirten bir başlık görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-106">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="4f5f7-107">Tüm denetimler için, özelliğini kullanarak metni ayarlayabilir veya döndürebilirsiniz <xref:System.Windows.Forms.Control.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="4f5f7-107">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="4f5f7-108">Özelliğini kullanarak yazı tipini değiştirebilirsiniz <xref:System.Windows.Forms.Control.Font%2A> .</span><span class="sxs-lookup"><span data-stu-id="4f5f7-108">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="4f5f7-109">Ayrıca, [tasarımcıyı](#designer)kullanarak metni de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-109">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="4f5f7-110">Programlı</span><span class="sxs-lookup"><span data-stu-id="4f5f7-110">Programmatic</span></span>

1. <span data-ttu-id="4f5f7-111"><xref:System.Windows.Forms.Control.Text%2A>Özelliği bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="4f5f7-112">Altı çizili erişim anahtarı oluşturmak için, erişim tuşu olacak harften önce bir ve işareti (&) içerir.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-112">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="4f5f7-113"><xref:System.Windows.Forms.Control.Font%2A>Özelliğini türünde bir nesne olarak ayarlayın <xref:System.Drawing.Font> .</span><span class="sxs-lookup"><span data-stu-id="4f5f7-113">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

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
    > <span data-ttu-id="4f5f7-114">Bir kaçış karakteri kullanarak, normalde bunları farklı şekilde yorumlayacak Kullanıcı arabirimi öğelerinde menü öğeleri gibi özel bir karakter görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-114">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="4f5f7-115">Örneğin, aşağıdaki kod satırı menü öğesinin metnini "tamamen farklı bir şey Için şimdi & okunacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-115">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="4f5f7-116">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="4f5f7-116">Designer</span></span>

1. <span data-ttu-id="4f5f7-117">Visual Studio 'daki **Özellikler** penceresinde, denetimin **Text** özelliğini uygun bir dize olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-117">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="4f5f7-118">Altı çizili kısayol tuşu oluşturmak için, kısayol tuşu olacak harften önce bir ve işareti (&) içerir.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-118">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="4f5f7-119">**Özellikler** penceresinde, ![ ](./media/visual-studio-ellipsis-button.png) **yazı tipi** özelliğinin yanındaki üç nokta düğmesini (Visual Studio Özellikler penceresi) seçin.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-119">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="4f5f7-120">Standart yazı tipi iletişim kutusunda yazı tipi, yazı tipi stili, boyut, efekt (üstü çizili veya altı çizili) ve istediğiniz betiği seçin.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-120">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f5f7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f5f7-121">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4f5f7-122">Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4f5f7-122">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="4f5f7-123">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="4f5f7-123">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
