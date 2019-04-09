---
title: "Nasıl yapılır: Freezable'ı Salt Okunur Yapma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 9b7102db4de0df7183355e50e3b372eac30d81b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191458"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="bedc8-102">Nasıl yapılır: Freezable'ı Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="bedc8-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="bedc8-103">Bu örnek nasıl yapılacağını gösteren bir <xref:System.Windows.Freezable> salt okunur çağırarak kendi <xref:System.Windows.Freezable.Freeze%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bedc8-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="bedc8-104">Freeze edilemez bir <xref:System.Windows.Freezable> aşağıdaki koşullardan herhangi biri doğru ise, nesne `true` nesneyle ilgili:</span><span class="sxs-lookup"><span data-stu-id="bedc8-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="bedc8-105">Animasyonlu veya veri ilişkili özellikleri.</span><span class="sxs-lookup"><span data-stu-id="bedc8-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="bedc8-106">Dinamik bir kaynak tarafından ayarlanan özellikler var.</span><span class="sxs-lookup"><span data-stu-id="bedc8-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="bedc8-107">Dinamik kaynaklar hakkında daha fazla bilgi için bkz. [XAML kaynakları](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bedc8-107">For more information about dynamic resources, see the [XAML Resources](xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="bedc8-108">İçerdiği <xref:System.Windows.Freezable> nelze zmrazit alt nesneler.</span><span class="sxs-lookup"><span data-stu-id="bedc8-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="bedc8-109">Bu koşullar varsa `false` için <xref:System.Windows.Freezable> nesne ve düşünmüyorsanız onu değiştirmek için performans avantajı için dondurmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="bedc8-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bedc8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="bedc8-110">Example</span></span>  
 <span data-ttu-id="bedc8-111">Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush>, bir tür olduğu <xref:System.Windows.Freezable> nesne.</span><span class="sxs-lookup"><span data-stu-id="bedc8-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="bedc8-112">Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bedc8-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedc8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bedc8-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="bedc8-114">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bedc8-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="bedc8-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="bedc8-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
