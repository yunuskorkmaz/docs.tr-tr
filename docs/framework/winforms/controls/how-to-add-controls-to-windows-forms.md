---
title: "Nasıl yapılır: Windows Formlarına Denetimler Ekleme"
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
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab92f7a56173ec71642d0cc09f3f81e9859533b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-to-windows-forms"></a>Nasıl yapılır: Windows Formlarına Denetimler Ekleme
Çoğu form formun yüzeye denetimler ekleyerek, bir kullanıcı arabirimi (UI) tanımlamak için tasarlanmıştır. A *denetim* bilgilerini görüntülemek veya kullanıcı girişi kabul etmek için kullanılan bir form üzerinde bir bileşenidir. Denetimleri hakkında daha fazla bilgi için bkz: [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-draw-a-control-on-a-form"></a>Bir form üzerinde denetim çizmek için  
  
1.  Formu açın. Daha fazla bilgi için bkz: [nasıl yapılır: görüntü Windows Forms Tasarımcısı'nda](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  İçinde **araç**, formunuza eklemek istediğiniz denetimi tıklatın.  
  
3.  Form yerleştirilecek denetimin sol üst köşesinde istediğiniz yeri tıklatın ve bulunması için denetimin sağ alt köşedeki istediğiniz yere sürükleyin.  
  
     Denetim belirtilen konum ve boyutlarının formla eklenir.  
  
    > [!NOTE]
    >  Her denetim tanımlanan varsayılan boyutuna sahiptir. Bir denetim denetimin varsayılan boyutu formunuzda ondan sürükleyerek ekleyebileceğiniz **araç** form.  
  
### <a name="to-drag-a-control-to-a-form"></a>Forma denetim sürükleyin  
  
1.  Formu açın. Daha fazla bilgi için bkz: [nasıl yapılır: görüntü Windows Forms Tasarımcısı'nda](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  İçinde **araç**, istediğiniz ve formunuza sürükleyin denetimi tıklatın.  
  
     Denetim formun varsayılan boyutuna belirtilen konumda eklenir.  
  
    > [!NOTE]
    >  Denetim içinde çift tıklayarak **araç** varsayılan boyutuna formunda sol üst köşesindeki eklemek için.  
  
     Ayrıca denetimleri dinamik olarak forma çalışma zamanında ekleyebilirsiniz. Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.TextBox> denetim forma eklenecek olduğunda bir <xref:System.Windows.Forms.Button> denetim tıklandığında.  
  
    > [!NOTE]
    >  Aşağıdaki yordam bir formla gerekir. bir **düğmesini** denetimi `Button1`, üzerindeki zaten yerleştirilmiş.  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>Program aracılığıyla bir forma denetim eklemek için  
  
1.  Düğmenin işleme yöntemi `Click` , formun sınıftaki ekleme kodu, denetim değişkeni bir başvuru eklemek için aşağıdakine benzer olay ayarlamak denetimin `Location`ve denetim ekleyin.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  Diğer denetim özelliklerini başlatmak için kod de ekleyebilirsiniz.  
  
    > [!IMPORTANT]
    >  Yerel bir güvenlik riski ağ üzerinden bilgisayarınıza bir kötü amaçlı başvurarak doğurabilir `UserControl`. Bu, yalnızca, yanlışlıkla projenize ekleme ve ardından zararlı olabilecek özel bir denetim oluşturma kötü niyetli bir kişi olması durumunda ilgili bir sorun olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Nasıl yapılır: Windows Forms’da Denetimleri Yeniden Boyutlandırma](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
