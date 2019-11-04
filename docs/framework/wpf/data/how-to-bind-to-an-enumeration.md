---
title: 'Nasıl yapılır: Numaralandırmaya Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454444"
---
# <a name="how-to-bind-to-an-enumeration"></a>Nasıl yapılır: Numaralandırmaya Bağlama
Bu örnek, numaralandırmanın GetValues yöntemine bağlama yoluyla bir numaralandırmaya nasıl bağlanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Controls.ListBox>, veri bağlama aracılığıyla <xref:System.Windows.HorizontalAlignment> numaralandırma değerlerinin listesini görüntüler. <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.ListBox>bir değer seçerek <xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özellik değerini değiştirebilmeniz için bağlanır.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Yönteme Bağlama](how-to-bind-to-a-method.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
