---
title: "Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma"
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a856090a76f484c21c1d9982d67e9fdf21e8451
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma
Windows Forms <xref:System.Windows.Forms.Label> denetimleri, diğer denetimler için erişim anahtarları tanımlamak için kullanılabilir. Bir etiket denetiminde bir erişim anahtarı tanımladığınızda, kullanıcı ALT tuşuyla birlikte odağını sekme sırasında izleyen denetime taşıma için belirttiğiniz karakter tuşlarına basabilirsiniz. Etiketleri odak alamaz olduğundan odağını sekme sırasında bir sonraki denetime otomatik olarak taşır. Metin kutuları, birleşik giriş kutuları, liste kutuları ile veri kılavuzları erişim tuşları atamak için bu tekniği kullanabilirsiniz.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Bir etiket bir denetim için erişim tuşu atamak için  
  
1.  Etiketin ilk çizim ve diğer denetim çizin.  
  
     veya  
  
     Herhangi bir sırada denetimleri çizme ve ayarlayın <xref:System.Windows.Forms.Control.TabIndex%2A> bir diğer denetim değerinden etiketinin özelliği.  
  
2.  Etiketin ayarlamak <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `true`.  
  
3.  Ve işareti kullanın (&) etiketin <xref:System.Windows.Forms.Label.Text%2A> etiketi için erişim anahtarı atamak için özellik. Daha fazla bilgi için bkz: [oluşturma erişim anahtarları için Windows Forms denetimleri](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Yerine bir etiket denetimi ve işaretlerini görüntüleme erişim tuşları oluşturma için onları kullanmak isteyebilirsiniz. Etiket denetimi nerede ve işaretlerini verileri içeren bir kayıt kümesindeki alan bağlarsanız bu durum oluşabilir. Etiket denetimi ve işaretlerini görüntülemek için ayarlanmış <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `false`. Ve işaretlerini görüntüleme ve ayrıca bir erişim anahtarı isterseniz, <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `true` ve bir ampersan erişim anahtarıyla belirtin (&) ve ve işareti ile iki ve işaretlerini görüntüleme.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [Etiket Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Etiket Denetimi](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
