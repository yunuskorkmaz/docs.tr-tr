---
title: 'Nasıl yapılır: Bir sayfanın tarayıcıda barındırılıp barındırılmadığını belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: ebc5612f059a6cf26f2568bbc08e705b4b3014c1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359997"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="0c2c1-102">Nasıl yapılır: Bir sayfanın tarayıcıda barındırılıp barındırılmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="0c2c1-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="0c2c1-103">Bu örnek belirlemek nasıl gösterir bir <xref:System.Windows.Controls.Page> bir tarayıcıda barındırılır.</span><span class="sxs-lookup"><span data-stu-id="0c2c1-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c2c1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c2c1-104">Example</span></span>  
 <span data-ttu-id="0c2c1-105">A <xref:System.Windows.Controls.Page> konak belirsiz olabilir ve bu nedenle, konakları dahil olmak üzere, birkaç farklı türde yüklenebilir bir <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, veya bir tarayıcı.</span><span class="sxs-lookup"><span data-stu-id="0c2c1-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="0c2c1-106">Bir veya birden çok sayfa içeren ve birden fazla tek başına tarafından başvurulan ve gözatılabilir kitaplık derlemesine sahip olduğunda bu durum oluşabilir ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) uygulamaları barındırın.</span><span class="sxs-lookup"><span data-stu-id="0c2c1-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="0c2c1-107">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> belirlemek için bir <xref:System.Windows.Controls.Page> bir tarayıcıda barındırılır.</span><span class="sxs-lookup"><span data-stu-id="0c2c1-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="0c2c1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c2c1-108">See also</span></span>
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
