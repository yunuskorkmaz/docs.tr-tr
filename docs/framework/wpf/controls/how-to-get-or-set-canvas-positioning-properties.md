---
title: 'Nasıl yapılır: Tuval Konumlandırma Özelliklerini Alma veya Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 06508e1198736ccb1cbda41641dff4bc634ef82b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194415"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>Nasıl yapılır: Tuval Konumlandırma Özelliklerini Alma veya Ayarlama
Bu örnek, yerleştirme yöntemlerini kullanmayı gösterir. <xref:System.Windows.Controls.Canvas> alt konumlandırmak için öğesi. Bu örnekte bu içerikte bir <xref:System.Windows.Controls.ListBoxItem> temsil etmek için konumlandırma değerler ve değerlerin örneğine dönüştürür <xref:System.Double>, yerleştirme için gerekli bir bağımsız değişken olduğu. Değerlerin geri dizelere dönüştürülür ve metin olarak görüntülenen bir <xref:System.Windows.Controls.TextBlock> kullanarak öğesi <xref:System.Windows.Controls.Canvas.GetLeft%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.ListBox> seçilebilir on sahip öğe <xref:System.Windows.Controls.ListBoxItem> öğeleri. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Olay tetikleyicilerini `ChangeLeft` sonraki kod bloğu tanımlar özel yöntemi.  
  
 Her <xref:System.Windows.Controls.ListBoxItem> temsil eden bir <xref:System.Double> bağımsız değişkenlerden biri olan değeri, <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemi <xref:System.Windows.Controls.Canvas> kabul eder. Kullanmak için bir <xref:System.Windows.Controls.ListBoxItem> örneğini temsil eden <xref:System.Double>, dönüştürmeniz gerekir <xref:System.Windows.Controls.ListBoxItem> doğru veri türü.  
  
 [!code-xaml[CanvasPositioningProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Bir kullanıcı değiştiğinde <xref:System.Windows.Controls.ListBox> seçimi çağırdığı `ChangeLeft` özel yöntemi. Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.LengthConverter> dönüştüren nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Double> (Bu değer için zaten dönüştürülmüş bildirimi bir <xref:System.String> kullanarak <xref:System.Windows.Controls.Control.ToString%2A> yöntemi). Bu değer daha sonra geri geçirilir <xref:System.Windows.Controls.Canvas.SetLeft%2A> ve <xref:System.Windows.Controls.Canvas.GetLeft%2A> yöntemlerinin <xref:System.Windows.Controls.Canvas> konumunu değiştirmek için `text1` nesne.  
  
 [!code-csharp[CanvasPositioningProperties#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [Panellere Genel Bakış](panels-overview.md)
