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
ms.openlocfilehash: 2e0134206ba3ebdce35f5374cbad575e34483d58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956092"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="1e4e1-102">Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1e4e1-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="1e4e1-103">Denetim yerini alır ve <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStripProgressBar></span><span class="sxs-lookup"><span data-stu-id="1e4e1-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="1e4e1-104">.NET Framework, <xref:System.Windows.Forms.ProgressBar> denetim içinde verilen bir değeri görüntülemenin birkaç farklı yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-104">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="1e4e1-105">Hangi yaklaşımda seçeceğiniz, yaptığınız göreve veya çözmenize yönelik soruna bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="1e4e1-106">Aşağıdaki tabloda, seçebileceğiniz yaklaşımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="1e4e1-107">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="1e4e1-107">Approach</span></span>|<span data-ttu-id="1e4e1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e4e1-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1e4e1-109"><xref:System.Windows.Forms.ProgressBar> Denetimin değerini doğrudan ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="1e4e1-110">Bu yaklaşım, bir veri kaynağından kayıtları okumak gibi Ölçülecek öğenin toplam miktarını bildiğiniz görevler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="1e4e1-111">Ayrıca, yalnızca değeri bir veya iki kez ayarlamanız gerekiyorsa bu, bunu yapmanın kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="1e4e1-112">Son olarak, ilerleme çubuğu tarafından görüntülenecek değeri azaltmayı gerekiyorsa bu işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="1e4e1-113"><xref:System.Windows.Forms.ProgressBar> Görüntüyü sabit bir değere göre artırın.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="1e4e1-114">Bu yaklaşım, geçen süre veya bilinen toplam dışında işlenen dosya sayısı gibi minimum ve maksimum arasında basit bir sayı görüntülerken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="1e4e1-115"><xref:System.Windows.Forms.ProgressBar> Görüntüyü değişen bir değere göre artırın.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="1e4e1-116">Bu yaklaşım, görüntülenecek değeri farklı tutarlarda birkaç kez değiştirmeniz gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="1e4e1-117">Diske bir dosya dizisi yazarken tüketilen sabit disk alanı miktarını gösteren bir örnek bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="1e4e1-118">İlerleme çubuğu tarafından görüntülenecek değeri ayarlamanın en doğrudan yolu, <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği ayarlamadır.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="1e4e1-119">Bu, tasarım zamanında ya da çalışma zamanında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="1e4e1-120">ProgressBar değerini doğrudan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1e4e1-120">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="1e4e1-121"><xref:System.Windows.Forms.ProgressBar> Denetimin<xref:System.Windows.Forms.ProgressBar.Maximum%2A> ve değerlerini ayarlayın. <xref:System.Windows.Forms.ProgressBar.Minimum%2A></span><span class="sxs-lookup"><span data-stu-id="1e4e1-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="1e4e1-122">Kod içinde, denetimin <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini, oluşturduğunuz en düşük ve en yüksek değerler arasında bir tamsayı değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1e4e1-123"><xref:System.Windows.Forms.ProgressBar.Value%2A> Özelliğini <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.ArgumentException> ve özellikleritarafındanbelirlenensınırlarındışındaayarlarsanız,denetimbirözeldurumoluşturur.<xref:System.Windows.Forms.ProgressBar.Maximum%2A></span><span class="sxs-lookup"><span data-stu-id="1e4e1-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="1e4e1-124">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.ProgressBar> değerin doğrudan nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="1e4e1-125">Kod, bir veri kaynağından kayıtları okur ve bir veri kaydı her okunışında ilerleme çubuğunu ve etiketi güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="1e4e1-126"><xref:System.Windows.Forms.Label> Bu örnekte `CustomerRow` `FirstName` `LastName` , formunuzun bir denetim, Denetimvevealanlarıileadlıbirsatırıolanbirveritablosuolmasıgerekir.<xref:System.Windows.Forms.ProgressBar></span><span class="sxs-lookup"><span data-stu-id="1e4e1-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Sabit bir aralıkla devam eden ilerlemeyi görüntülüyorsanız, değeri ayarlayabilir ve sonra <xref:System.Windows.Forms.ProgressBar> denetimin değerini o aralığa göre artıran bir yöntemi çağırabilirsiniz. <span data-ttu-id="1e4e1-128">Bu, tüm kullanım yüzdesi olarak ilerlemeyi ölçmeye devam ettiğiniz zamanlayıcılar ve diğer senaryolar için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="1e4e1-129">İlerleme çubuğunu sabit bir değere göre artırma</span><span class="sxs-lookup"><span data-stu-id="1e4e1-129">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="1e4e1-130"><xref:System.Windows.Forms.ProgressBar> Denetimin<xref:System.Windows.Forms.ProgressBar.Maximum%2A> ve değerlerini ayarlayın. <xref:System.Windows.Forms.ProgressBar.Minimum%2A></span><span class="sxs-lookup"><span data-stu-id="1e4e1-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="1e4e1-131">Denetim <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliğini, ilerleme çubuğunun Görüntülenme değerini artırmak için miktarı temsil eden bir tamsayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="1e4e1-132"><xref:System.Windows.Forms.ProgressBar.Step%2A> Özelliğindeki miktar kümesi tarafından görüntülenecek değeri değiştirmek için yönteminiçağırın.<xref:System.Windows.Forms.ProgressBar.PerformStep%2A></span><span class="sxs-lookup"><span data-stu-id="1e4e1-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="1e4e1-133">Aşağıdaki kod örneğinde, bir ilerleme çubuğunun bir kopyalama işleminde dosya sayısını nasıl koruyabileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="1e4e1-134">Aşağıdaki örnekte, her bir dosya belleğe okunduğu için, ilerleme çubuğu ve etiket okunan toplam dosyaları yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="1e4e1-135">Bu örnek, <xref:System.Windows.Forms.Label> formunuzun denetim <xref:System.Windows.Forms.ProgressBar> ve denetim olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Son olarak, her artışın benzersiz bir miktar olması için ilerleme çubuğu ile görüntülenen değeri artırabilirsiniz. <span data-ttu-id="1e4e1-137">Bu, farklı boyutlardaki dosyaları bir sabit diske yazma veya bir bütün kullanım yüzdesi olarak ilerlemeyi ölçme gibi bir dizi benzersiz işlemi izlerken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="1e4e1-138">İlerleme çubuğunu dinamik bir değere göre artırmak için</span><span class="sxs-lookup"><span data-stu-id="1e4e1-138">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="1e4e1-139"><xref:System.Windows.Forms.ProgressBar> Denetimin<xref:System.Windows.Forms.ProgressBar.Maximum%2A> ve değerlerini ayarlayın. <xref:System.Windows.Forms.ProgressBar.Minimum%2A></span><span class="sxs-lookup"><span data-stu-id="1e4e1-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="1e4e1-140">Belirttiğiniz bir tamsayı ile görüntülenecek değeri değiştirmek için yönteminiçağırın.<xref:System.Windows.Forms.ProgressBar.Increment%2A></span><span class="sxs-lookup"><span data-stu-id="1e4e1-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="1e4e1-141">Aşağıdaki kod örneği, bir kopyalama işlemi sırasında bir ilerleme çubuğunun ne kadar disk alanı kullandığını nasıl hesaplayabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="1e4e1-142">Aşağıdaki örnekte, her bir dosya sabit diske yazıldığı için, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="1e4e1-143">Bu örnek, <xref:System.Windows.Forms.Label> formunuzun denetim <xref:System.Windows.Forms.ProgressBar> ve denetim olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e4e1-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e4e1-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="1e4e1-145">ProgressBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1e4e1-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="1e4e1-146">ProgressBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="1e4e1-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
