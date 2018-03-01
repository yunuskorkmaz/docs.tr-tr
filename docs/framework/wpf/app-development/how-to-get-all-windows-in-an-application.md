---
title: "Nasıl yapılır: bir uygulamadaki tüm pencereleri Al"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fdb1baad8b779b6ef0443a05e5f6575b552b1c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a>Nasıl yapılır: bir uygulamadaki tüm pencereleri Al
Bu örnek, tüm alma gösterir <xref:System.Windows.Window> bir uygulamadaki nesneler.  
  
## <a name="example"></a>Örnek  
 Her örneği <xref:System.Windows.Window> nesne görünür olup olmadığını veya değil, bir koleksiyon tarafından yönetilen pencere referansları otomatik olarak eklenir <xref:System.Windows.Application>ve tan açığa çıkarılan <xref:System.Windows.Application.Windows%2A>.  
  
 Numaralandırmak <xref:System.Windows.Application.Windows%2A> aşağıdaki kodu kullanarak tüm oluşturulan pencereleri almak için:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
