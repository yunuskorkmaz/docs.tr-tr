---
title: "Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma"
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
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2b0ce30f76fe7f8cbdc156c4a8ff5abffafae10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma
Windows Forms'ta baskı temelidir <xref:System.Drawing.Printing.PrintDocument> bileşen — daha belirgin olarak <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay. İşlemek için kod yazarak <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay, yazdırma gerekenler ve yazdırmak nasıl belirtebilirsiniz.  
  
### <a name="to-create-a-print-job"></a>Bir yazdırma işi oluşturmak için  
  
1.  Ekleme bir <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.  
  
2.  İşlemek için kod yazma <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.  
  
     Yazdırma mantığınızı kod gerekecektir. Ayrıca, yazdırılacak malzeme belirtmek gerekir.  
  
     Aşağıdaki kod örneğinde bir örnek grafik kırmızı bir dikdörtgen şeklinde oluşturulan <xref:System.Drawing.Printing.PrintDocument.PrintPage> yazdırılması malzeme olarak davranacak şekilde olay işleyicisi.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     İçin kod yazma isteyebilirsiniz <xref:System.Drawing.Printing.PrintDocument.BeginPrint> ve <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayları, belki de her bir sayfa yazdırır gibi düşülür yazdırmak için sayfaların toplam sayısını temsil eden bir tamsayı dahil olmak üzere.  
  
    > [!NOTE]
    >  Ekleyebileceğiniz bir <xref:System.Windows.Forms.PrintDialog> kullanıcılarınıza temiz ve etkili bir kullanıcı arabirimi (UI) sağlamak için formunuza bileşen. Ayarı <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintDialog> Yazdır ilgili özelliği ayarlamak için belge bileşen etkinleştirir, form üzerinde çalıştığınız. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.PrintDialog> bileşeni Bkz [PrintDialog bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).  
  
     Daha fazla Windows Forms hakkında bilgi için ayrıntıları yazdırma işlerini bir yazdırma işi programlı olarak oluşturmak nasıl dahil olmak üzere, bkz: <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
