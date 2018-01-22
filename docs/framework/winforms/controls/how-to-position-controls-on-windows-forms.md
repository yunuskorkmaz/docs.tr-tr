---
title: "Nasıl yapılır: Windows Formlarında Denetimleri Konumlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4519be86d83fce5afc7410c9f76591158ed71cb6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-position-controls-on-windows-forms"></a>Nasıl yapılır: Windows Formlarında Denetimleri Konumlandırma
Denetimleri getirin, Windows Form Tasarımcısı kullanın veya belirtmek için <xref:System.Windows.Forms.Control.Location%2A> özelliği.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Windows Form Tasarımcısı tasarım yüzeyine denetim konumlandırmak için  
  
-   Denetim fareyle uygun konuma sürükleyin.  
  
    > [!NOTE]
    >  Denetimi seçin ve onu oklu daha kesin olarak konumlandırmak için anahtarları taşıyın. Ayrıca, *dayama çizgileri* tam olarak formunuza denetimler yerleştirme yardımcı. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak dayama çizgileri düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
### <a name="to-position-a-control-using-the-properties-window"></a>Özellikler penceresini kullanarak denetim konumlandırmak için  
  
1.  Yerleştirmek istediğiniz denetimi tıklatın.  
  
2.  İçinde **özellikleri** penceresinde, türü değerleri için <xref:System.Windows.Forms.Control.Location%2A> kontrolün kapsayıcı içindeki denetim konumuna bağlı olarak, bir virgülle ayrılmış özelliği.  
  
     İlk (X) kapsayıcısının sol kenarlık mesafe sayısıdır; İkinci (Y) üst kenarlığın piksel cinsinden ölçülür kapsayıcı alanının mesafe sayıdır.  
  
    > [!NOTE]
    >  Genişletebilirsiniz <xref:System.Windows.Forms.Control.Location%2A> türü için özellik **X** ve **Y** ayrı ayrı değerleri.  
  
### <a name="to-position-a-control-programmatically"></a>Bir denetim programlı olarak konumlandırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Location%2A> denetiminin özelliği bir <xref:System.Drawing.Point>.  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  Denetimin konumunun X koordinatını değiştirme kullanarak <xref:System.Windows.Forms.Control.Left%2A> alt özellik öneki.  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>Bir denetimin konumunu programlı olarak artırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Left%2A> denetimi X koordinatını artırmak için alt özellik öneki.  
  
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
    >  Kullanım <xref:System.Windows.Forms.Control.Location%2A> bir denetimin X ve Y ayarlamak için özellik aynı anda yerleştirir. Tek tek bir konum ayarlamak için denetimin kullanın <xref:System.Windows.Forms.Control.Left%2A> (**X**) veya <xref:System.Windows.Forms.Control.Top%2A> (**Y**) alt özellik öneki. X ve Y koordinatları örtük olarak ayarlamaya çalışmayın <xref:System.Drawing.Point> bu yapı düğmenin koordinatları bir kopyasını içerdiğinden düğmenin konumu temsil eden yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Nasıl yapılır: Windows Forms ekran konumunu ayarlama](http://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
