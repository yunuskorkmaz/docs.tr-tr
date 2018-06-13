---
title: 'Nasıl yapılır: Donatıcı Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: f5b0ed080a413546a3b985055858e209f9f347eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552971"
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="0c549-102">Nasıl yapılır: Donatıcı Uygulama</span><span class="sxs-lookup"><span data-stu-id="0c549-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="0c549-103">Bu örnek, en az donatıcı uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c549-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="0c549-104">Uygulayanlar için Notlar</span><span class="sxs-lookup"><span data-stu-id="0c549-104">Notes for Implementers</span></span>  
 <span data-ttu-id="0c549-105">Donatıcılar herhangi devralınmış işleme davranışını içermez dikkate almak önemlidir; donatıcı işler sağlama donatıcı uygulayan sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="0c549-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="0c549-106">İşleme davranışını uygulamanın en yaygın yolu geçersiz kılmaktır <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> donatıcının (Bu örnekte gösterildiği gibi) gereken görsellerini işlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0c549-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c549-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c549-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0c549-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c549-108">Description</span></span>  
 <span data-ttu-id="0c549-109">Özel bir donatıcı Özet devralan bir sınıf uygulama tarafından oluşturulan <xref:System.Windows.Documents.Adorner> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0c549-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="0c549-110">Örnek donatıcı yalnızca köşelerinde daireler donatır bir <xref:System.Windows.UIElement> kılarak daireler ile <xref:System.Windows.UIElement.OnRender%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c549-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0c549-111">Kod</span><span class="sxs-lookup"><span data-stu-id="0c549-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="0c549-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c549-112">See Also</span></span>  
 [<span data-ttu-id="0c549-113">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0c549-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
