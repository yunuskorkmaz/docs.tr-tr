---
title: "Nasıl yapılır: Basit bir Bağlama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="f66fc-102">Nasıl yapılır: Basit bir Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f66fc-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="f66fc-103">Bu örnek nasıl basit bir oluşturulacağını gösterir <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="f66fc-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f66fc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f66fc-104">Example</span></span>  
 <span data-ttu-id="f66fc-105">Bu örnekte, sahip olduğunuz bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="f66fc-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="f66fc-106">`Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="f66fc-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="f66fc-107">İçeren vurgulanan satırı `<src>` öğesi aşağıdaki örnekte başlatır `Person` nesnesi ile bir `PersonName` özellik değerinin `Joe`.</span><span class="sxs-lookup"><span data-stu-id="f66fc-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="f66fc-108">Bu yapılır `Resources` bölümünde ve atanmış bir `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="f66fc-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="f66fc-109">İçeren vurgulanan satırı `<TextBlock>` öğesi sonra bağlar <xref:System.Windows.Controls.TextBlock> denetimini `PersonName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="f66fc-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="f66fc-110">Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "Can" değeriyle belirir.</span><span class="sxs-lookup"><span data-stu-id="f66fc-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66fc-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f66fc-111">See Also</span></span>  
 [<span data-ttu-id="f66fc-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f66fc-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f66fc-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f66fc-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
