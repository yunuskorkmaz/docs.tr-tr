---
title: "Nasıl yapılır: ListBox'ın Kayma Performansını Artırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364560"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Nasıl yapılır: ListBox'ın Kayma Performansını Artırma
Varsa bir <xref:System.Windows.Controls.ListBox> sayıda öğe içeren bir kullanıcı kaydırdığında kullanıcı arabirimi yanıt yavaş olabilir <xref:System.Windows.Controls.ListBox> fare tekerleğini kullanarak veya bir kaydırma çubuğunun sürükleyerek. Performansını iyileştirebilir <xref:System.Windows.Controls.ListBox> kullanıcı ne zaman kaydırma ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.ListBox> ve ayarlar `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> kaydırma sırasında performansı geliştirmek için.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
