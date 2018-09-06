---
title: 'Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: aa32850b9bcd1a15a93bd6c80b2278278d12c417
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746551"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama
Denetiminiz için özel bir simge görünür olmasını istiyorsanız **araç kutusu**, belirli bir görüntü kullanarak belirtebilirsiniz <xref:System.Drawing.ToolboxBitmapAttribute>. Bu sınıf, bir *özniteliği*, diğer sınıflara iliştirebilirsiniz sınıfı özel bir tür. Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikler genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) Visual Basic veya [öznitelikler (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) C# için.  
  
 Kullanarak <xref:System.Drawing.ToolboxBitmapAttribute>, 16 x 16 piksel bit eşlem yolunu ve dosya adını belirten bir dize belirtebilirsiniz. Bu bit eşlem eklendiğinde denetim ardından yanında **araç kutusu**. Ayrıca belirtebileceğiniz bir <xref:System.Type>, bu durumda, türü ile ilişkili bit eşlem yüklenir. Her ikisini de belirtirseniz bir <xref:System.Type> ve bir dize denetim tarafından belirtilen tür içeren derlemenin dize parametresi tarafından belirtilen ada sahip bir görüntü kaynağı için arar <xref:System.Type> parametresi.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Denetiminiz için bir araç kutusu bit eşlemi belirtmek için  
  
1.  Ekleme <xref:System.Drawing.ToolboxBitmapAttribute> denetiminizin önce sınıf bildirimine `Class` visual Basic ve Visual C# sınıf bildiriminin üstüne anahtar sözcüğü.  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  Projeyi yeniden derleyin.  
  
    > [!NOTE]
    >  Bit eşlem otomatik olarak oluşturulan denetimleri ve bileşenleri için Araç Kutusu'nda görünmez. Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu. Daha fazla bilgi için [izlenecek yol: otomatik olarak, araç kutusunu özel bileşenlerle doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Öznitelikler genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Öznitelikler (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
