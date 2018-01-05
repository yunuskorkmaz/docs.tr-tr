---
title: "Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma"
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
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6049e5e0f2d79bab8ad90b6e63e91d4d4fa705ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma
Varolan bir denetim işlevselliğini genişletmek istiyorsanız, varolan denetimi devralma yoluyla türetilmiş bir denetim oluşturabilirsiniz. Varolan denetimden devralırken tüm işlevleri ve bu denetim görsel özelliklerini devralır. Örneğin, devralınan bir denetim oluşturuyorsanız <xref:System.Windows.Forms.Button>, yeni denetim görünür ve act tam gibi standart bir <xref:System.Windows.Forms.Button> denetim. Sonra genişletin veya yeni denetiminiz özel yöntemleri ve özellikleri uyarlamasını aracılığıyla işlevlerini değiştirin. Bazı denetimler de devralınan denetim görsel görünümünü geçersiz kılarak değiştirebilirsiniz kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-inherited-control"></a>Devralınan bir denetim oluşturmak için  
  
1.  Yeni bir **Windows Forms uygulaması** projesi.  
  
2.  Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, çift **özel denetimi**.  
  
     Yeni bir özel denetim projenize eklenir.  
  
4.  Varsa, Visual Basic en üstünde kullanarak **Çözüm Gezgini**, tıklatın **tüm dosyaları göster**. CustomControl1.vb genişletin ve ardından CustomControl1.Designer.vb kod düzenleyicisinde açın.  
  
5.  C# kullanıyorsanız CustomControl1.cs kod düzenleyicisinde açın.  
  
6.  Devraldığı sınıfı bildirimini bulun <xref:System.Windows.Forms.Control>.  
  
7.  Devralınan istediğiniz denetlemek için temel sınıf değiştirin.  
  
     Örneğin, devralınan istiyorsanız <xref:System.Windows.Forms.Button>, sınıf bildirimi şu şekilde değiştirin:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Visual Basic kullanıyorsanız, kaydedin ve CustomControl1.Designer.vb kapatın. CustomControl1.vb kod düzenleyicisinde açın.  
  
9. Herhangi bir özel yöntemler veya denetiminizi dahil özellikler uygular.  
  
10. Grafik, denetimin görünümünü değiştirmek istiyorsanız, geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
    > [!NOTE]
    >  Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> tüm denetimlerin görünümünü değiştirmenizi izin vermez. Tüm Windows tarafından yapılan kendi boyama bu denetimleri (örneğin, <xref:System.Windows.Forms.TextBox>) hiçbir zaman çağrı kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve bu nedenle hiçbir zaman kullanım özel kod. Olmadığını görmek için değiştirmek istediğiniz belirli denetim için Yardım belgelerine başvurun <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi kullanılabilir. Tüm Windows Form denetimlerini listesi için bkz: [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Bir denetim yoksa <xref:System.Windows.Forms.Control.OnPaint%2A> üye yöntemi olarak listelenen, size görünümünü bu yöntemi geçersiz kılarak değiştirilemiyor. Özel boyama hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. Kaydet ve denetiminizin sınayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Nasıl yapılır: Denetim Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Nasıl yapılır: UserControl Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Nasıl yapılır: Windows Forms için Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
