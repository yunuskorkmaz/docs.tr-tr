---
title: 'Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 76bae6ba3b2a36e9dfa527528fe1e4322a87426c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539782"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme
Windows Forms davranışı ve görünümü belirlerken aralarından seçim yapabileceğiniz çeşitli kenarlık stilleri var. Değiştirerek <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliği, formu yeniden boyutlandırma davranışını kontrol edebilirsiniz. Ayrıca, ayarı <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ne düğmeleri üzerinde görünebilir yanı sıra başlık çubuğunu nasıl görüntüleneceğini etkiler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Visual Studio'da bu görev için kapsamlı destek yoktur.  
  
 Ayrıca bkz. [nasıl yapılır: Tasarımcı kullanarak Windows formlarının kenarlıklarını değiştirme](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Windows Forms kenarlık stilini programlı olarak ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.Form.FormBorderStyle%2A> istediğiniz stil özelliğine. Aşağıdaki kod örneğinde form kenarlık stilini ayarlar `DlgBx1` için <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
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
  
     Ayrıca bkz. [nasıl yapılır: tasarım zamanında iletişim kutuları oluşturma](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).  
  
     Ayrıca, isteğe bağlı sağlayan form için kenarlık stili seçmiş olduğunuz varsa **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, ya da işlevsel olması için bu düğmelerin her ikisi de isteyip istemediğinizi belirtebilirsiniz. Bu düğme, yakından kullanıcı deneyimini kontrol etmek istediğinizde faydalıdır. **Simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, varsayılan olarak etkinleştirilir ve bunların işlevi aracılığıyla yönetilebilir **özellikleri** penceresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [Windows Forms'a Başlarken](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
