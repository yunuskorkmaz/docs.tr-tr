---
title: "Nasıl yapılır: Freezable'ı Salt Okunur Yapma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460075"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="95fc4-102">Nasıl yapılır: Freezable'ı Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="95fc4-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="95fc4-103">Bu örnek, <xref:System.Windows.Freezable.Freeze%2A> metodunu çağırarak <xref:System.Windows.Freezable> salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="95fc4-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="95fc4-104">Aşağıdaki koşullardan herhangi biri nesne hakkında `true` ise <xref:System.Windows.Freezable> nesnesini donduramazsınız:</span><span class="sxs-lookup"><span data-stu-id="95fc4-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="95fc4-105">Animasyonlu veya veri bağlantılı özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95fc4-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="95fc4-106">Dinamik bir kaynak tarafından ayarlanan özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95fc4-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="95fc4-107">Dinamik kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="95fc4-107">For more information about dynamic resources, see the [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
- <span data-ttu-id="95fc4-108">Dondurulamayan <xref:System.Windows.Freezable> alt nesneler içerir.</span><span class="sxs-lookup"><span data-stu-id="95fc4-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="95fc4-109">Bu koşullar <xref:System.Windows.Freezable> nesneniz için `false` ve değiştirmek istemiyorsanız, performans avantajları elde etmek için bunu dondurmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="95fc4-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95fc4-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="95fc4-110">Example</span></span>  
 <span data-ttu-id="95fc4-111">Aşağıdaki örnek, bir tür <xref:System.Windows.Freezable> nesnesi olan bir <xref:System.Windows.Media.SolidColorBrush>dondurur.</span><span class="sxs-lookup"><span data-stu-id="95fc4-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="95fc4-112"><xref:System.Windows.Freezable> nesneler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95fc4-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fc4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95fc4-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="95fc4-114">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="95fc4-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="95fc4-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="95fc4-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
