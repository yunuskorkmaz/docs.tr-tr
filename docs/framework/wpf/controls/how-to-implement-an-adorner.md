---
title: 'Nasıl yapılır: Donatıcı Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: 53a25396ba5d8a5c78e850e636b7c882c03d5152
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362649"
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="9024a-102">Nasıl yapılır: Donatıcı Uygulama</span><span class="sxs-lookup"><span data-stu-id="9024a-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="9024a-103">Bu örnekte, en az donatıcı uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9024a-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="9024a-104">Uygulayanlar için Notlar</span><span class="sxs-lookup"><span data-stu-id="9024a-104">Notes for Implementers</span></span>  
 <span data-ttu-id="9024a-105">Donatıcıları herhangi devralınan işleme davranışını içermez dikkat edin önemlidir; öğeye bir donatıcı oluşturulduğunu sağlama donatıcı uygulayan sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="9024a-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="9024a-106">Geçersiz kılmak için işleme davranışını uygulamanın yaygın bir yolu olan <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> (Bu örnekte gösterildiği gibi) gerektiği gibi donatıcının görseller oluşturmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="9024a-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9024a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9024a-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9024a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9024a-108">Description</span></span>  
 <span data-ttu-id="9024a-109">Özet devralan bir sınıf uygulama tarafından oluşturulan özel bir donatıcı <xref:System.Windows.Documents.Adorner> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9024a-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="9024a-110">Örnek donatıcı köşelerini yalnızca daireler donatır bir <xref:System.Windows.UIElement> kılarak daireler ile <xref:System.Windows.UIElement.OnRender%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9024a-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9024a-111">Kod</span><span class="sxs-lookup"><span data-stu-id="9024a-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="9024a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9024a-112">See also</span></span>
- [<span data-ttu-id="9024a-113">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9024a-113">Adorners Overview</span></span>](adorners-overview.md)
