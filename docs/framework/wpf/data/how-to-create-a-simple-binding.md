---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555025"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="bee89-102">Nasıl yapılır: Basit bir Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bee89-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="bee89-103">Bu örnek nasıl basit bir oluşturulacağını gösterir <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="bee89-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bee89-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bee89-104">Example</span></span>  
 <span data-ttu-id="bee89-105">Bu örnekte, sahip olduğunuz bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="bee89-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="bee89-106">`Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="bee89-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="bee89-107">İçeren vurgulanan satırı `<src>` öğesi aşağıdaki örnekte başlatır `Person` nesnesi ile bir `PersonName` özellik değerinin `Joe`.</span><span class="sxs-lookup"><span data-stu-id="bee89-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="bee89-108">Bu yapılır `Resources` bölümünde ve atanmış bir `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="bee89-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="bee89-109">İçeren vurgulanan satırı `<TextBlock>` öğesi sonra bağlar <xref:System.Windows.Controls.TextBlock> denetimini `PersonName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bee89-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="bee89-110">Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "Can" değeriyle belirir.</span><span class="sxs-lookup"><span data-stu-id="bee89-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee89-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bee89-111">See Also</span></span>  
 [<span data-ttu-id="bee89-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bee89-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="bee89-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="bee89-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
