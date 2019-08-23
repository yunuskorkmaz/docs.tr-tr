---
title: 'Nasıl yapılır: Bir Sayfadan Pencere Genişliğini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940772"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Nasıl yapılır: Bir Sayfadan Pencere Genişliğini Ayarlama
Bu örnek, ' dan <xref:System.Windows.Controls.Page>pencerenin genişliğinin nasıl ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Page> , Ayarlayarak<xref:System.Windows.Controls.Page.WindowWidth%2A>ana penceresinin genişliğini ayarlayabilir. Bu özellik, <xref:System.Windows.Controls.Page> uygulamasının kendisini barındıran pencere türü hakkında açık bilgisine sahip olmasına izin verir.  
  
> [!NOTE]
> Bir pencerenin genişliğini kullanarak <xref:System.Windows.Controls.Page.WindowWidth%2A>ayarlamak için, bir <xref:System.Windows.Controls.Page> pencerenin alt öğesi olmalıdır.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
