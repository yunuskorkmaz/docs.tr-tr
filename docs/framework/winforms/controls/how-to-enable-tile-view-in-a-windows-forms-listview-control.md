---
title: ListView denetiminde kutucuk görünümünü etkinleştir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 8ccbd42d870e44fc6fd80169327922409ea4f6e7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745469"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
<xref:System.Windows.Forms.ListView> denetimin kutucuk görünümü özelliği ile grafik ve metin bilgileri arasında görsel bir denge sağlayabilirsiniz. Kutucuk görünümündeki bir öğe için görünen metin bilgileri, Ayrıntılar görünümü için tanımlanan sütun bilgileri ile aynıdır. Kutucuk görünümü, <xref:System.Windows.Forms.ListView> denetimindeki gruplandırma ya da ekleme işareti özellikleriyle birlikte kullanılır.  
  
 Kutucuk görünümü, aşağıdaki görüntülerde gösterildiği gibi bir 32 x 32 piksel simgesi ve birkaç satırlık metin kullanır.  
  
 ![ListView denetimindeki kutucuk görünümü](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Kutucuk görünümü simgeleri ve metni")  
 
 Kutucuk görünümünü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Tile>olarak ayarlayın. <xref:System.Windows.Forms.ListView.TileSize%2A> özelliğini ayarlayarak kutucukların boyutunu ve <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonunu ayarlayarak kutucukta görünen metin çizgilerinin sayısını ayarlayabilirsiniz.  
  
### <a name="to-set-tile-view-programmatically"></a>Kutucuk görünümünü programlı bir şekilde ayarlamak için  
  
1. <xref:System.Windows.Forms.ListView> denetiminin <xref:System.Windows.Forms.View> sabit listesini kullanın.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, üç satırlık metin göstermek için değiştirilen kutucukları içeren kutucuk görünümünü gösterir. Kutucuk boyutu, satır kaydırmayı engelleyecek şekilde ayarlandı.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
- Yürütülebilir dosya ile aynı dizinde Book. ico adlı bir simge dosyası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
