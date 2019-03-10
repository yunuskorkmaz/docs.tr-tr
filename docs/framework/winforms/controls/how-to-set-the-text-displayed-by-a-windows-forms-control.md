---
title: 'Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi'
ms.date: 03/30/2017
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
ms.openlocfilehash: 8ebb39e4e9337ede0dc8c7f5569ea27d8cfafd26
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716914"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="92b9d-102">Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="92b9d-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="92b9d-103">Windows Forms denetimleri, genellikle denetimin birincil işleve ilgili bazı metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="92b9d-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="92b9d-104">Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğmesine tıklandığında hangi eylemin gerçekleştirileceğini belirten bir başlık görüntüler.</span><span class="sxs-lookup"><span data-stu-id="92b9d-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="92b9d-105">Tüm denetimler için ayarlayabilir veya dönüş metni kullanarak <xref:System.Windows.Forms.Control.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="92b9d-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="92b9d-106">Yazı tipi kullanarak değiştirebileceğiniz <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="92b9d-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="92b9d-107">Tasarımcı kullanarak metin de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92b9d-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="92b9d-108">Ayrıca bkz: [nasıl yapılır: Windows Forms Tasarımcısı'nı kullanarak denetimleri için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms Tasarımcısı'nı kullanarak denetimi](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [nasıl yapılır: Tarafından görüntülenen resmi ayarlama bir Windows Forms Tasarımcısı'nı kullanarak denetimi](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="92b9d-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="92b9d-109">Program aracılığıyla bir denetimi tarafından görüntülenen metni ayarlama</span><span class="sxs-lookup"><span data-stu-id="92b9d-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="92b9d-110">Ayarlama <xref:System.Windows.Forms.Control.Text%2A> bir dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="92b9d-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="92b9d-111">Bir altı çizili erişim anahtarı oluşturmak için içeren bir ampersan (&) erişim anahtarı olacak harfi önce.</span><span class="sxs-lookup"><span data-stu-id="92b9d-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="92b9d-112">Ayarlama <xref:System.Windows.Forms.Control.Font%2A> türünde bir nesne özelliğini <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="92b9d-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="92b9d-113">Bir kaçış karakteri, bir özel karakter normalde bunları farklı menü öğeleri gibi yorumlar kullanıcı arabirimi öğelerini görüntülemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92b9d-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="92b9d-114">Örneğin, menü öğesinin metin okumak için aşağıdaki kod satırını ayarlar "& şimdi bir şey için tamamen farklı":</span><span class="sxs-lookup"><span data-stu-id="92b9d-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="92b9d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92b9d-115">See also</span></span>
- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="92b9d-116">Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma</span><span class="sxs-lookup"><span data-stu-id="92b9d-116">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="92b9d-117">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="92b9d-117">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
