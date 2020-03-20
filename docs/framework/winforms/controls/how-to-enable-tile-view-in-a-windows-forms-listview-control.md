---
title: ListView Denetiminde Döşeme Görünümü etkinleştirme
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
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182160"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
<xref:System.Windows.Forms.ListView> Denetimin döşeme görünümü özelliği yle, grafik ve metinsel bilgiler arasında görsel bir denge sağlayabilirsiniz. Döşeme görünümünde bir öğe için görüntülenen metin bilgileri, ayrıntılar görünümü için tanımlanan sütun bilgileriyle aynıdır. Döşeme <xref:System.Windows.Forms.ListView> görünümü, denetimdeki gruplandırma veya ekleme işareti özellikleriyle birlikte çalışır.  
  
 Döşeme görünümü, aşağıdaki resimlerde gösterildiği gibi 32 x 32 piksel simgesi ve birkaç metin satırı kullanır.  
  
 ![ListView Denetiminde Döşeme Görünümü](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Döşeme görünümü simgeleri ve metin")  

 Döşeme görünümünü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> <xref:System.Windows.Forms.View.Tile>özelliği ' niçin ayarla <xref:System.Windows.Forms.ListView.TileSize%2A> Özelliği ayarlayarak kutucukların boyutunu ve <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu ayarlayarak kutucukta görüntülenen metin satırlarının sayısını ayarlayabilirsiniz.  
  
### <a name="to-set-tile-view-programmatically"></a>Döşeme görünümünü programlı olarak ayarlamak için  
  
1. Denetimin <xref:System.Windows.Forms.View> numaralandırmasını <xref:System.Windows.Forms.ListView> kullanın.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam kod örneği, üç metin satırı göstermek üzere değiştirilmiş kutucuklarla Kutucuk görünümünü gösterir. Döşeme boyutu, satır kaydırmayı önlemek için ayarlanmış.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
- Yürütülebilir dosyayla aynı dizinde book.ico adlı bir simge dosyası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
