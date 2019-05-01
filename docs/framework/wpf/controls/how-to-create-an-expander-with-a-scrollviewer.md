---
title: 'Nasıl yapılır: ScrollViewer ile bir Genişletici Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: ef0bc5d344f7d465de9209708430d3e61d40d4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910799"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="cb2b6-102">Nasıl yapılır: ScrollViewer ile bir Genişletici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb2b6-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="cb2b6-103">Bu örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Expander> içeren bir görüntü ve metin gibi karmaşık içerik denetimi.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="cb2b6-104">Bu örnek ayrıca içeriğini barındırır <xref:System.Windows.Controls.Expander> içinde bir <xref:System.Windows.Controls.ScrollViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb2b6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb2b6-105">Example</span></span>  
 <span data-ttu-id="cb2b6-106">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="cb2b6-107">Örnekte bir <xref:System.Windows.Controls.Primitives.BulletDecorator> tanımlamak için bir görüntü ve metin içeren bir denetim <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="cb2b6-108">A <xref:System.Windows.Controls.ScrollViewer> denetim genişletilmiş içerik kaydırma bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="cb2b6-109">Örnek ayarlar Not <xref:System.Windows.FrameworkElement.Height%2A> özelliği <xref:System.Windows.Controls.ScrollViewer> yerine içerik üzerinde.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="cb2b6-110">Varsa <xref:System.Windows.FrameworkElement.Height%2A> içeriğe göre ayarlanır <xref:System.Windows.Controls.ScrollViewer> içerik kaydırma kullanıcıya izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="cb2b6-111"><xref:System.Windows.FrameworkElement.Width%2A> Özelliği ayarlanmış <xref:System.Windows.Controls.Expander> denetimi ve bu ayar uygulandığı <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve genişletilmiş içeriği.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="cb2b6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb2b6-112">See also</span></span>

- <xref:System.Windows.Controls.Expander>
- [<span data-ttu-id="cb2b6-113">Genişleticiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb2b6-113">Expander Overview</span></span>](expander-overview.md)
- [<span data-ttu-id="cb2b6-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="cb2b6-114">How-to Topics</span></span>](expander-how-to-topics.md)
