---
title: "Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: f6d20025d59a702357b12da9f5dc0f5887968143
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542759"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="16dc6-102">Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="16dc6-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="16dc6-103">Bu örnek nasıl belirleneceğini göstermektedir olup bir <xref:System.Windows.Freezable> nesnesinin dondurulmuş.</span><span class="sxs-lookup"><span data-stu-id="16dc6-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="16dc6-104">Dondurulmuş değiştirmeye çalışırsanız, <xref:System.Windows.Freezable> nesnesi, onu oluşturur bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="16dc6-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="16dc6-105">Bu özel durum atma önlemek için <xref:System.Windows.Freezable.IsFrozen%2A> özelliği <xref:System.Windows.Freezable> dondurulmuş olup olmadığını belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="16dc6-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16dc6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="16dc6-106">Example</span></span>  
 <span data-ttu-id="16dc6-107">Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush> ve kullanılarak test <xref:System.Windows.Freezable.IsFrozen%2A> dondurulmuş olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="16dc6-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="16dc6-108">Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16dc6-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16dc6-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16dc6-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [<span data-ttu-id="16dc6-110">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16dc6-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="16dc6-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="16dc6-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
