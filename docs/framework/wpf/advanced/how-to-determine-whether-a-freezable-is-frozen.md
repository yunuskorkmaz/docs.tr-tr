---
title: "Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 005bb27803830a2e38a7b143d2c4cff669ad1da6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362519"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="82d2b-102">Nasıl yapılır: Freezable'ın Dondurulmuş Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="82d2b-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="82d2b-103">Bu örnek nasıl belirleneceğini göstermektedir olup olmadığını bir <xref:System.Windows.Freezable> nesne donuktur.</span><span class="sxs-lookup"><span data-stu-id="82d2b-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="82d2b-104">Dondurulmuş değiştirmeye çalışırsanız <xref:System.Windows.Freezable> nesnesi atar bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="82d2b-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="82d2b-105">Bu özel durum önlemek için <xref:System.Windows.Freezable.IsFrozen%2A> özelliği <xref:System.Windows.Freezable> dondurulmuş olup olmadığını belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="82d2b-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82d2b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="82d2b-106">Example</span></span>  
 <span data-ttu-id="82d2b-107">Aşağıdaki örnek donuyor bir <xref:System.Windows.Media.SolidColorBrush> ve kullanılarak test <xref:System.Windows.Freezable.IsFrozen%2A> dondurulmuş olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="82d2b-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="82d2b-108">Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="82d2b-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d2b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82d2b-109">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [<span data-ttu-id="82d2b-110">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="82d2b-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="82d2b-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="82d2b-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
