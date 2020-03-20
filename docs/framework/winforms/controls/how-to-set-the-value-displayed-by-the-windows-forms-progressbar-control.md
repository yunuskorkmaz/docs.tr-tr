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
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="56353-102">Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="56353-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="56353-103">Denetim, <xref:System.Windows.Forms.ToolStripProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.ProgressBar> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="56353-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="56353-104">.NET Framework, denetim içinde belirli bir değeri <xref:System.Windows.Forms.ProgressBar> görüntülemeniz için birkaç farklı yol sunar.</span><span class="sxs-lookup"><span data-stu-id="56353-104">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="56353-105">Hangi yaklaşımı seçeceğiniz, elinizdeki göreve veya çözeceğiniz soruna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="56353-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="56353-106">Aşağıdaki tabloda seçebileceğiniz yaklaşımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56353-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="56353-107">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="56353-107">Approach</span></span>|<span data-ttu-id="56353-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56353-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="56353-109"><xref:System.Windows.Forms.ProgressBar> Denetimin değerini doğrudan ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56353-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="56353-110">Bu yaklaşım, bir veri kaynağından kayıtları n okuma gibi, ilgili olacak ölçülen öğenin toplamını bildiğiniz görevler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="56353-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="56353-111">Ayrıca, değeri yalnızca bir veya iki kez ayarlamanız gerekiyorsa, bunu yapmanın kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="56353-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="56353-112">Son olarak, ilerleme çubuğu tarafından görüntülenen değeri azaltmanız gerekiyorsa bu işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="56353-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="56353-113">Ekranı <xref:System.Windows.Forms.ProgressBar> sabit bir değerle artırın.</span><span class="sxs-lookup"><span data-stu-id="56353-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="56353-114">Bu yaklaşım, geçen süre veya bilinen toplamdan işlenen dosya sayısı gibi minimum ve en büyük arasında basit bir sayı görüntülerken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="56353-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="56353-115">Ekranı <xref:System.Windows.Forms.ProgressBar> değişen bir değere göre artırın.</span><span class="sxs-lookup"><span data-stu-id="56353-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="56353-116">Bu yaklaşım, görüntülenen değeri farklı miktarlarda birkaç kez değiştirmeniz gerektiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="56353-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="56353-117">Bir örnek, diske bir dizi dosya yazarken tüketilen sabit disk alanı miktarını göstermek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="56353-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="56353-118">İlerleme çubuğu tarafından görüntülenen değeri ayarlamanın en doğrudan <xref:System.Windows.Forms.ProgressBar.Value%2A> yolu özelliği ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="56353-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="56353-119">Bu, tasarım zamanında veya çalışma zamanında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="56353-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="56353-120">ProgressBar değerini doğrudan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="56353-120">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="56353-121">Denetimin <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerin ayarla.</span><span class="sxs-lookup"><span data-stu-id="56353-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="56353-122">Kodda, denetimin <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini oluşturduğunuz minimum ve en büyük değerler arasında bir sonda değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56353-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="56353-123">Özelliği, özellik <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> mülkler tarafından belirlenen sınırların dışına ayarlarsanız, <xref:System.ArgumentException> denetim bir özel durum oluşturur. <xref:System.Windows.Forms.ProgressBar.Value%2A></span><span class="sxs-lookup"><span data-stu-id="56353-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="56353-124">Aşağıdaki kod örneği, değerin <xref:System.Windows.Forms.ProgressBar> doğrudan nasıl ayarlanır olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="56353-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="56353-125">Kod, bir veri kaynağından kayıtları okur ve bir veri kaydı her okundunda ilerleme çubuğunu ve etiketi güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="56353-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="56353-126">Bu örnek, formunuzun <xref:System.Windows.Forms.Label> bir <xref:System.Windows.Forms.ProgressBar> denetimi, denetimi ve bir satır `CustomerRow` `FirstName` la `LastName` ve alanları olan bir veri tablosuna sahip olduğunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="56353-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Sabit bir aralıkla ilerleyen ilerlemeyi görüntülerseniz, değeri ayarlayabilir ve ardından denetimin <xref:System.Windows.Forms.ProgressBar> değerini bu aralıkla artıran bir yöntem çağırabilirsiniz. <span data-ttu-id="56353-128">Bu, ilerlemeyi bütünün yüzdesi olarak ölçmediğiniz zamanlayıcılar ve diğer senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="56353-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="56353-129">İlerleme çubuğunu sabit bir değerle artırmak için</span><span class="sxs-lookup"><span data-stu-id="56353-129">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="56353-130">Denetimin <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerin ayarla.</span><span class="sxs-lookup"><span data-stu-id="56353-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="56353-131">İlerleme çubuğunun <xref:System.Windows.Forms.ProgressBar.Step%2A> görüntülenen değerini artırmak için denetimin özelliğini miktarı temsil eden bir karşılamaya ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56353-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="56353-132"><xref:System.Windows.Forms.ProgressBar.Step%2A> Özellikte <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> ayarlanan tutara göre görüntülenen değeri değiştirmek için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="56353-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="56353-133">Aşağıdaki kod örneği, bir ilerleme çubuğunun bir kopyalama işleminde dosyaların sayısını nasıl koruyabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="56353-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="56353-134">Aşağıdaki örnekte, her dosya belleğe okundukça, ilerleme çubuğu ve etiket, okunan toplam dosyaları yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="56353-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="56353-135">Bu örnek, formunuzun <xref:System.Windows.Forms.Label> bir <xref:System.Windows.Forms.ProgressBar> denetimi ve denetimi olduğunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="56353-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Son olarak, her artış benzersiz bir tutar olacak şekilde bir ilerleme çubuğu tarafından görüntülenen değeri artırabilirsiniz. <span data-ttu-id="56353-137">Bu, sabit diske farklı boyutlarda dosyalar yazmak veya ilerlemeyi bütünün yüzdesi olarak ölçmek gibi bir dizi benzersiz işlemi takip ederken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="56353-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="56353-138">İlerleme çubuğunu dinamik bir değerle artırmak için</span><span class="sxs-lookup"><span data-stu-id="56353-138">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="56353-139">Denetimin <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerlerin ayarla.</span><span class="sxs-lookup"><span data-stu-id="56353-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="56353-140">Belirttiğiniz <xref:System.Windows.Forms.ProgressBar.Increment%2A> bir arastağı tarafından görüntülenen değeri değiştirmek için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="56353-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="56353-141">Aşağıdaki kod örneği, bir ilerleme çubuğunun kopyalama işlemi sırasında ne kadar disk alanı kullanıldığını nasıl hesaplayabildiğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="56353-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="56353-142">Aşağıdaki örnekte, her dosya sabit diske yazıldığından, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="56353-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="56353-143">Bu örnek, formunuzun <xref:System.Windows.Forms.Label> bir <xref:System.Windows.Forms.ProgressBar> denetimi ve denetimi olduğunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="56353-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56353-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56353-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="56353-145">ProgressBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="56353-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="56353-146">ProgressBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="56353-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
