---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 157060e784e4169ac8e31c6028ed65f0a9568e0f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373588"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="e8ee3-102">Nasıl yapılır: Basit bir Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8ee3-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="e8ee3-103">Bu örnekte basit bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8ee3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8ee3-104">Example</span></span>  
 <span data-ttu-id="e8ee3-105">Bu örnekte bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="e8ee3-106">`Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="e8ee3-107">İçeren vurgulanan satırın `<src>` öğesi aşağıdaki örnekte başlatır `Person` nesnesi ile bir `PersonName` özelliği değerinin `Joe`.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="e8ee3-108">Bu yapılır `Resources` bölümünde ve atanmış bir `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="e8ee3-109">İçeren vurgulanan satırın `<TextBlock>` öğesi ardından bağlar <xref:System.Windows.Controls.TextBlock> denetimini `PersonName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="e8ee3-110">Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "Joe" değeriyle görünür.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ee3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8ee3-111">See also</span></span>
- [<span data-ttu-id="e8ee3-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e8ee3-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="e8ee3-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e8ee3-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
