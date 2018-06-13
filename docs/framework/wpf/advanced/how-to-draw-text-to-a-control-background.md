---
title: 'Nasıl yapılır: bir denetim için metin çizme&#39;s arka plan'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: f79ec4f2c394fdc9462f4fd00942673b4536d713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542983"
---
# <a name="how-to-draw-text-to-a-control39s-background"></a><span data-ttu-id="58cba-102">Nasıl yapılır: bir denetim için metin çizme&#39;s arka plan</span><span class="sxs-lookup"><span data-stu-id="58cba-102">How to: Draw Text to a Control&#39;s Background</span></span>
<span data-ttu-id="58cba-103">Bir metin dizesi dönüştürerek doğrudan bir denetim arka plan için metin çizebilirsiniz bir <xref:System.Windows.Media.FormattedText> nesnesini genişletin ve ardından denetimin çizim nesnesi <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="58cba-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="58cba-104">Arka plan nesnelerin çizime türetilmiş için de bu tekniği kullanabilirsiniz <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="58cba-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="58cba-105">![Metin arka planı olarak görüntüleme denetimleri](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="58cba-105">![Controls displaying text as background](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="58cba-106">Özel metin arka plan denetimleriyle örneği</span><span class="sxs-lookup"><span data-stu-id="58cba-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="58cba-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="58cba-107">Example</span></span>  
 <span data-ttu-id="58cba-108">Denetim arka plan çizmek için yeni bir oluşturma <xref:System.Windows.Media.DrawingBrush> nesne ve dönüştürülen metin nesnenin çizin <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="58cba-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="58cba-109">Ardından, yeni Ata <xref:System.Windows.Media.DrawingBrush> denetimin arka plan özelliğine.</span><span class="sxs-lookup"><span data-stu-id="58cba-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="58cba-110">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.FormattedText> nesne ve arka planını çizin bir <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Button> nesne.</span><span class="sxs-lookup"><span data-stu-id="58cba-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="58cba-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58cba-111">See Also</span></span>  
 <xref:System.Windows.Media.FormattedText>  
 [<span data-ttu-id="58cba-112">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="58cba-112">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
