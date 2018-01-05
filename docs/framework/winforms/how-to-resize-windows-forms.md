---
title: "Nasıl yapılır: Windows Formlarını Yeniden Boyutlandırma"
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
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2e9f81094d16030dbe4595a8132569edab782a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-windows-forms"></a>Nasıl yapılır: Windows Formlarını Yeniden Boyutlandırma
Windows Form boyutunu çeşitli yollarla belirtebilirsiniz. İçin yeni bir değer ayarlayarak yükseklik ve formun genişliğini program aracılığıyla değiştirebilirsiniz <xref:System.Windows.Forms.Form.Size%2A> özelliği veya ayarla <xref:System.Windows.Forms.Control.Height%2A> veya <xref:System.Windows.Forms.Control.Width%2A> özellikleri ayrı ayrı. Kullanıyorsanız [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], Windows Forms Tasarımcısı'nı kullanarak boyutunu değiştirebilirsiniz. Ayrıca bkz. [nasıl yapılır: yeniden boyutlandırma Windows formları kullanarak Tasarımcı](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).  
  
### <a name="to-resize-a-form-programmatically"></a>Bir form programlı olarak yeniden boyutlandırmak için  
  
-   Ayarlayarak çalışma zamanında bir form boyutunu tanımlamaya <xref:System.Windows.Forms.Form.Size%2A> formun özelliği.  
  
     Aşağıdaki kod örneğinde form boyutu 100 × 100 piksel ayarını gösterir.  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a>Form genişlik ve yükseklik programlı olarak değiştirmek için  
  
-   Sonra <xref:System.Windows.Forms.Form.Size%2A> olan tanımlanmış formu yükseklik veya genişliği kullanarak değiştirme <xref:System.Windows.Forms.Control.Width%2A> veya <xref:System.Windows.Forms.Control.Height%2A> özellikleri.  
  
     Yükseklik sabit kalır ancak aşağıdaki kod örneğinde form sol kenarından 300 piksel olarak ayarlanan formun genişliğini gösterir.  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     veya  
  
     Değişiklik <xref:System.Drawing.Size.Width%2A> veya <xref:System.Drawing.Size.Height%2A> ayarlayarak <xref:System.Windows.Forms.Form.Size%2A> özelliği.  
  
     Ancak, aşağıdaki kod örneğinde gösterildiği gibi bu yaklaşım yalnızca ayarlamaktan daha kullanışsız <xref:System.Windows.Forms.Control.Width%2A> veya <xref:System.Windows.Forms.Control.Height%2A> özellikleri.  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a>Form boyutunu artışlarla programlı olarak değiştirmek için  
  
-   Formun boyutunu artırmak için ayarlanmış <xref:System.Drawing.Size.Width%2A> ve <xref:System.Drawing.Size.Height%2A> özellikleri.  
  
     Aşağıdaki kod örneği, geçerli boyuttan daha geniş 200 piksel için ayarlanan formun genişliğini gösterir.  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  Her zaman kullanmak <xref:System.Drawing.Size.Height%2A> veya <xref:System.Drawing.Size.Width%2A> ayarlayarak aynı anda yükseklik ve genişlik boyutlarını ayarlıyorsanız sürece bir form boyutunu değiştirmek için özellik <xref:System.Windows.Forms.Form.Size%2A> yeni bir özellik <xref:System.Drawing.Size> yapısı. <xref:System.Windows.Forms.Form.Size%2A> Özelliği döndürür bir <xref:System.Drawing.Size> bir değer türü yapısı. Değer türü özelliği için yeni bir değer atayamazsınız. Bu nedenle, aşağıdaki kod örneğinde derlenmez.  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'a Başlarken](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Windows Forms Uygulamalarını Geliştirme](../../../docs/framework/winforms/advanced/index.md)
