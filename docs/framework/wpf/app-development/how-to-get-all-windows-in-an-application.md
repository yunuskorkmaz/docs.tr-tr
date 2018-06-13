---
title: 'Nasıl yapılır: bir uygulamadaki tüm pencereleri Al'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545497"
---
# <a name="how-to-get-all-windows-in-an-application"></a>Nasıl yapılır: bir uygulamadaki tüm pencereleri Al
Bu örnek, tüm alma gösterir <xref:System.Windows.Window> bir uygulamadaki nesneler.  
  
## <a name="example"></a>Örnek  
 Her örneği <xref:System.Windows.Window> nesne görünür olup olmadığını veya değil, bir koleksiyon tarafından yönetilen pencere referansları otomatik olarak eklenir <xref:System.Windows.Application>ve tan açığa çıkarılan <xref:System.Windows.Application.Windows%2A>.  
  
 Numaralandırmak <xref:System.Windows.Application.Windows%2A> aşağıdaki kodu kullanarak tüm oluşturulan pencereleri almak için:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
