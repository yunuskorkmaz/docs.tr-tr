---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme'
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
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966686"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
<xref:System.Windows.Forms.ListView> Denetimin kutucuk görünümü özelliği ile grafik ve metin bilgileri arasında bir görsel denge sağlayabilirsiniz. Kutucuk görünümündeki bir öğe için görünen metin bilgileri, Ayrıntılar görünümü için tanımlanan sütun bilgileri ile aynıdır. Kutucuk görünümü, <xref:System.Windows.Forms.ListView> denetimdeki gruplandırma ya da ekleme işareti özellikleriyle birlikte kullanılır.  
  
 Kutucuk görünümü, aşağıdaki görüntülerde gösterildiği gibi bir 32 x 32 piksel simgesi ve birkaç satırlık metin kullanır.  
  
 ![ListView denetimindeki kutucuk görünümü](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Kutucuk görünümü simgeleri ve metni")  
 
 Kutucuk görünümünü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> özelliğini olarak <xref:System.Windows.Forms.View.Tile>ayarlayın. <xref:System.Windows.Forms.ListView.TileSize%2A> Özelliği ayarlayarak kutucukların boyutunu ve <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu ayarlayarak kutucukta görünen metin çizgilerinin sayısını ayarlayabilirsiniz.  
  
> [!NOTE]
> Kutucuk görünümü yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir. Önceki işletim sistemlerinde, kutucuk görünümüyle ilgili tüm kodlar etkisizdir ve <xref:System.Windows.Forms.ListView> denetim büyük simge görünümünde görüntülenir. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Kutucuk görünümünü programlı bir şekilde ayarlamak için  
  
1. <xref:System.Windows.Forms.ListView> Denetimin <xref:System.Windows.Forms.View> numaralandırmasını kullanın.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
- Yürütülebilir dosya ile aynı dizinde Book. ico adlı bir simge dosyası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
