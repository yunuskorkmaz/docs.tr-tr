---
title: 'Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: a85c0c36ef99e6501afddaca7f26acd2928da1ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550871"
---
# <a name="how-to-share-sizing-properties-between-grids"></a>Nasıl yapılır: Kılavuzlar Arasında Boyutlandırma Özelliklerini Paylaşma
Bu örnek arasındaki satırları ve sütunları boyutlandırma verisinin nasıl paylaşılacağını gösterir <xref:System.Windows.Controls.Grid> boyutlandırmayı tutarlı saklamak için öğeleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki tanıtır <xref:System.Windows.Controls.Grid> öğeler alt öğelerin üst öğesi olarak <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Özelliği bağlı <xref:System.Windows.Controls.Grid> üst öğede tanımlanan <xref:System.Windows.Controls.DockPanel>.  
  
 İki kullanarak örnek özellik değerini yönetir <xref:System.Windows.Controls.Button> öğeleri; bir Boolean özellik değerlerinin her öğesi gösterir. Zaman <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> özellik değeri ayarlanmış `true`, her bir sütun veya satır üyesi bir <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> bir satır veya sütun içeriği ne olursa olsun boyutlandırma bilgi paylaşır.  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki arka plan kodu örnek yöntemleri işler, düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayını başlatır. Bu yöntem çağrılarının sonuçlarını örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğelerini alma dizesi olarak yeni özellik değerlerinin çıktısını almak için yöntemleri.  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
