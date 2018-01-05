---
title: "Nasıl yapılır: Sayfa İşlevi Çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba1aa9c713d311bf1c6b42e8f72e89bb292927dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="7f8f9-102">Nasıl yapılır: Sayfa İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="7f8f9-102">How to: Call a Page Function</span></span>
<span data-ttu-id="7f8f9-103">Bu örnek bir Sayfa işlevinden çağrısının nasıl gerçekleştireceğini bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfası.</span><span class="sxs-lookup"><span data-stu-id="7f8f9-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f8f9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f8f9-104">Example</span></span>  
 <span data-ttu-id="7f8f9-105">Kullanarak bir sayfa işlevi gidebilirsiniz bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], bir sayfaya gittiğinizde olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="7f8f9-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="7f8f9-106">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7f8f9-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="7f8f9-107">Sayfa işlevine veri iletmek gerekiyorsa, bir örneğini oluşturabilir ve bir özelliği ayarlanarak veri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f8f9-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="7f8f9-108">Veya, aşağıdaki örnekte gösterildiği gibi varsayılan olmayan bir Oluşturucu kullanarak veri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f8f9-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="7f8f9-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f8f9-109">See Also</span></span>  
 <xref:System.Windows.Navigation.PageFunction%601>
