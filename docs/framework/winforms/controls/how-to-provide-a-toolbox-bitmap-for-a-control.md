---
title: "Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama"
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
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d1ab49b6596c6feaa2ead5bbb92525f0ddb356d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama
Sahip olmak istiyorsanız denetlemek için özel bir simgesi görünür **araç**, kullanarak belirli bir görüntü belirtebilirsiniz <xref:System.Drawing.ToolboxBitmapAttribute>. Bu sınıf, bir *özniteliği*, özel türde bir sınıfı diğer sınıfların iliştirebilirsiniz. Öznitelikler hakkında daha fazla bilgi için bkz: [NOT ın yapı: Visual Basic'te öznitelikler genel bakış](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ve [öznitelikleri](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) için [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].  
  
 Kullanarak <xref:System.Drawing.ToolboxBitmapAttribute>, 16 x 16 piksel bit eşlem için yolu ve dosya adını belirten bir dize belirtin. Bu bit eşlemi eklendiğinde, Denetim yanındaki sonra görünür **araç**. Ayrıca belirtebilirsiniz bir <xref:System.Type>, o türü ile ilişkili bit eşlem; bu durumda yüklenir. Her ikisini de belirtirseniz bir <xref:System.Type> ve tarafından belirtilen türünü içeren bütünleştirilmiş dizesi parametresi tarafından belirtilen ada sahip bir görüntü kaynağı için bir dize denetimi arar <xref:System.Type> parametresi.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Denetim için araç kutusu bit eşlemi belirtmek için  
  
1.  Ekleme <xref:System.Drawing.ToolboxBitmapAttribute> önce denetiminizin sınıfı bildirimine `Class` for anahtar sözcüğü [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]ve için sınıf bildiriminin üstüne [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].  
  
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
  
2.  Projeyi yeniden oluşturun.  
  
    > [!NOTE]
    >  Bit eşlem otomatik olarak oluşturulur denetimleri ve bileşenleri için Araç Kutusu'nda görünmez. Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu. Daha fazla bilgi için bkz: [izlenecek yol: araç kutusunu özel bileşenlerle'otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Windows Forms denetimleri geliştirme tasarım zamanında](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Öznitelikler (Visual Basic)](~/docs/visual-basic/language-reference/attributes.md)  
 [Öznitelikleri](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
