---
title: 'Nasıl yapılır: Sayfanın Tarayıcıda Barındırılıp Barındırılmadığını Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: d154de2f885101d1bd0c4613dfb1604be8acbe6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978347"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Nasıl yapılır: Sayfanın Tarayıcıda Barındırılıp Barındırılmadığını Belirleme
Bu örnek belirlemek nasıl gösterir bir <xref:System.Windows.Controls.Page> bir tarayıcıda barındırılır.  
  
## <a name="example"></a>Örnek  
 A <xref:System.Windows.Controls.Page> konak belirsiz olabilir ve bu nedenle, konakları dahil olmak üzere, birkaç farklı türde yüklenebilir bir <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, veya bir tarayıcı. Bir veya birden çok sayfa içeren ve birden fazla tek başına tarafından başvurulan ve gözatılabilir kitaplık derlemesine sahip olduğunda bu durum oluşabilir ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) uygulamaları barındırın.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> belirlemek için bir <xref:System.Windows.Controls.Page> bir tarayıcıda barındırılır.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
