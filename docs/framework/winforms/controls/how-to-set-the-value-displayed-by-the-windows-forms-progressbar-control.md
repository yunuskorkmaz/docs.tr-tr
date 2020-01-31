---
title: ProgressBar denetimi tarafından görünen değeri ayarla
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 79ce1e576652d00b323d31dfc6551e168ea0a9a0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743807"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> denetimi yerini alır ve <xref:System.Windows.Forms.ProgressBar> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.ProgressBar> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.  
  
 .NET Framework, <xref:System.Windows.Forms.ProgressBar> denetimindeki belirli bir değeri görüntülemenin birkaç farklı yolunu sağlar. Hangi yaklaşımda seçeceğiniz, yaptığınız göreve veya çözmenize yönelik soruna bağlı olarak değişir. Aşağıdaki tabloda, seçebileceğiniz yaklaşımlar gösterilmektedir.  
  
|Yaklaşım|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.ProgressBar> denetiminin değerini doğrudan ayarlayın.|Bu yaklaşım, bir veri kaynağından kayıtları okumak gibi Ölçülecek öğenin toplam miktarını bildiğiniz görevler için yararlıdır. Ayrıca, yalnızca değeri bir veya iki kez ayarlamanız gerekiyorsa bu, bunu yapmanın kolay bir yoludur. Son olarak, ilerleme çubuğu tarafından görüntülenecek değeri azaltmayı gerekiyorsa bu işlemi kullanın.|  
|<xref:System.Windows.Forms.ProgressBar> görüntüsünü sabit bir değere göre artırın.|Bu yaklaşım, geçen süre veya bilinen toplam dışında işlenen dosya sayısı gibi minimum ve maksimum arasında basit bir sayı görüntülerken faydalıdır.|  
|Değişen bir değere göre <xref:System.Windows.Forms.ProgressBar> görüntülenmesini artırın.|Bu yaklaşım, görüntülenecek değeri farklı tutarlarda birkaç kez değiştirmeniz gerektiğinde faydalıdır. Diske bir dosya dizisi yazarken tüketilen sabit disk alanı miktarını gösteren bir örnek bir örnektir.|  
  
 İlerleme çubuğu tarafından görüntülenecek değeri ayarlamanın en doğrudan yolu <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini ayarlamadır. Bu, tasarım zamanında ya da çalışma zamanında yapılabilir.  
  
### <a name="to-set-the-progressbar-value-directly"></a>ProgressBar değerini doğrudan ayarlamak için  
  
1. <xref:System.Windows.Forms.ProgressBar> denetiminin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerini ayarlayın.  
  
2. Kod içinde, denetimin <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini, en düşük ve en yüksek değerler arasında bir tamsayı değeri olarak ayarlayın.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> Özellikler tarafından belirlenen sınırların dışında ayarlarsanız, denetim bir <xref:System.ArgumentException> özel durumu oluşturur.  
  
     Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.ProgressBar> değerinin doğrudan nasıl ayarlanacağı gösterilmektedir. Kod, bir veri kaynağından kayıtları okur ve bir veri kaydı her okunışında ilerleme çubuğunu ve etiketi güncelleştirir. Bu örnek, formunuzun bir <xref:System.Windows.Forms.Label> denetimine, bir <xref:System.Windows.Forms.ProgressBar> denetimine ve `FirstName` ve `LastName` alanlarıyla `CustomerRow` adlı bir satırı olan bir veri tablosuna sahip olmasını gerektirir.  
  
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
  
     Sabit bir aralıkla devam eden ilerlemeyi görüntülüyorsanız, değeri ayarlayabilir ve ardından bu aralığa göre <xref:System.Windows.Forms.ProgressBar> denetiminin değerini artıran bir yöntemi çağırabilirsiniz. Bu, tüm kullanım yüzdesi olarak ilerlemeyi ölçmeye devam ettiğiniz zamanlayıcılar ve diğer senaryolar için kullanışlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>İlerleme çubuğunu sabit bir değere göre artırma  
  
1. <xref:System.Windows.Forms.ProgressBar> denetiminin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerini ayarlayın.  
  
2. Denetimin <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliğini, ilerleme çubuğunun gösterildiği değeri artırmak için miktarı temsil eden bir tamsayı olarak ayarlayın.  
  
3. <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliğinde ayarlanan miktar tarafından görüntülenecek değeri değiştirmek için <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> yöntemini çağırın.  
  
     Aşağıdaki kod örneğinde, bir ilerleme çubuğunun bir kopyalama işleminde dosya sayısını nasıl koruyabileceği gösterilmektedir.  
  
     Aşağıdaki örnekte, her bir dosya belleğe okunduğu için, ilerleme çubuğu ve etiket okunan toplam dosyaları yansıtacak şekilde güncelleştirilir. Bu örnek, formunuzun <xref:System.Windows.Forms.Label> denetimine ve <xref:System.Windows.Forms.ProgressBar> denetimine sahip olmasını gerektirir.  
  
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
  
     Son olarak, her artışın benzersiz bir miktar olması için ilerleme çubuğu ile görüntülenen değeri artırabilirsiniz. Bu, farklı boyutlardaki dosyaları bir sabit diske yazma veya bir bütün kullanım yüzdesi olarak ilerlemeyi ölçme gibi bir dizi benzersiz işlemi izlerken yararlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>İlerleme çubuğunu dinamik bir değere göre artırmak için  
  
1. <xref:System.Windows.Forms.ProgressBar> denetiminin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerini ayarlayın.  
  
2. Belirttiğiniz bir tamsayı ile görüntülenecek değeri değiştirmek için <xref:System.Windows.Forms.ProgressBar.Increment%2A> yöntemini çağırın.  
  
     Aşağıdaki kod örneği, bir kopyalama işlemi sırasında bir ilerleme çubuğunun ne kadar disk alanı kullandığını nasıl hesaplayabileceğini göstermektedir.  
  
     Aşağıdaki örnekte, her bir dosya sabit diske yazıldığı için, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirilir. Bu örnek, formunuzun <xref:System.Windows.Forms.Label> denetimine ve <xref:System.Windows.Forms.ProgressBar> denetimine sahip olmasını gerektirir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar Denetimine Genel Bakış](progressbar-control-overview-windows-forms.md)
- [ProgressBar Denetimi](progressbar-control-windows-forms.md)
