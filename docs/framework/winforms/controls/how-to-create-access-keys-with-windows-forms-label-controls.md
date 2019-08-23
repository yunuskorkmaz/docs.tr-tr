---
title: 'Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma'
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
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950533"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma
Windows Forms <xref:System.Windows.Forms.Label> denetimleri, diğer denetimler için erişim anahtarlarını tanımlamak üzere kullanılabilir. Bir etiket denetiminde bir erişim anahtarı tanımladığınızda, Kullanıcı ALT tuşuna ve odağı sekme düzeninde takip eden denetime taşımak için belirlediğiniz karaktere basabilir. Etiketler odağı alamadığı için odak otomatik olarak sekme sırasında bir sonraki denetime taşınır. Metin kutularına, Birleşik giriş kutularına, liste kutularına ve veri kılavuzlarına erişim tuşları atamak için bu tekniği kullanın.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Etikete sahip bir denetime erişim anahtarı atamak için  
  
1. Önce etiketi çizin, sonra diğer denetimi çizin.  
  
     -veya-  
  
     Denetimleri herhangi bir sırada çizin ve etiketin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini diğer denetimden daha az bir olacak şekilde ayarlayın.  
  
2. Etiketin <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini olarak `true`ayarlayın.  
  
3. Etiket için erişim anahtarını atamak üzere etiketin <xref:System.Windows.Forms.Label.Text%2A> özelliğinde bir ve işareti (&) kullanın. Daha fazla bilgi için bkz. [Windows Forms denetimleri Için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > Etiketleri, erişim tuşları oluşturmak için kullanmak yerine bir etiket denetiminde göstermek isteyebilirsiniz. Bu durum, bir etiket denetimini, verilerin dahil edildiği bir kayıt kümesindeki bir alana bağlarsanız meydana gelebilir. Etiketleri etiket denetiminde göstermek için <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini olarak `false`ayarlayın. Birlikte bulunan DS 'yi ve ayrıca bir erişim anahtarınız göstermek istiyorsanız, <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini olarak `true` ayarlayın ve erişim anahtarını tek bir ve işareti (&) ile, iki ile birlikte görüntülenecek şekilde belirtin.  
  
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

- [Nasıl yapılır: Bir Windows Forms etiketi denetimini Içeriğine sığacak şekilde boyutlandır](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Etiket Denetimine Genel Bakış](label-control-overview-windows-forms.md)
- [Etiket Denetimi](label-control-windows-forms.md)
