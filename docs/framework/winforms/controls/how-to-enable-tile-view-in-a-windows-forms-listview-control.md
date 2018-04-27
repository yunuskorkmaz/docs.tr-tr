---
title: Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c416a83d6a5303203de85d7f051252e794b4e30b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme
Döşeme görünümü özelliği ile <xref:System.Windows.Forms.ListView> denetim, grafik ve metin bilgi arasında görsel bir denge sağlayabilir. Döşeme görünümde bir öğe için görüntülenen metin bilgileri, ayrıntı görünümü için tanımlanan sütun bilgileri ile aynıdır. Döşeme görünümü gruplandırma veya ekleme işareti özellikleri ile birlikte çalışır <xref:System.Windows.Forms.ListView> denetim.  
  
 Döşeme görünümü bir 32 x 32 piksel simgesi ve birkaç satırlık metin, aşağıdaki görüntüleri gösterildiği gibi kullanır.  
  
 ![Görünüm ListView denetiminde döşeme](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
Döşeme görünümü simgeler ve metin  
  
 Döşeme görünümü etkinleştirmek için ayarlanmış <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Tile>. Ayarlayarak döşeme boyutunu ayarlayabilirsiniz <xref:System.Windows.Forms.ListView.TileSize%2A> özelliği ve ayarlayarak kutucukta görüntülenen metin satırı sayısını <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu.  
  
> [!NOTE]
>  Döşeme görünümü yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde döşeme görünümüne ilgili herhangi bir kod herhangi bir etkisi olmaz ve <xref:System.Windows.Forms.ListView> denetimi büyük simge görünümünü görüntüler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Döşeme görünümü programlı olarak ayarlamak için  
  
1.  Kullanım <xref:System.Windows.Forms.View> numaralandırması <xref:System.Windows.Forms.ListView> denetim.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam kod örneğinde üç satırlık metin göstermek için değişiklik döşeme ile döşeme görünümünü gösterir. Döşeme boyutunu satır kaydırma önlemek için düzeltildi.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
-   Bir simge dosyası yürütülebilir dosya ile aynı dizinde book.ico adlı.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP özellikleri ve Windows Forms denetimleri](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
