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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="7a3d3-102">Nasıl yapılır: bir sayfanın tarayıcıda barındırılıp barındırılmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="7a3d3-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="7a3d3-103">Bu örnek, bir <xref:System.Windows.Controls.Page> tarayıcıda barındırılıp barındırılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a3d3-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a3d3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a3d3-104">Example</span></span>  
 <span data-ttu-id="7a3d3-105"><xref:System.Windows.Controls.Page> ana bilgisayar belirsiz olabilir ve sonuç olarak, <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>veya tarayıcı dahil olmak üzere birkaç farklı türde konağa yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7a3d3-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="7a3d3-106">Bu durum, bir veya daha fazla sayfa içeren bir kitaplık derlemeniz varsa ve birden çok tek başına ve gözatılabilir (XAML tarayıcı uygulaması (XBAP)) ana bilgisayar uygulaması tarafından başvurulan bir kitaplık derlemesidir.</span><span class="sxs-lookup"><span data-stu-id="7a3d3-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable (XAML browser application (XBAP)) host applications.</span></span>  
  
 <span data-ttu-id="7a3d3-107">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Page> tarayıcıda barındırılıp barındırılmadığını öğrenmek için <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a3d3-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="7a3d3-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a3d3-108">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
