---
title: 'Nasıl yapılır: Bir Sayfadan Pencere Yüksekliğini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940794"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Nasıl yapılır: Bir Sayfadan Pencere Yüksekliğini Ayarlama
Bu örnek, ' dan <xref:System.Windows.Controls.Page>pencerenin yüksekliğinin nasıl ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Page> , Ayarlayarak<xref:System.Windows.Controls.Page.WindowHeight%2A>ana penceresinin yüksekliğini ayarlayabilir. Bu özellik, <xref:System.Windows.Controls.Page> uygulamasının kendisini barındıran pencere türü hakkında açık bilgisine sahip olmasına izin verir.  
  
> [!NOTE]
> Bir pencerenin yüksekliğini kullanarak <xref:System.Windows.Controls.Page.WindowHeight%2A>ayarlamak için, bir <xref:System.Windows.Controls.Page> pencerenin alt öğesi olmalıdır.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
