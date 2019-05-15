---
title: 'Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 10e864ccfeb22113e5704a4063f903d7a91fedcd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591585"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ProgressBar> denetler; ancak, <xref:System.Windows.Forms.ProgressBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 .NET Framework içinde belirli bir değeri görüntülemek için çeşitli yollar sunar <xref:System.Windows.Forms.ProgressBar> denetimi. Seçtiğiniz hangi yaklaşımın elinizdeki veya sorun çözme bağlı olacaktır. Aşağıdaki tabloda, seçebileceğiniz yaklaşım gösterilmektedir.  
  
|Yaklaşım|Açıklama|  
|--------------|-----------------|  
|Değerini <xref:System.Windows.Forms.ProgressBar> doğrudan denetimi.|Bu yaklaşım, bir veri kaynağındaki kayıtları okuma gibi dahil olacaktır, toplam öğe ölçülen bildiğiniz görevler için kullanışlıdır. Yalnızca değeri veya iki kez ayarlamanız gerekir, ayrıca, bunu yapmanın kolay bir yolu budur. Son olarak, ilerleme çubuğu tarafından görüntülenen değeri azaltmak gerekiyorsa bu işlemi kullanın.|  
|Artırmak <xref:System.Windows.Forms.ProgressBar> sabit bir değere göre görüntüler.|Basit bir sayısı minimum ve maksimum, geçen süre veya bilinen toplam dışında işlenen dosya sayısı gibi arasında görüntülerken bu faydalı bir yaklaşımdır.|  
|Artırmak <xref:System.Windows.Forms.ProgressBar> değişen bir değer görüntüler.|Bu yaklaşım, görüntülenen değeri birkaç kez farklı tutarları değiştirmeniz gerektiğinde yararlıdır. Bir örnek, bir dizi dosyası diske yazılırken kullanılan sabit disk alanı miktarını gösteren.|  
  
 Bir ilerleme çubuğu tarafından görüntülenen değeri ayarlama en dolaysız yolu ayardır <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği. Bu tasarım zamanında veya çalışma zamanında yapılabilir.  
  
### <a name="to-set-the-progressbar-value-directly"></a>ProgressBar değeri doğrudan ayarlamak için  
  
1. Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.  
  
2. Kodda, denetimin ayarlamak <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğine yerleşik minimum ve maksimum değerleri arasında bir tamsayı değeri.  
  
    > [!NOTE]
    >  Ayarlarsanız <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği tarafından kurulan sınırların dışındaki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> denetimin özelliklerini oluşturur bir <xref:System.ArgumentException> özel durum.  
  
     Aşağıdaki kod örneğinde nasıl ayarlanacağını gösterir <xref:System.Windows.Forms.ProgressBar> doğrudan değeri. Kod, bir veri kaynağındaki kayıtları okur ve veri kaydı okuma her zaman ilerleme çubuğu ve etiket güncelleştirir. Bu örnekte, formunuzu olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetimi, bir <xref:System.Windows.Forms.ProgressBar> denetimi ve bir veri tablosu adı verilen bir satır ile `CustomerRow` ile `FirstName` ve `LastName` alanları.  
  
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
  
     Sabit bir aralıkla geçer ilerleme görüntülüyorsanız, değerini ayarlayın ve ardından artıran bir yöntem çağrısı <xref:System.Windows.Forms.ProgressBar> bu aralığa göre denetimin değeri. Bu, zamanlayıcılar ve ilerleme durumunu burada bütün bir yüzdesi olarak ölçüm değil diğer senaryolar için kullanışlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Sabit bir değere göre ilerleme çubuğu artırmak için  
  
1. Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.  
  
2. Denetimin ayarlamak <xref:System.Windows.Forms.ProgressBar.Step%2A> ilerleme çubuğunun artırmak için temsil eden tamsayı özellik değeri görüntülenir.  
  
3. Çağrı <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> kümesinde miktarı tarafından görüntülenen değeri değiştirmek için yöntem <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliği.  
  
     Aşağıdaki kod örneği, bir ilerleme çubuğu dosyaları kopyalama işlemi sayısını nasıl koruyabilirsiniz gösterir.  
  
     Her dosya belleğe okurken aşağıdaki örnekte, ilerleme çubuğu ve etiket toplam dosya okuma yansıtmak üzere güncelleştirilmiştir. Bu örnekte, formunuzu olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetimi ve bir <xref:System.Windows.Forms.ProgressBar> denetimi.  
  
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
  
     Son olarak, böylece her artış benzersiz bir miktar bir ilerleme çubuğu tarafından görüntülenen değeri artırabilirsiniz. Bu, bir dizi farklı boyutlardaki dosyaları bir sabit diske yazma veya bütün bir yüzdesi olarak ilerlemeyi ölçme gibi benzersiz işlemlerini izleyen olduğunda yararlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Dinamik bir değere göre ilerleme çubuğu artırmak için  
  
1. Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.  
  
2. Çağrı <xref:System.Windows.Forms.ProgressBar.Increment%2A> belirttiğiniz bir tamsayı tarafından görüntülenen değeri değiştirmek için yöntemi.  
  
     Aşağıdaki kod örneği, bir kopyalama işlemi sırasında ne kadar disk alanı kullanılmış bir ilerleme çubuğu nasıl hesaplayabilirsiniz gösterir.  
  
     Her dosya sabit diske yazılan aşağıdaki örnekte, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirildi. Bu örnekte, formunuzu olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetimi ve bir <xref:System.Windows.Forms.ProgressBar> denetimi.  
  
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
