---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: a0f567befb1e0c323dd16fffedec279ff836cbf8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337961"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="de5dc-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="de5dc-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="de5dc-103">Windows Forms denetimleri, genellikle denetimin birincil işleve ilgili bazı metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de5dc-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="de5dc-104">Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğmesine tıklandığında hangi eylemin gerçekleştirileceğini gösteren bir başlık görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de5dc-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="de5dc-105">Tüm denetimler için ayarlayabilir veya dönüş metni kullanarak <xref:System.Windows.Forms.Control.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="de5dc-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="de5dc-106">Yazı tipi kullanarak değiştirebileceğiniz <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="de5dc-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="de5dc-107">Tasarımcı ile yazı tipi ve metin ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="de5dc-107">To set the text and font with the designer</span></span>  
  
1. <span data-ttu-id="de5dc-108">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Control.Text%2A> denetiminin uygun bir dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="de5dc-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="de5dc-109">Bir altı çizili kısayol tuşu oluşturulacağını içerir ve işareti (&) kısayol tuşunu olacak harfi önce.</span><span class="sxs-lookup"><span data-stu-id="de5dc-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2. <span data-ttu-id="de5dc-110">Özellikler penceresinde üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="de5dc-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="de5dc-111">Standart yazı tipi iletişim kutusu yazı tipini, yazı tipi stili, boyutu, etkileri (örneğin, üstü çizili veya alt çizgi) ve betik istediğiniz seçin.</span><span class="sxs-lookup"><span data-stu-id="de5dc-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5dc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de5dc-112">See also</span></span>

- [<span data-ttu-id="de5dc-113">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="de5dc-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="de5dc-114">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="de5dc-114">Using Fonts and Text</span></span>](../advanced/using-fonts-and-text.md)
- [<span data-ttu-id="de5dc-115">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="de5dc-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
