---
title: 'Nasıl yapılır: bir sayfanın tarayıcıda barındırılıp barındırılmadığını belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424698"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Nasıl yapılır: bir sayfanın tarayıcıda barındırılıp barındırılmadığını belirleme
Bu örnek, bir <xref:System.Windows.Controls.Page> tarayıcıda barındırılıp barındırılmadığını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Page> ana bilgisayar belirsiz olabilir ve sonuç olarak, <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>veya tarayıcı dahil olmak üzere birkaç farklı türde konağa yüklenebilir. Bu durum, bir veya daha fazla sayfa içeren bir kitaplık derlemeniz varsa ve birden çok tek başına ve gözatılabilir (XAML tarayıcı uygulaması (XBAP)) ana bilgisayar uygulaması tarafından başvurulan bir kitaplık derlemesidir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Page> tarayıcıda barındırılıp barındırılmadığını öğrenmek için <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
