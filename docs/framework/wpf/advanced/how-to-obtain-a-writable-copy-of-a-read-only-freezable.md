---
title: "Nasıl yapılır: Salt Okunur Freezable'ın Yazılabilir Kopyasını Edinme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 910c5dada6ca82f68992722e4df6b35f9f7497c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206479"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="0d8e3-102">Nasıl yapılır: Salt Okunur Freezable'ın Yazılabilir Kopyasını Edinme</span><span class="sxs-lookup"><span data-stu-id="0d8e3-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="0d8e3-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Freezable.Clone%2A> salt okunur'ın yazılabilir kopyasını oluşturmak için gereken yöntemini <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="0d8e3-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="0d8e3-104">Sonra bir <xref:System.Windows.Freezable> nesne işaretlenmiş salt okunur ("dondurulmuş"), onu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d8e3-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="0d8e3-105">Ancak, kullanabileceğiniz <xref:System.Windows.Freezable.Clone%2A> donmuş nesnesi değiştirilebilir bir kopyasını oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d8e3-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d8e3-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d8e3-106">Example</span></span>  
 <span data-ttu-id="0d8e3-107">Aşağıdaki örnek, dondurulmuş değiştirilebilir kopyasını oluşturur. <xref:System.Windows.Media.SolidColorBrush> nesne.</span><span class="sxs-lookup"><span data-stu-id="0d8e3-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="0d8e3-108">Hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0d8e3-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8e3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d8e3-109">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [<span data-ttu-id="0d8e3-110">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d8e3-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="0d8e3-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0d8e3-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
