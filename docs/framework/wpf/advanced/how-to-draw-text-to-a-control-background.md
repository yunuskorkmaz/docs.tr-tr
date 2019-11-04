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
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424384"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="60c80-102">Nasıl yapılır: Denetimin Arka Planına Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="60c80-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="60c80-103">Bir metin dizesini <xref:System.Windows.Media.FormattedText> nesnesine dönüştürerek ve sonra denetimin <xref:System.Windows.Media.DrawingContext>nesneyi çizerek bir denetimin arka planına doğrudan metin çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c80-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="60c80-104">Bu tekniği, <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.StackPanel>gibi <xref:System.Windows.Controls.Panel>türetilen nesnelerin arka planına çizim için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c80-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="60c80-105">![Metin arka plan olarak görüntülenen denetimlerin ekran görüntüsü.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="60c80-105">![Screenshot of controls displaying text as background.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span></span>  
<span data-ttu-id="60c80-106">Özel metin arka planlarına sahip denetimler örneği</span><span class="sxs-lookup"><span data-stu-id="60c80-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="60c80-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="60c80-107">Example</span></span>  
 <span data-ttu-id="60c80-108">Bir denetimin arka planına çizim yapmak için, yeni bir <xref:System.Windows.Media.DrawingBrush> nesnesi oluşturun ve dönüştürülen metni nesnenin <xref:System.Windows.Media.DrawingContext>çizin.</span><span class="sxs-lookup"><span data-stu-id="60c80-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="60c80-109">Ardından, yeni <xref:System.Windows.Media.DrawingBrush> denetimin arka plan özelliğine atayın.</span><span class="sxs-lookup"><span data-stu-id="60c80-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="60c80-110">Aşağıdaki kod örneği, bir <xref:System.Windows.Media.FormattedText> nesnesinin nasıl oluşturulduğunu ve bir <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Button> nesnesinin arka planına nasıl çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="60c80-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="60c80-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c80-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="60c80-112">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="60c80-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
