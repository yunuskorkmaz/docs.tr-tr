---
title: "Nasıl yapılır: Freezable'ı Salt Okunur Yapma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: be3abd74a71fc711cd9f4bf6796b7d55017355ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543438"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="b322f-102">Nasıl yapılır: Freezable'ı Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="b322f-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="b322f-103">Bu örnek nasıl yapılacağını gösteren bir <xref:System.Windows.Freezable> salt okunur çağırarak kendi <xref:System.Windows.Freezable.Freeze%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b322f-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="b322f-104">Freeze olamaz bir <xref:System.Windows.Freezable> aşağıdaki koşullardan herhangi biri olup olmadığını nesne `true` nesneyle ilgili:</span><span class="sxs-lookup"><span data-stu-id="b322f-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="b322f-105">Animasyonlu veya veri ilişkili özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b322f-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="b322f-106">Dinamik bir kaynak tarafından ayarlanan özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b322f-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="b322f-107">Dinamik kaynaklar hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="b322f-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="b322f-108">İçerdiği <xref:System.Windows.Freezable> dondurulmuş olamaz alt nesneler.</span><span class="sxs-lookup"><span data-stu-id="b322f-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="b322f-109">Bu koşullar olduğunda `false` için <xref:System.Windows.Freezable> nesne ve düşünmüyorsanız değiştirmek için performans avantajı için dondurmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b322f-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b322f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b322f-110">Example</span></span>  
 <span data-ttu-id="b322f-111">Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush>, bir tür olduğu <xref:System.Windows.Freezable> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b322f-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="b322f-112">Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b322f-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b322f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b322f-113">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="b322f-114">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b322f-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="b322f-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b322f-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
