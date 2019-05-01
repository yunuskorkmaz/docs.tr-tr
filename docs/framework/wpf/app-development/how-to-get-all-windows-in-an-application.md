---
title: 'Nasıl yapılır: Bir Uygulamadaki Tüm Pencereleri Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947777"
---
# <a name="how-to-get-all-windows-in-an-application"></a>Nasıl yapılır: Bir Uygulamadaki Tüm Pencereleri Alma
Bu örnek, tüm alınacağı gösterilmektedir <xref:System.Windows.Window> bir uygulamadaki nesneler.  
  
## <a name="example"></a>Örnek  
 Her örneği <xref:System.Windows.Window> nesne, görünür olsun veya olmasın tarafından yönetilen penceresi başvuruları koleksiyonunu otomatik olarak eklenir <xref:System.Windows.Application>ve gelen sunulan <xref:System.Windows.Application.Windows%2A>.  
  
 U numaralandırabilirsiniz <xref:System.Windows.Application.Windows%2A> aşağıdaki kodu kullanarak tüm oluşturulan windows almak için:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
