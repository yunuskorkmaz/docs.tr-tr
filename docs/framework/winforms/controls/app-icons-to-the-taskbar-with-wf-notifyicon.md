---
title: "Nasıl yapılır: Windows Forms Notifyıcon bileşeni taskbar'na uygulama simgeleri ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 925134e4a0317322d7a4f4cfdc9ac8e3780cf9e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650710"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Nasıl yapılır: Windows Forms Notifyıcon bileşeni taskbar'na uygulama simgeleri ekleme
Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşen durumu görev çubuğu bildirim alanında tek bir simge görüntüler. Durum alanında birden fazla simgeleri göstermek için birden çok sahip <xref:System.Windows.Forms.NotifyIcon> formunuzdaki bileşenleri. Bir denetim için görüntülenen simgenin ayarlamak için kullanın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği. Ayrıca kod yazabileceğiniz <xref:System.Windows.Forms.NotifyIcon.DoubleClick> kullanıcı simgesine tıkladığında bu şey için olay işleyicisi. Örneğin, bir iletişim kutusu kullanıcının simgesiyle gösterilen arka plan işlemi yapılandırmak görünür yapabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> Çeşit durumundaki bir değişiklik veya bileşen yalnızca, bildirim amacıyla bir eylem veya olayın oluştuğunu kullanıcıları uyarmak üzere kullanılır. Menüleri, araç çubukları ve diğer kullanıcı arabirimi öğeleri uygulamalarla standart etkileşim için kullanmanız gerekir.  
  
### <a name="to-set-the-icon"></a>Simge ayarlamak için  
  
1.  Bir değer atayın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği. Değer türü olmalıdır `System.Drawing.Icon` ve bir .ico dosyasını yüklenebilir. Simge dosyası üç nokta düğmesine tıklayarak ya da kod belirtebilirsiniz (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğinde  **Özellikleri** penceresi ve sonra dosyayı seçerek **açık** görüntülenen iletişim kutusunda.  
  
2.  Ayarlama <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğini `true`.  
  
3.  Ayarlama <xref:System.Windows.Forms.NotifyIcon.Text%2A> uygun bir araç ipucu dize özelliği.  
  
     Aşağıdaki kod örneğinde yolunu ayarlamak için simgenin konumunu **Belgelerim** klasör. Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır. Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar sağlar. Aşağıdaki örnek bir formla gerektiren bir <xref:System.Windows.Forms.NotifyIcon> denetim zaten eklendi. Adlı bir simge dosyası aynı zamanda gerektirir `Icon.ico`.  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Nasıl yapılır: Bir kısayol menüsünü Windows Forms Notifyıcon bileşeniyle ilişkilendirme](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon Bileşeni](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
- [NotifyIcon Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
