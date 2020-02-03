---
title: Form kenarlıklarını değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739571"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="54980-102">Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="54980-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="54980-103">Windows Forms görünümünü ve davranışını belirlerken aralarından seçim yapabileceğiniz birkaç kenarlık stili vardır.</span><span class="sxs-lookup"><span data-stu-id="54980-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="54980-104"><xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini değiştirerek, formun yeniden boyutlandırma davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54980-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="54980-105">Ayrıca, <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ayarlanması, başlık çubuğunun ve üzerinde hangi düğmelerin görünebileceği hakkında da etkiler.</span><span class="sxs-lookup"><span data-stu-id="54980-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="54980-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="54980-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="54980-107">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="54980-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="54980-108">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms kenarlıklarını değiştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="54980-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="54980-109">Windows Forms kenarlık stilini program aracılığıyla ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="54980-109">To set the border style of Windows Forms programmatically</span></span>  
  
- <span data-ttu-id="54980-110"><xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini istediğiniz stile ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54980-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="54980-111">Aşağıdaki kod örneği `DlgBx1` biçim kenarlık stilini <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="54980-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="54980-112">Ayrıca bkz. [nasıl yapılır: tasarım zamanında Iletişim kutusu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="54980-112">Also see [How to: Create Dialog Boxes at Design Time](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span></span>  
  
     <span data-ttu-id="54980-113">Ayrıca, form için isteğe bağlı **minimize** ve **Ekranı Kapla** düğmelerini sağlayan bir kenarlık stili seçtiyseniz, bu düğmelerden birinin veya her ikisinin de işlevsel olmasını isteyip istemediğinizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54980-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="54980-114">Bu düğmeler, Kullanıcı deneyimini yakından denetlemek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="54980-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="54980-115">**Simge durumuna küçült** ve **Büyüt** düğmeleri varsayılan olarak etkindir ve işlevleri **Özellikler** penceresi aracılığıyla işlenir.</span><span class="sxs-lookup"><span data-stu-id="54980-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54980-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54980-116">See also</span></span>

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [<span data-ttu-id="54980-117">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="54980-117">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
