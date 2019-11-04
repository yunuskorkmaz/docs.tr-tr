---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453501"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="24a0f-102">Nasıl yapılır: Basit bir Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="24a0f-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="24a0f-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="24a0f-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24a0f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="24a0f-104">Example</span></span>  
 <span data-ttu-id="24a0f-105">In this example, you have a `Person` object with a string property named `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="24a0f-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="24a0f-106">The `Person` object is defined in the namespace called `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="24a0f-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="24a0f-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span><span class="sxs-lookup"><span data-stu-id="24a0f-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="24a0f-108">This is done in the `Resources` section and assigned an `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="24a0f-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="24a0f-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span><span class="sxs-lookup"><span data-stu-id="24a0f-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="24a0f-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span><span class="sxs-lookup"><span data-stu-id="24a0f-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a0f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24a0f-111">See also</span></span>

- [<span data-ttu-id="24a0f-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="24a0f-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="24a0f-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="24a0f-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
