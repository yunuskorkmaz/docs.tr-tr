---
title: "Nasıl yapılır: ListBoxItem Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e014dc05e24b5337e8e448451244633cb8ed0ff1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-listboxitem"></a>Nasıl yapılır: ListBoxItem Alma
Belirli bir almanız gerekirse <xref:System.Windows.Controls.ListBoxItem> içinde belirli bir dizindeki bir <xref:System.Windows.Controls.ListBox>, kullanabileceğiniz bir <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.ListBox> ve onun öğelerini.  
  
 [!code-xaml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnek, öğenin dizinini belirterek öğeyi almak gösterilmiştir <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> özelliği <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 Liste kutusu öğesi aldıktan sonra aşağıdaki örnekte gösterildiği gibi öğenin içeriğini görüntüleyebilir.  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
