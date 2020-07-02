---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
description: Windows Presentation Foundation (WPF) içinde bu nasıl yapılır örneği aracılığıyla uygulamalarınız için basit bir bağlama oluşturun.
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618707"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="db462-103">Nasıl yapılır: Basit bir Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db462-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="db462-104">Bu örnekte, nasıl basit bir şekilde oluşturabileceğiniz gösterilmektedir <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="db462-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db462-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="db462-105">Example</span></span>  
 <span data-ttu-id="db462-106">Bu örnekte, bir `Person` String özelliği adlı bir nesneniz vardır `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="db462-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="db462-107">`Person`Nesnesi, adlı ad alanında tanımlanır `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="db462-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="db462-108">Aşağıdaki örnekteki öğesini içeren vurgulanmış çizgi, `<src>` `Person` bir özellik değeri olan nesnesini başlatır `PersonName` `Joe` .</span><span class="sxs-lookup"><span data-stu-id="db462-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="db462-109">Bu, `Resources` bölümünde yapılır ve atanır `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="db462-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="db462-110">Öğesini içeren vurgulanmış çizgi, `<TextBlock>` daha sonra <xref:System.Windows.Controls.TextBlock> denetimi `PersonName` özelliğine bağlar.</span><span class="sxs-lookup"><span data-stu-id="db462-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="db462-111">Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "ali" değeri ile görünür.</span><span class="sxs-lookup"><span data-stu-id="db462-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db462-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db462-112">See also</span></span>

- [<span data-ttu-id="db462-113">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="db462-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="db462-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="db462-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
