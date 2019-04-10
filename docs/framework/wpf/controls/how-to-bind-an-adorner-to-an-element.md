---
title: 'Nasıl yapılır: Öğeye bir Donatıcı Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: b6909fec466c2b31a7f4156c43b21a0c724f0217
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307294"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="9cdde-102">Nasıl yapılır: Öğeye bir Donatıcı Bağlama</span><span class="sxs-lookup"><span data-stu-id="9cdde-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="9cdde-103">Bu örnekte, program aracılığıyla belirtilen bir öğeye bir donatıcı bağlama işlemi gösterilmektedir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="9cdde-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cdde-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cdde-104">Example</span></span>  
 <span data-ttu-id="9cdde-105">Belirli bir öğeye bir donatıcı bağlama için <xref:System.Windows.UIElement>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9cdde-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="9cdde-106">Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> nesnesi <xref:System.Windows.UIElement> donatılmış için.</span><span class="sxs-lookup"><span data-stu-id="9cdde-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> <span data-ttu-id="9cdde-107">Belirtilen adreste başlayan görsel ağaç'kurmak gezer **UIElement**ve bulduğu ilk donatıcı katmanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cdde-107">walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="9cdde-108">(Hiçbir donatıcı katman bulunursa, yöntem null değeri döndürür.)</span><span class="sxs-lookup"><span data-stu-id="9cdde-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="9cdde-109">Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedefe bağlamak için yöntemi **UIElement**.</span><span class="sxs-lookup"><span data-stu-id="9cdde-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="9cdde-110">Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlayan bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="9cdde-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="9cdde-111">Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] başka bir öğeye bir donatıcı bağlamak için şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9cdde-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdde-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cdde-112">See also</span></span>

- [<span data-ttu-id="9cdde-113">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9cdde-113">Adorners Overview</span></span>](adorners-overview.md)
