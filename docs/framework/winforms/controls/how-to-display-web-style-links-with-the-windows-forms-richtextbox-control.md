---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme"
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
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80f794be15eae33ca4e28dc0cfe04872f63230b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, Web bağlantıları görüntüleyebilir, renkli ve altı çizili olarak. Bağlantıyı tıklattığında bağlantı metinde belirtilen Web sitesi gösteren bir tarayıcı penceresi açılır kod yazabilirsiniz.  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>RichTextBox denetimi ile bir Web sayfasına bağlamak için  
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği için geçerli bir URL (örneğin, "http://www.microsoft.com/") içeren bir dize.  
  
2.  Emin olun <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> özelliği ayarlanmış `true` (varsayılan).  
  
3.  Yeni genel bir örneğini oluşturmak <xref:System.Diagnostics.Process> nesnesi.  
  
4.  Bir olay işleyicisi yazma <xref:System.Windows.Forms.RichTextBox.LinkClicked> istenen metni tarayıcı gönderen olay.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.RichTextBox.LinkClicked> olayı açar belirtilen URL'ye Internet Explorer'ın bir örneği <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetim. Bu örnek bir formla varsayar bir <xref:System.Windows.Forms.RichTextBox> denetim.  
  
    > [!IMPORTANT]
    >  Arama içinde <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> yöntemi, karşılaşırsınız bir <xref:System.Security.SecurityException> nedeniyle yeterli ayrıcalığa sahip bir kısmi güven bağlamında kodu çalıştırıyorsanız, özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) İşlem başlatmalıdır `p`, formunuz oluşturucuda aşağıdaki ifadeyi ekleyerek yapabilirsiniz:  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     Hemen çalışmaya tamamladıktan sonra oluşturduğunuz işlemi durdurmak önemlidir. Yukarıdaki sunulan kodu aşağıdakilerle ilgili işlemi durdurmak için kodunuzu şuna benzeyebilir:  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>  
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
