---
title: 'Nasıl yapılır: Denetimin Arka Planına Metin Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 76449c88f9a720741c8ed61255e04a40e6a8613f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776211"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="2a3bb-102">Nasıl yapılır: Denetimin Arka Planına Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="2a3bb-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="2a3bb-103">Bir metin dizesindeki dönüştürerek doğrudan bir denetimin arka planına metin çizebilirsiniz bir <xref:System.Windows.Media.FormattedText> nesnesi ve ardından nesne denetimin çizim <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="2a3bb-104">Nesne arka plan çizimi türetilen için de bu tekniği kullanabilirsiniz <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="2a3bb-105">![Metin arka planı olarak görüntüleme denetimleri](./media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="2a3bb-105">![Controls displaying text as background](./media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="2a3bb-106">Özel metin arka plan denetimleriyle örneği</span><span class="sxs-lookup"><span data-stu-id="2a3bb-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a3bb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a3bb-107">Example</span></span>  
 <span data-ttu-id="2a3bb-108">Bir denetimin arka planına çizmek için yeni bir oluşturma <xref:System.Windows.Media.DrawingBrush> nesne ve nesnenin Dönüştürülen metin çizme <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="2a3bb-109">Ardından, yeni Ata <xref:System.Windows.Media.DrawingBrush> denetimin arka plan özelliği için.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="2a3bb-110">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.FormattedText> nesne ve arka planına çizin bir <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Button> nesne.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="2a3bb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="2a3bb-112">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="2a3bb-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
