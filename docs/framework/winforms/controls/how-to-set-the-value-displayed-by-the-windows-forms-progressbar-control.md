---
title: ProgressBar Denetimi tarafından Görüntülenen Değeri Ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d295079a96ca19a4e4c98e113a3f3051c6403182
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141817"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama
> [!IMPORTANT]
> Denetim, <xref:System.Windows.Forms.ToolStripProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.ProgressBar> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.  
  
 .NET Framework, denetim içinde belirli bir değeri <xref:System.Windows.Forms.ProgressBar> görüntülemeniz için birkaç farklı yol sunar. Hangi yaklaşımı seçeceğiniz, elinizdeki göreve veya çözeceğiniz soruna bağlıdır. Aşağıdaki tabloda seçebileceğiniz yaklaşımlar gösterilmektedir.  
  
|Yaklaşım|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.ProgressBar> Denetimin değerini doğrudan ayarlayın.|Bu yaklaşım, bir veri kaynağından kayıtları n okuma gibi, ilgili olacak ölçülen öğenin toplamını bildiğiniz görevler için yararlıdır. Ayrıca, değeri yalnızca bir veya iki kez ayarlamanız gerekiyorsa, bunu yapmanın kolay bir yoludur. Son olarak, ilerleme çubuğu tarafından görüntülenen değeri azaltmanız gerekiyorsa bu işlemi kullanın.|  
|Ekranı <xref:System.Windows.Forms.ProgressBar> sabit bir değerle artırın.|Bu yaklaşım, geçen süre veya bilinen toplamdan işlenen dosya sayısı gibi minimum ve en büyük arasında basit bir sayı görüntülerken yararlıdır.|  
|Ekranı <xref:System.Windows.Forms.ProgressBar> değişen bir değere göre artırın.|Bu yaklaşım, görüntülenen değeri farklı miktarlarda birkaç kez değiştirmeniz gerektiğinde yararlıdır. Bir örnek, diske bir dizi dosya yazarken tüketilen sabit disk alanı miktarını göstermek olacaktır.|  
  
 İlerleme çubuğu tarafından görüntülenen değeri ayarlamanın en doğrudan <xref:System.Windows.Forms.ProgressBar.Value%2A> yolu özelliği ayarlamaktır. Bu, tasarım zamanında veya çalışma zamanında yapılabilir.  
  
### <a name="to-set-the-progressbar-value-directly"></a>ProgressBar değerini doğrudan ayarlamak için  
  
1. Denetimin <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerin ayarla.  
  
2. Kodda, denetimin <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini oluşturduğunuz minimum ve en büyük değerler arasında bir sonda değerine ayarlayın.  
  
    > [!NOTE]
    > Özelliği, özellik <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> mülkler tarafından belirlenen sınırların dışına ayarlarsanız, <xref:System.ArgumentException> denetim bir özel durum oluşturur. <xref:System.Windows.Forms.ProgressBar.Value%2A>  
  
     Aşağıdaki kod örneği, değerin <xref:System.Windows.Forms.ProgressBar> doğrudan nasıl ayarlanır olduğunu göstermektedir. Kod, bir veri kaynağından kayıtları okur ve bir veri kaydı her okundunda ilerleme çubuğunu ve etiketi güncelleştirir. Bu örnek, formunuzun <xref:System.Windows.Forms.Label> bir <xref:System.Windows.Forms.ProgressBar> denetimi, denetimi ve bir satır `CustomerRow` `FirstName` la `LastName` ve alanları olan bir veri tablosuna sahip olduğunu gerektirir.  
  
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
  
     Sabit bir aralıkla ilerleyen ilerlemeyi görüntülerseniz, değeri ayarlayabilir ve ardından denetimin <xref:System.Windows.Forms.ProgressBar> değerini bu aralıkla artıran bir yöntem çağırabilirsiniz. Bu, ilerlemeyi bütünün yüzdesi olarak ölçmediğiniz zamanlayıcılar ve diğer senaryolar için yararlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>İlerleme çubuğunu sabit bir değerle artırmak için  
  
1. Denetimin <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerin ayarla.  
  
2. İlerleme çubuğunun <xref:System.Windows.Forms.ProgressBar.Step%2A> görüntülenen değerini artırmak için denetimin özelliğini miktarı temsil eden bir karşılamaya ayarlayın.  
  
3. <xref:System.Windows.Forms.ProgressBar.Step%2A> Özellikte <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> ayarlanan tutara göre görüntülenen değeri değiştirmek için yöntemi arayın.  
  
     Aşağıdaki kod örneği, bir ilerleme çubuğunun bir kopyalama işleminde dosyaların sayısını nasıl koruyabileceğini göstermektedir.  
  
     Aşağıdaki örnekte, her dosya belleğe okundukça, ilerleme çubuğu ve etiket, okunan toplam dosyaları yansıtacak şekilde güncelleştirilir. Bu örnek, formunuzun <xref:System.Windows.Forms.Label> bir <xref:System.Windows.Forms.ProgressBar> denetimi ve denetimi olduğunu gerektirir.  
  
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
  
     Son olarak, her artış benzersiz bir tutar olacak şekilde bir ilerleme çubuğu tarafından görüntülenen değeri artırabilirsiniz. Bu, sabit diske farklı boyutlarda dosyalar yazmak veya ilerlemeyi bütünün yüzdesi olarak ölçmek gibi bir dizi benzersiz işlemi takip ederken kullanışlıdır.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>İlerleme çubuğunu dinamik bir değerle artırmak için  
  
1. Denetimin <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerin ayarla.  
  
2. Belirttiğiniz <xref:System.Windows.Forms.ProgressBar.Increment%2A> bir arastağı tarafından görüntülenen değeri değiştirmek için yöntemi arayın.  
  
     Aşağıdaki kod örneği, bir ilerleme çubuğunun kopyalama işlemi sırasında ne kadar disk alanı kullanıldığını nasıl hesaplayabildiğini göstermektedir.  
  
     Aşağıdaki örnekte, her dosya sabit diske yazıldığından, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirilir. Bu örnek, formunuzun <xref:System.Windows.Forms.Label> bir <xref:System.Windows.Forms.ProgressBar> denetimi ve denetimi olduğunu gerektirir.  
  
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
