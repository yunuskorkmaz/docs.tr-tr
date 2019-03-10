---
title: 'Nasıl yapılır: Windows formlarının kenarlıklarını değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: f188e14b304970840bfc35a592a445f68f9d7af7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713915"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Nasıl yapılır: Windows formlarının kenarlıklarını değiştirme
Görünümünü ve davranışını Windows formlarınızın belirlerken, aralarından seçim yapabileceğiniz çeşitli kenarlık stillerini var. Değiştirerek <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliği, formu yeniden boyutlandırma davranışını kontrol edebilirsiniz. Ayrıca, ayarı <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ne düğme üzerinde görünebilir yanı sıra başlık çubuğunun nasıl görüntüleneceğini etkiler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  
  
 Ayrıca bkz: [nasıl yapılır: Tasarımcı kullanarak Windows formlarının kenarlıklarını değiştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Windows Forms kenarlık stilini program üzerinden ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini istediğiniz stili. Aşağıdaki kod örneği form kenarlık stilini ayarlar `DlgBx1` için <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
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
  
     Ayrıca bkz: [nasıl yapılır: Tasarım zamanında iletişim kutuları oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Ayrıca, isteğe bağlı sağlayan form için bir kenarlık stili seçtiniz, **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, ya da işlevsel olması için bu düğmeleri isteyip istemediğinizi belirtebilirsiniz. Bu düğmeler, kullanıcı deneyimini yakından denetlemek istediğinizde yararlıdır. **Simge durumuna küçült** ve **Ekranı Kapla** düğmeler, varsayılan olarak etkinleştirilir ve işlevleri aracılığıyla yönetilebilir **özellikleri** penceresi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
