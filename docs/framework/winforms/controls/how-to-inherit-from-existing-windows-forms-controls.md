---
title: 'Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: f19b207c840994ffa3aa364135583b5daeb26827
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542290"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma
Varolan bir denetimi işlevlerini genişletmek istiyorsanız, varolan bir denetimi devralma yoluyla türetilen bir denetim oluşturabilirsiniz. Varolan bir denetimden devralınırken tüm işlevleri ve denetim görsel özelliklerini devralır. Örneğin, devralınan bir denetim oluşturuyorsanız <xref:System.Windows.Forms.Button>, yeni denetiminizin görünür ve Yasası tam gibi standart <xref:System.Windows.Forms.Button> denetimi. Ardından genişletin veya yeni, denetimin özel yöntemleri ve özellikleri uygulaması aracılığıyla işlevselliğini değiştirmenize. Bazı denetimler, ayrıca, devralınan denetim görsel görünümünü geçersiz kılarak değiştirebilirsiniz, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-inherited-control"></a>Devralınan bir denetim oluşturmak için  
  
1.  Yeni bir **Windows Forms uygulaması** proje.  
  
2.  Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, çift **özel denetim**.  
  
     Yeni özel denetim projenize eklenir.  
  
4.  Varsa, Visual Basic kullanarak en üstündeki **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**. CustomControl1.vb genişletin ve ardından CustomControl1.Designer.vb kod Düzenleyicisi'nde açın.  
  
5.  C# kullanıyorsanız CustomControl1.cs Kod Düzenleyicisi'nde açın.  
  
6.  Öğesinden devralan sınıf bildiriminin bulun <xref:System.Windows.Forms.Control>.  
  
7.  Verileri devralmak istediğiniz denetlemek için temel sınıf değiştirin.  
  
     Örneğin devralınacak istiyorsanız <xref:System.Windows.Forms.Button>, sınıf bildiriminin aşağıdakiyle değiştirin:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Visual Basic kullanıyorsanız, kaydedin ve CustomControl1.Designer.vb kapatın. CustomControl1.vb kod Düzenleyicisi'nde açın.  
  
9. Herhangi bir özel yöntemler veya denetiminiz birleştirecektir özellikleri uygulayın.  
  
10. Grafik görünümünü değiştirmek istiyorsanız, geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
    > [!NOTE]
    >  Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> tüm denetimlerin görünümünü değiştirmenizi izin vermez. Kendi boyama Windows tarafından yapılan tüm bu denetimler (örneğin, <xref:System.Windows.Forms.TextBox>) hiçbir zaman çağrısı kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve dolayısıyla kullanım özel kod hiçbir zaman. Olmadığını görmek için değiştirmek istediğiniz belirli denetim için Yardım belgelerine başvurun <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi kullanılabilir. Tüm Windows Form denetimleri listesi için bkz. [Windows Forms'da kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Bir denetim yoksa <xref:System.Windows.Forms.Control.OnPaint%2A> üye yöntemi olarak listelenen, görünümünü bu yöntemi geçersiz kılarak değiştirilemiyor. Özel boyama hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
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
  
11. Kaydet ve denetim test edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Nasıl yapılır: Denetim Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Nasıl yapılır: UserControl Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Nasıl yapılır: Windows Forms için Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
