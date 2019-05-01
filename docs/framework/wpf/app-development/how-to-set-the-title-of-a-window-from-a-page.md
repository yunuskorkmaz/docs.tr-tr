---
title: 'Nasıl yapılır: Bir Sayfadan Pencere Başlığını Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054009"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Nasıl yapılır: Bir Sayfadan Pencere Başlığını Ayarlama
Bu örnek nasıl pencerenin başlığı ayarlayın gösterir bir <xref:System.Windows.Controls.Page> barındırılır.  
  
## <a name="example"></a>Örnek  
 Bir sayfa ayarlayarak barındıran pencerenin başlığı değiştirebilirsiniz <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliği şu şekilde:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Ayar <xref:System.Windows.Controls.Page.Title%2A> özellik sayfasının, pencere başlığı değerini değiştirmez. Bunun yerine, <xref:System.Windows.Controls.Page.Title%2A> Gezinme geçmişi içinde bir sayfa girişi adını belirtir.
