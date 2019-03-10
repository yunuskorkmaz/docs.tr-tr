---
title: 'Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: 227880ad15e452df3f05807c41f3923cccb6fe3a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708307"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma
Windows Forms <xref:System.Windows.Forms.Label> denetimleri, diğer denetimler için erişim anahtarları tanımlamak için kullanılabilir. Kullanıcı, bir etiket denetiminde bir erişim anahtarı tanımladığınızda, ALT tuşuyla sekme sırasının takip eden denetim odağı taşımak için belirlediğiniz karakter basabilirsiniz. Etiketleri odağı alamıyor olduğundan, odak sonraki sekme sırasını denetimde otomatik olarak taşır. Metin kutuları, birleşik giriş kutuları, liste kutuları ve veri kılavuzları için erişim anahtarlarını atamak için bu tekniği kullanın.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Bir denetimi bir etikete sahip bir erişim anahtarı atamak için  
  
1.  Etiket çizebilir ve diğer denetimi çizin.  
  
     -veya-  
  
     Herhangi bir sırada denetimlerini çizmek ve ayarlama <xref:System.Windows.Forms.Control.TabIndex%2A> diğer denetim küçük etiketin özelliği.  
  
2.  Etiketin <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true`.  
  
3.  Ve işareti kullanın (&) etiketin <xref:System.Windows.Forms.Label.Text%2A> etiket için erişim tuşu atama özelliği. Daha fazla bilgi için [oluşturma erişim anahtarları için Windows Forms denetimleri](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Yerine bir etiket denetiminde kodlarına görüntülemek erişim anahtarları oluşturmak için bunları kullanmayı isteyebilirsiniz. Burada kodlarına verileri içeren bir kayıt alana bir etiket denetimi bağlarsanız bu durum oluşabilir. Kodlarına bir etiket denetiminde görüntülenecek kümesi <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `false`. İşaretlerini görüntüleme ve ayrıca bir erişim anahtarı isterseniz <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true` ve bir ampersan ile erişim anahtarını belirtin (&) ve ve işareti ile iki kodlarına görüntülenecek.  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bir Windows Forms etiket denetimini içeriğini sığdıracak şekilde boyutlandırma](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Etiket Denetimine Genel Bakış](label-control-overview-windows-forms.md)
- [Etiket Denetimi](label-control-windows-forms.md)
