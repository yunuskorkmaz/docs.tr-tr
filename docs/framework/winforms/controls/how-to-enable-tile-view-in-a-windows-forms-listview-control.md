---
title: Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
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
ms.openlocfilehash: 4eb418bbd2d399c57ce4a8235130a9939be56ce4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480974"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
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
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP özellikleri ve Windows Forms denetimleri](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
