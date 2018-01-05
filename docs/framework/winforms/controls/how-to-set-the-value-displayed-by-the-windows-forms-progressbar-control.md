---
title: "Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama"
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
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6ebca02e2084fdb7a76a9a9d711a0b0180f7a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ProgressBar> kontrol; ancak, <xref:System.Windows.Forms.ProgressBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçinde belirli bir değeri görüntülemek için birkaç farklı yöntem sunar <xref:System.Windows.Forms.ProgressBar> denetim. Seçtiğiniz hangi yaklaşımın elinizdeki veya sorun çözme bağlıdır. Aşağıdaki tabloda, seçebileceğiniz yaklaşımlar gösterir.  
  
|Yaklaşım|Açıklama|  
|--------------|-----------------|  
|Değerini <xref:System.Windows.Forms.ProgressBar> denetimini doğrudan.|Bu yaklaşım, bir veri kaynağından okuma gibi kayıtları dahil olacaktır toplamı öğesi ölçülen, burada bildiğiniz görevler için yararlıdır. Yalnızca değeri veya iki kez ayarlamak gerekiyorsa, ek olarak, bunu yapmak için kolay bir yoludur. Son olarak, ilerleme çubuğu tarafından görüntülenen değeri azaltmak gerekiyorsa bu işlemi kullanın.|  
|Artırmak <xref:System.Windows.Forms.ProgressBar> tarafından sabit bir değer görüntüler.|Bu yaklaşım basit sayısı minimum ve maksimum geçen süre veya dışında bilinen toplam işlenen dosya sayısı gibi arasında görüntülenirken yararlıdır.|  
|Artırmak <xref:System.Windows.Forms.ProgressBar> değişen değere göre görüntüler.|Görüntülenen değer bir dizi farklı tutarlar kez değiştirmeniz gerektiğinde bu yararlı bir yaklaşımdır. Örnek bir dizi dosyası diske yazılırken kullanılan sabit disk alanı miktarını gösteren.|  
  
 Bir ilerleme çubuğu tarafından görüntülenen değeri ayarlamak için en doğrudan yolu ayarlanmasıdır <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği. Bu tasarım zamanında veya çalışma zamanında yapılabilir.  
  
### <a name="to-set-the-progressbar-value-directly"></a>ProgressBar değerini doğrudan ayarlamak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.  
  
2.  Kodda, denetimin ayarlama <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğine kurulan minimum ve maksimum değerleri arasında bir tamsayı değeri.  
  
    > [!NOTE]
    >  Ayarlarsanız <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği belirlenen sınırlar dışında <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> denetimi özellikleri, yaratır bir <xref:System.ArgumentException> özel durum.  
  
     Aşağıdaki kod örneğinde nasıl ayarlanacağını gösterir <xref:System.Windows.Forms.ProgressBar> doğrudan değeri. Kod kayıtları veri kaynağından okur ve veri kaydı okuma her zaman ilerleme çubuğu ve etiket güncelleştirir. Bu örnekte, form olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetimi, bir <xref:System.Windows.Forms.ProgressBar> denetim ve veri tablosu olarak adlandırılan bir satır ile `CustomerRow` ile `FirstName` ve `LastName` alanları.  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     Sabit bir aralıkla geçer ilerleme görüntülüyorsanız, değerini ayarlayın ve sonra artırır bir yöntem çağrısı <xref:System.Windows.Forms.ProgressBar> bu aralığa göre denetimin değeri. Bu, zamanlayıcılar ve ilerleme burada bütün bir yüzdesi olarak ölçme olmayan diğer senaryolar için kullanışlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>İlerleme çubuğu tarafından sabit bir değer artırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.  
  
2.  Denetimin ayarlamak <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliğini ilerleme çubuğunun artırmak üzere temsil eden bir tamsayı değeri görüntülenir.  
  
3.  Çağrı <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> kümesinde tutar tarafından görüntülenen değeri değiştirmek için yöntemi <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliği.  
  
     Aşağıdaki kod örneği, bir ilerleme çubuğu bir kopyalama işlemi dosyalarında sayısını nasıl koruyabilirsiniz gösterilmektedir.  
  
     Her dosya belleğe, salt okunur olduğundan aşağıdaki örnekte, ilerleme çubuğu ve etiket toplam dosya okuma yansıtacak şekilde güncelleştirilmiştir. Bu örnekte, form olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetim ve <xref:System.Windows.Forms.ProgressBar> denetim.  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Son olarak, böylece her artış benzersiz bir miktar bir ilerleme çubuğu tarafından görüntülenen değeri artırabilirsiniz. Bu, bir dizi farklı boyutlarda dosyaları bir sabit diske yazma ya da bütün bir yüzdesi olarak ilerlemesini ölçme gibi benzersiz işlemlerini izleyen olduğunda yararlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>İlerleme çubuğu dinamik bir değerle artırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.  
  
2.  Çağrı <xref:System.Windows.Forms.ProgressBar.Increment%2A> belirttiğiniz bir tamsayı tarafından görüntülenen değeri değiştirmek için yöntem.  
  
     Aşağıdaki kod örneğinde, ne kadar disk alanı kopyalama işlemi sırasında kullanılan bir ilerleme çubuğu nasıl hesaplayabilirsiniz gösterilmektedir.  
  
     Her dosya sabit diske yazılır olarak aşağıdaki örnekte, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirilmiştir. Bu örnekte, form olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetim ve <xref:System.Windows.Forms.ProgressBar> denetim.  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [ProgressBar Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [ProgressBar Denetimi](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
