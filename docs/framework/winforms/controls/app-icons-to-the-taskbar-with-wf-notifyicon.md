---
title: Uygulama simgelerini NotifyIcon bileşeniyle birlikte görev çubuğuna ekleme
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
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746252"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'na Uygulama Simgeleri Ekleme

Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşeni, görev çubuğunun durum bildirimi alanında tek bir simge görüntüler. Durum alanında birden çok simge göstermek için, formunuzda birden çok <xref:System.Windows.Forms.NotifyIcon> bileşeni olması gerekir. Bir denetim için görüntülenecek simgeyi ayarlamak için <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğini kullanın. Ayrıca, Kullanıcı simgeye çift tıkladığında bir şeyin olması için <xref:System.Windows.Forms.NotifyIcon.DoubleClick> olay işleyicisine kod yazabilirsiniz. Örneğin, kullanıcının simgesiyle gösterilen arka plan sürecini yapılandırması için bir iletişim kutusu görünür.

> [!NOTE]
> <xref:System.Windows.Forms.NotifyIcon> bileşeni, yalnızca bir eylem veya olayın oluştuğunu veya bazı bir sıralama durumunda değişiklik olduğunu uyarmak için bildirim amaçları için kullanılır. Uygulamalarla standart etkileşim için menüleri, araç çubuklarını ve diğer kullanıcı arabirimi öğelerini kullanmanız gerekir.

### <a name="to-set-the-icon"></a>Simgeyi ayarlamak için

1. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğine bir değer atayın. Değer `System.Drawing.Icon` türünde olmalı ve bir. ico dosyasından yüklenebilir. Koddaki simge dosyasını veya üç nokta düğmesini (...), **Özellikler** penceresindeki <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğinin yanındaki (... Özellikler penceresi) ve ardından görüntülenen **Aç** iletişim kutusunda dosyayı seçerek belirtebilirsiniz (![)](./media/visual-studio-ellipsis-button.png).

2. <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğini `true`olarak ayarlayın.

3. <xref:System.Windows.Forms.NotifyIcon.Text%2A> özelliğini uygun bir araç Ipucu dizesine ayarlayın.

     Aşağıdaki kod örneğinde, simgenin konumu için ayarlanan yol **Belgelerim klasörüdür.** Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır. Bu konumun seçilmesi, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına de olanak sağlar. Aşağıdaki örnek, zaten eklenmiş <xref:System.Windows.Forms.NotifyIcon> denetimi olan bir form gerektirir. Ayrıca, `Icon.ico`adlı bir simge dosyası da gerektirir.

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
- [Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon Bileşeni](notifyicon-component-windows-forms.md)
- [NotifyIcon Bileşenine Genel Bakış](notifyicon-component-overview-windows-forms.md)
