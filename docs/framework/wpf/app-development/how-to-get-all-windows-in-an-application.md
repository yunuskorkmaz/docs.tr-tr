---
title: 'Nasıl yapılır: Bir uygulamadaki tüm Windows Al'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378845"
---
# <a name="how-to-get-all-windows-in-an-application"></a>Nasıl yapılır: Bir uygulamadaki tüm Windows Al
Bu örnek, tüm alınacağı gösterilmektedir <xref:System.Windows.Window> bir uygulamadaki nesneler.  
  
## <a name="example"></a>Örnek  
 Her örneği <xref:System.Windows.Window> nesne, görünür olsun veya olmasın tarafından yönetilen penceresi başvuruları koleksiyonunu otomatik olarak eklenir <xref:System.Windows.Application>ve gelen sunulan <xref:System.Windows.Application.Windows%2A>.  
  
 U numaralandırabilirsiniz <xref:System.Windows.Application.Windows%2A> aşağıdaki kodu kullanarak tüm oluşturulan windows almak için:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
