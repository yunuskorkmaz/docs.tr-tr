---
title: 'Nasıl yapılır: Windows Forms ListView denetiminde döşeme görünümünü etkinleştirme'
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
ms.openlocfilehash: 34e7025ab29ec2e0d2035fa07f2a6d53c2b197c9
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261719"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView denetiminde döşeme görünümünü etkinleştirme
Döşeme görünümü özelliği ile <xref:System.Windows.Forms.ListView> denetimi, grafik ve metinsel bilgileri arasında görsel bir denge sağlayabilir. Kutucuk görünümde bir öğe için görüntülenen metin tabanlı bilgiler tanımlanan ayrıntı görünümü için sütun bilgileri ile aynıdır. Kutucuk görünümü gruplandırma veya ekleme işareti özellikleri ile birlikte çalışır <xref:System.Windows.Forms.ListView> denetimi.  
  
 Kutucuk görünümü aşağıdaki görüntüde gösterildiği gibi bir 32 x 32 piksel simgesi ve birkaç satırlık metin kullanır.  
  
 ![Görünüm ListView denetiminde döşeme](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
Kutucuk görünümü simge ve metin  
  
 Kutucuk görünümü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Tile>. Kutucukların boyutunu ayarlayarak yapabilirsiniz <xref:System.Windows.Forms.ListView.TileSize%2A> özelliği ve metin satırı ayarlayarak kutucuğunda görüntülenen <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu.  
  
> [!NOTE]
>  Kutucuk görünümü yalnızca üzerinde kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde kutucuk görünümüne ilgili herhangi bir kod bir etkisi yoktur ve <xref:System.Windows.Forms.ListView> denetimi büyük simge görünümünde görüntüler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Kutucuk görünümü program üzerinden ayarlamak için  
  
1.  Kullanım <xref:System.Windows.Forms.View> numaralandırması <xref:System.Windows.Forms.ListView> denetimi.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tam örneği kutucuk görünümü kutucukları içeren üç satır metin göstermek için değişiklik gösterir. Satır kaydırma önlemek için döşeme boyutunu ayarlandı.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
-   Bir simge dosyası yürütülebilir dosyayla aynı dizinde book.ico adı.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
