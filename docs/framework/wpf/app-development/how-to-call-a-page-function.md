---
title: 'Nasıl yapılır: Sayfa İşlevi Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: 4cd839cc959c1e3730418d2feab80b9aef642161
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542827"
---
# <a name="how-to-call-a-page-function"></a>Nasıl yapılır: Sayfa İşlevi Çağırma
Bu örnek bir Sayfa işlevinden çağırmak nasıl gösterir bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfası.  
  
## <a name="example"></a>Örnek  
 Sayfasını kullanarak işlevi gezinebilirsiniz bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], bir sayfasına gittiğinizde olduğu gibi. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 Sayfa işlevine veri iletmek gerekiyorsa bir örneğini oluşturun ve bir özelliği ayarlayarak veri geçirebilirsiniz. Veya aşağıdaki örnekte gösterildiği gibi varsayılan olmayan bir Oluşturucu kullanarak verileri geçirebilirsiniz.  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Navigation.PageFunction%601>
