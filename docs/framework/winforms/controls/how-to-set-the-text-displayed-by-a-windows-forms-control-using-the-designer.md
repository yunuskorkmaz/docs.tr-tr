---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimi Tarafından Görüntülenen Metni Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6d49466e5dd25bbe9e97262d68f2c3fb2f8ba1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="4023c-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4023c-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="4023c-103">Windows Forms denetimleri genellikle denetimi birincil işlev için ilgili bazı metinleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4023c-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="4023c-104">Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğme tıklatıldığında ne gerçekleştirilen gösteren resim yazısı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4023c-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="4023c-105">Tüm denetimler için ayarlama veya kullanarak metin döndürme <xref:System.Windows.Forms.Control.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4023c-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="4023c-106">Yazı tipi kullanarak değiştirebilirsiniz <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4023c-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="4023c-107">Metin ve yazı tipi Tasarımcısı ile ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4023c-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="4023c-108">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Control.Text%2A> uygun bir dizeye denetiminin özelliği.</span><span class="sxs-lookup"><span data-stu-id="4023c-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="4023c-109">Bir altı çizili kısayol tuşu oluşturmak için içerir ve işareti (&) kısayol tuşunu olacaktır harf önce.</span><span class="sxs-lookup"><span data-stu-id="4023c-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="4023c-110">Özellikler penceresinde üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.Control.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4023c-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="4023c-111">Standart yazı tipi iletişim kutusu, yazı tipi, yazı tipi stilini, boyutu, etkileri (örneğin, üstü çizili veya alt çizgi) ve betik istediğiniz seçin.</span><span class="sxs-lookup"><span data-stu-id="4023c-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4023c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4023c-112">See Also</span></span>  
 [<span data-ttu-id="4023c-113">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4023c-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="4023c-114">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="4023c-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="4023c-115">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="4023c-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
