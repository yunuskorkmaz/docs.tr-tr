---
title: "Nasıl yapılır: Donatıcı Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76bceae5b69fad4c217127617309484edcf18108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="1a410-102">Nasıl yapılır: Donatıcı Uygulama</span><span class="sxs-lookup"><span data-stu-id="1a410-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="1a410-103">Bu örnek, en az donatıcı uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a410-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="1a410-104">Uygulayanlar için Notlar</span><span class="sxs-lookup"><span data-stu-id="1a410-104">Notes for Implementers</span></span>  
 <span data-ttu-id="1a410-105">Donatıcılar herhangi devralınmış işleme davranışını içermez dikkate almak önemlidir; donatıcı işler sağlama donatıcı uygulayan sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="1a410-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="1a410-106">İşleme davranışını uygulamanın en yaygın yolu geçersiz kılmaktır <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> donatıcının (Bu örnekte gösterildiği gibi) gereken görsellerini işlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1a410-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a410-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a410-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1a410-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a410-108">Description</span></span>  
 <span data-ttu-id="1a410-109">Özel bir donatıcı Özet devralan bir sınıf uygulama tarafından oluşturulan <xref:System.Windows.Documents.Adorner> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a410-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="1a410-110">Örnek donatıcı yalnızca köşelerinde daireler donatır bir <xref:System.Windows.UIElement> kılarak daireler ile <xref:System.Windows.UIElement.OnRender%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a410-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1a410-111">Kod</span><span class="sxs-lookup"><span data-stu-id="1a410-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="1a410-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a410-112">See Also</span></span>  
 [<span data-ttu-id="1a410-113">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a410-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
