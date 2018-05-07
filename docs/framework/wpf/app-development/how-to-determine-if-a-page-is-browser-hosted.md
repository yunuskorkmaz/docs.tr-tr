---
title: 'Nasıl yapılır: bir sayfa tarayıcı barındırılan olup olmadığını belirler'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: 6eb83429cb4f9dac5f3561b41997d24bcaa2c62f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Nasıl yapılır: bir sayfa tarayıcı barındırılan olup olmadığını belirler
Bu örnek belirlemek gösterilmiştir bir <xref:System.Windows.Controls.Page> bir tarayıcı içinde barındırılır.  
  
## <a name="example"></a>Örnek  
 A <xref:System.Windows.Controls.Page> konak belirsiz olabilir ve bu nedenle, konakları dahil olmak üzere, birkaç farklı türde yüklenebilir bir <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, veya bir tarayıcı. Bir veya daha fazla sayfa içerir ve birden fazla tek başına tarafından başvurulan ve gözatılamaz Kitaplık derlemesi olduğunda bu durum oluşabilir ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) barındıran uygulamalar.  
  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> belirlemek için bir <xref:System.Windows.Controls.Page> bir tarayıcıda barındırılan.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
