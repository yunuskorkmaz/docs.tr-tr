---
title: "Nasıl yapılır: ScrollViewer ile bir Genişletici Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="01504-102">Nasıl yapılır: ScrollViewer ile bir Genişletici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01504-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="01504-103">Bu örnek nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Expander> bir resim ve metin gibi karmaşık içerik içeren denetim.</span><span class="sxs-lookup"><span data-stu-id="01504-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="01504-104">Bu örnek ayrıca içeriğini barındırır <xref:System.Windows.Controls.Expander> içinde bir <xref:System.Windows.Controls.ScrollViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="01504-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01504-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="01504-105">Example</span></span>  
 <span data-ttu-id="01504-106">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="01504-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="01504-107">Örnek kullanan bir <xref:System.Windows.Controls.Primitives.BulletDecorator> tanımlamak için bir resim ve metin içeren denetim <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="01504-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="01504-108">A <xref:System.Windows.Controls.ScrollViewer> denetimi genişletilmiş içeriği kaydırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="01504-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="01504-109">Örnek ayarlar Not <xref:System.Windows.FrameworkElement.Height%2A> özellikte <xref:System.Windows.Controls.ScrollViewer> yerine içerik üzerinde.</span><span class="sxs-lookup"><span data-stu-id="01504-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="01504-110">Varsa <xref:System.Windows.FrameworkElement.Height%2A> içerik üzerinde ayarlanmış <xref:System.Windows.Controls.ScrollViewer> içeriği kaydırmak kullanıcının izin vermez.</span><span class="sxs-lookup"><span data-stu-id="01504-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="01504-111"><xref:System.Windows.FrameworkElement.Width%2A> Özelliği ayarlanmış <xref:System.Windows.Controls.Expander> denetimi ve bu ayar uygulandığı <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve genişletilmiş içeriği.</span><span class="sxs-lookup"><span data-stu-id="01504-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="01504-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01504-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="01504-113">Genişleticiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="01504-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="01504-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="01504-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
