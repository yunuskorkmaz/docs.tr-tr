---
title: "Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 498849cc0205775f88c21d90d12b45c6b71a5dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="17548-102">Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma</span><span class="sxs-lookup"><span data-stu-id="17548-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="17548-103">Bu örnek binding nesnesinin veri bağlama hedef özelliğinden elde etme gösterir.</span><span class="sxs-lookup"><span data-stu-id="17548-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17548-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="17548-104">Example</span></span>  
 <span data-ttu-id="17548-105">Almak için aşağıdakileri yapabilirsiniz <xref:System.Windows.Data.Binding> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="17548-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  <span data-ttu-id="17548-106">Hedef nesnenin birden fazla özellik veri bağlamayı kullanması mümkün olduğundan, istediğiniz bağlama için bağımlılık özelliği belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="17548-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="17548-107">Alternatif olarak, alabileceğiniz <xref:System.Windows.Data.BindingExpression> ve değerini alın <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="17548-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="17548-108">Tam bir örnek için bkz: [bağlama doğrulama örnek](http://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="17548-108">For the complete example see [Binding Validation Sample](http://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17548-109">Bağlama ise bir <xref:System.Windows.Data.MultiBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="17548-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="17548-110">Eğer öyleyse bir <xref:System.Windows.Data.PriorityBinding>, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="17548-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="17548-111">Target özelliği kullanılarak mı bağlı emin değilseniz bir <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, veya bir <xref:System.Windows.Data.PriorityBinding>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="17548-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17548-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17548-112">See Also</span></span>  
 [<span data-ttu-id="17548-113">Kod içinde bir bağlaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="17548-113">Create a Binding in Code</span></span>](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [<span data-ttu-id="17548-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="17548-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
