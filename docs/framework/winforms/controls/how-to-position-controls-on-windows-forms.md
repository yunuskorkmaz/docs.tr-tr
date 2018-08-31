---
title: 'Nasıl yapılır: Windows Formlarında Denetimleri Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 6843c22fec964de92c41760f1108d1c83e1f5bf8
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332487"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Nasıl yapılır: Windows Formlarında Denetimleri Konumlandırma
Yerleştirmenize, Windows Forms Tasarımcısı'nı kullanın veya belirtmek için <xref:System.Windows.Forms.Control.Location%2A> özelliği.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Windows Form Tasarımcısı'nın tasarım yüzeyinde bir denetimi konumlandırmak için  
  
-   Denetim fare ile uygun konuma sürükleyin.  
  
    > [!NOTE]
    >  Denetimi seçin ve bunu bir ok ile daha hassas şekilde yerleştirmek için anahtarları taşıyın. Ayrıca, *dayama çizgileri* tam olarak, form üzerindeki denetimleri yerleştirme yardımcı. Daha fazla bilgi için [izlenecek yol: Windows Forms dayama çizgileri kullanarak düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
### <a name="to-position-a-control-using-the-properties-window"></a>Özellikler penceresini kullanarak bir denetimi konumlandırmak için  
  
1.  Yerleştirmek istediğiniz denetim tıklayın.  
  
2.  İçinde **özellikleri** penceresinde, tür değerleri için <xref:System.Windows.Forms.Control.Location%2A> denetim kapsayıcısı içinden konumuna bağlı olarak, bir virgülle ayrılmış bir özellik.  
  
     İlk (X) kapsayıcısının sol kenarlık mesafe sayısıdır; İkinci (Y) üst kenarlığın piksel cinsinden ölçülen kapsayıcı alanının mesafe sayısıdır.  
  
    > [!NOTE]
    >  İstediğiniz ölçekte çalışma yapabilirsiniz <xref:System.Windows.Forms.Control.Location%2A> türü için özellik **X** ve **Y** ayrı ayrı değerler.  
  
### <a name="to-position-a-control-programmatically"></a>Bir denetimin program aracılığıyla konumlandırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Location%2A> denetimin özellik bir <xref:System.Drawing.Point>.  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  Denetim konumunun X koordinatını değiştirme kullanarak <xref:System.Windows.Forms.Control.Left%2A> alt özellik.  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>Bir denetimin konumu programlı olarak artırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Left%2A> denetim noktasının X koordinatı artırmak için alt özellik.  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  Kullanım <xref:System.Windows.Forms.Control.Location%2A> denetimin X ve Y ayarlamak için özellik aynı anda yerleştirir. Tek tek bir konum belirlemek için denetimin kullanın <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özellik. X ve Y koordinatları örtük olarak ayarlamaya çalışmayın <xref:System.Drawing.Point> bu yapı düğmenin koordinatları bir kopyasını içerdiğinden düğmenin konumu temsil eden yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Nasıl yapılır: Windows formlarının ekran konumunu ayarlama](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
