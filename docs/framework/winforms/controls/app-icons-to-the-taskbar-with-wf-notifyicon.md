---
title: "Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme"
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
ms.openlocfilehash: 05b6f300afea4671c1a847b116b378514ecb8b56
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959510"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme

Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşen durumu görev çubuğu bildirim alanında tek bir simge görüntüler. Durum alanında birden fazla simgeleri göstermek için birden çok sahip <xref:System.Windows.Forms.NotifyIcon> formunuzdaki bileşenleri. Bir denetim için görüntülenen simgenin ayarlamak için kullanın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği. Ayrıca kod yazabileceğiniz <xref:System.Windows.Forms.NotifyIcon.DoubleClick> kullanıcı simgesine tıkladığında bu şey için olay işleyicisi. Örneğin, bir iletişim kutusu kullanıcının simgesiyle gösterilen arka plan işlemi yapılandırmak görünür yapabilirsiniz.

> [!NOTE]
> <xref:System.Windows.Forms.NotifyIcon> Çeşit durumundaki bir değişiklik veya bileşen yalnızca, bildirim amacıyla bir eylem veya olayın oluştuğunu kullanıcıları uyarmak üzere kullanılır. Menüleri, araç çubukları ve diğer kullanıcı arabirimi öğeleri uygulamalarla standart etkileşim için kullanmanız gerekir.

### <a name="to-set-the-icon"></a>Simge ayarlamak için

1. Bir değer atayın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği. Değer türü olmalıdır `System.Drawing.Icon` ve bir .ico dosyasını yüklenebilir. Simge dosyası üç nokta düğmesine tıklayarak ya da kod belirtebilirsiniz (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) yanındaki <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğinde **özellikleri** Pencere seçip ardından dosyasında **açık** görüntülenen iletişim kutusunda.

2. Ayarlama <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğini `true`.

3. Ayarlama <xref:System.Windows.Forms.NotifyIcon.Text%2A> uygun bir araç ipucu dize özelliği.

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
- [Nasıl yapılır: Bir kısayol menüsünü Windows Forms Notifyıcon bileşeniyle ilişkilendirme](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon Bileşeni](notifyicon-component-windows-forms.md)
- [NotifyIcon Bileşenine Genel Bakış](notifyicon-component-overview-windows-forms.md)
