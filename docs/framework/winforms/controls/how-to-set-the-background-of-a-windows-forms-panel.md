---
title: 'Nasıl yapılır: Bir Windows Forms panelinin arka planını ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 9336be2aebb10e5c0bd0bf4648cae34a3b5fe7c3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300415"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Nasıl yapılır: Bir Windows Forms panelinin arka planını ayarlama
Bir Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi hem de arka plan görüntüsü görüntüleyebilirsiniz. <xref:System.Windows.Forms.Control.BackColor%2A> Özelliği etiketleri ve radyo düğmeleri gibi içerdiği denetimlerle arka plan rengini ayarlar. Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi tüm panel doldurur. Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, görüntünün içerdiği denetimlerle görüntülenir.  
  
### <a name="to-set-the-background-programmatically"></a>Arka plan program üzerinden ayarlamak için  
  
1. Bölmenin ayarlamak <xref:System.Windows.Forms.Control.BackColor%2A> türünde bir değer özelliğini <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Bölmenin ayarlamak <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğini kullanarak <xref:System.Drawing.Image.FromFile%2A> yöntemi <xref:System.Drawing.Image?displayProperty=nameWithType> sınıfı.  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel Denetimi](panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
