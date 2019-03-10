---
title: "Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms Tasarımcısı'nı kullanarak denetimi"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 4d3f12bd2606e40b5ceeef716d8f5d264bc46622
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707384"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="317e9-102">Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms Tasarımcısı'nı kullanarak denetimi</span><span class="sxs-lookup"><span data-stu-id="317e9-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="317e9-103">Windows Forms denetimleri, genellikle denetimin birincil işleve ilgili bazı metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="317e9-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="317e9-104">Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğmesine tıklandığında hangi eylemin gerçekleştirileceğini gösteren bir başlık görüntüler.</span><span class="sxs-lookup"><span data-stu-id="317e9-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="317e9-105">Tüm denetimler için ayarlayabilir veya dönüş metni kullanarak <xref:System.Windows.Forms.Control.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="317e9-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="317e9-106">Yazı tipi kullanarak değiştirebileceğiniz <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="317e9-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="317e9-107">Tasarımcı ile yazı tipi ve metin ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="317e9-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="317e9-108">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Control.Text%2A> denetiminin uygun bir dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="317e9-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="317e9-109">Bir altı çizili kısayol tuşu oluşturulacağını içerir ve işareti (&) kısayol tuşunu olacak harfi önce.</span><span class="sxs-lookup"><span data-stu-id="317e9-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="317e9-110">Özellikler penceresinde üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="317e9-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="317e9-111">Standart yazı tipi iletişim kutusu yazı tipini, yazı tipi stili, boyutu, etkileri (örneğin, üstü çizili veya alt çizgi) ve betik istediğiniz seçin.</span><span class="sxs-lookup"><span data-stu-id="317e9-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="317e9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="317e9-112">See also</span></span>
- [<span data-ttu-id="317e9-113">Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="317e9-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="317e9-114">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="317e9-114">Using Fonts and Text</span></span>](../advanced/using-fonts-and-text.md)
- [<span data-ttu-id="317e9-115">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="317e9-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
