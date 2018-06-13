---
title: 'Nasıl yapılır: Sayfa İşlevinin Dönüş Değerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- functions [WPF], getting return values of
- page functions [WPF], getting return values of
- return values of page functions [WPF]
- getting [WPF], return values of page functions
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
ms.openlocfilehash: 2994a0fd7a192716a829c8290f030788da74cec5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545275"
---
# <a name="how-to-get-the-return-value-of-a-page-function"></a>Nasıl yapılır: Sayfa İşlevinin Dönüş Değerini Alma
Bu örnek bir sayfa işlevi tarafından döndürülen sonuç almak nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Sayfa işlevinden döndürülen sonucu elde etmek için işleme gerek <xref:System.Windows.Navigation.PageFunction%601.Return> çağırdığınız sayfa işlevinin.  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Navigation.PageFunction%601>
