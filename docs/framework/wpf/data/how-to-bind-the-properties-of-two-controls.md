---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974811"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Nasıl yapılır: İki Denetimin Özelliklerini Bağlama

Bu örnek, bir örneği oluşturulan denetimin özelliğinin, <xref:System.Windows.Data.Binding.ElementName%2A> özelliğini kullanarak başka birine nasıl bağlanacağını gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Panel.Background%2A> özelliğinin bir <xref:System.Windows.Controls.ComboBox>[Selectedidıtem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) özelliğine nasıl bağlanacağını gösterir:

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

Bu örnek işlendiğinde aşağıdaki gibi görünür:

![Yeşil ve yeşil kare değeri olan bir Birleşik giriş kutusunu gösteren ekran görüntüsü.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> Bağlama hedefi özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlama Kaynağı Belirtme](how-to-specify-the-binding-source.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
