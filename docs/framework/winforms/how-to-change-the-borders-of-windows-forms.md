---
title: Form kenarlıklarını değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739571"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme
Windows Forms görünümünü ve davranışını belirlerken aralarından seçim yapabileceğiniz birkaç kenarlık stili vardır. <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini değiştirerek, formun yeniden boyutlandırma davranışını kontrol edebilirsiniz. Ayrıca, <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ayarlanması, başlık çubuğunun ve üzerinde hangi düğmelerin görünebileceği hakkında da etkiler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  
  
 Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms kenarlıklarını değiştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Windows Forms kenarlık stilini program aracılığıyla ayarlamak için  
  
- <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini istediğiniz stile ayarlayın. Aşağıdaki kod örneği `DlgBx1` biçim kenarlık stilini <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>olarak ayarlar.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Ayrıca bkz. [nasıl yapılır: tasarım zamanında Iletişim kutusu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Ayrıca, form için isteğe bağlı **minimize** ve **Ekranı Kapla** düğmelerini sağlayan bir kenarlık stili seçtiyseniz, bu düğmelerden birinin veya her ikisinin de işlevsel olmasını isteyip istemediğinizi belirtebilirsiniz. Bu düğmeler, Kullanıcı deneyimini yakından denetlemek istediğinizde faydalıdır. **Simge durumuna küçült** ve **Büyüt** düğmeleri varsayılan olarak etkindir ve işlevleri **Özellikler** penceresi aracılığıyla işlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
