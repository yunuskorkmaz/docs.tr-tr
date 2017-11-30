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
ms.openlocfilehash: d3fd66e10515e5135545f6fcfa64546141346519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="ea319-102">Nasıl yapılır: Windows Forms ProgressBar Denetimi Tarafından Görüntülenen Değeri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ea319-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="ea319-103"><xref:System.Windows.Forms.ToolStripProgressBar> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ProgressBar> kontrol; ancak, <xref:System.Windows.Forms.ProgressBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="ea319-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ea319-104">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçinde belirli bir değeri görüntülemek için birkaç farklı yöntem sunar <xref:System.Windows.Forms.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="ea319-104">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="ea319-105">Seçtiğiniz hangi yaklaşımın elinizdeki veya sorun çözme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea319-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="ea319-106">Aşağıdaki tabloda, seçebileceğiniz yaklaşımlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea319-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="ea319-107">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="ea319-107">Approach</span></span>|<span data-ttu-id="ea319-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea319-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ea319-109">Değerini <xref:System.Windows.Forms.ProgressBar> denetimini doğrudan.</span><span class="sxs-lookup"><span data-stu-id="ea319-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="ea319-110">Bu yaklaşım, bir veri kaynağından okuma gibi kayıtları dahil olacaktır toplamı öğesi ölçülen, burada bildiğiniz görevler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea319-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="ea319-111">Yalnızca değeri veya iki kez ayarlamak gerekiyorsa, ek olarak, bunu yapmak için kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="ea319-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="ea319-112">Son olarak, ilerleme çubuğu tarafından görüntülenen değeri azaltmak gerekiyorsa bu işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea319-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="ea319-113">Artırmak <xref:System.Windows.Forms.ProgressBar> tarafından sabit bir değer görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ea319-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="ea319-114">Bu yaklaşım basit sayısı minimum ve maksimum geçen süre veya dışında bilinen toplam işlenen dosya sayısı gibi arasında görüntülenirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea319-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="ea319-115">Artırmak <xref:System.Windows.Forms.ProgressBar> değişen değere göre görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ea319-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="ea319-116">Görüntülenen değer bir dizi farklı tutarlar kez değiştirmeniz gerektiğinde bu yararlı bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="ea319-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="ea319-117">Örnek bir dizi dosyası diske yazılırken kullanılan sabit disk alanı miktarını gösteren.</span><span class="sxs-lookup"><span data-stu-id="ea319-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="ea319-118">Bir ilerleme çubuğu tarafından görüntülenen değeri ayarlamak için en doğrudan yolu ayarlanmasıdır <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ea319-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="ea319-119">Bu tasarım zamanında veya çalışma zamanında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea319-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="ea319-120">ProgressBar değerini doğrudan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ea319-120">To set the ProgressBar value directly</span></span>  
  
1.  <span data-ttu-id="ea319-121">Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.</span><span class="sxs-lookup"><span data-stu-id="ea319-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="ea319-122">Kodda, denetimin ayarlama <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğine kurulan minimum ve maksimum değerleri arasında bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="ea319-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea319-123">Ayarlarsanız <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği belirlenen sınırlar dışında <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> denetimi özellikleri, yaratır bir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="ea319-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="ea319-124">Aşağıdaki kod örneğinde nasıl ayarlanacağını gösterir <xref:System.Windows.Forms.ProgressBar> doğrudan değeri.</span><span class="sxs-lookup"><span data-stu-id="ea319-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="ea319-125">Kod kayıtları veri kaynağından okur ve veri kaydı okuma her zaman ilerleme çubuğu ve etiket güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ea319-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="ea319-126">Bu örnekte, form olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetimi, bir <xref:System.Windows.Forms.ProgressBar> denetim ve veri tablosu olarak adlandırılan bir satır ile `CustomerRow` ile `FirstName` ve `LastName` alanları.</span><span class="sxs-lookup"><span data-stu-id="ea319-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Sabit bir aralıkla geçer ilerleme görüntülüyorsanız, değerini ayarlayın ve sonra artırır bir yöntem çağrısı <xref:System.Windows.Forms.ProgressBar> bu aralığa göre denetimin değeri. <span data-ttu-id="ea319-128">Bu, zamanlayıcılar ve ilerleme burada bütün bir yüzdesi olarak ölçme olmayan diğer senaryolar için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea319-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="ea319-129">İlerleme çubuğu tarafından sabit bir değer artırmak için</span><span class="sxs-lookup"><span data-stu-id="ea319-129">To increase the progress bar by a fixed value</span></span>  
  
1.  <span data-ttu-id="ea319-130">Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.</span><span class="sxs-lookup"><span data-stu-id="ea319-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="ea319-131">Denetimin ayarlamak <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliğini ilerleme çubuğunun artırmak üzere temsil eden bir tamsayı değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ea319-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3.  <span data-ttu-id="ea319-132">Çağrı <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> kümesinde tutar tarafından görüntülenen değeri değiştirmek için yöntemi <xref:System.Windows.Forms.ProgressBar.Step%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ea319-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="ea319-133">Aşağıdaki kod örneği, bir ilerleme çubuğu bir kopyalama işlemi dosyalarında sayısını nasıl koruyabilirsiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea319-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="ea319-134">Her dosya belleğe, salt okunur olduğundan aşağıdaki örnekte, ilerleme çubuğu ve etiket toplam dosya okuma yansıtacak şekilde güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ea319-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="ea319-135">Bu örnekte, form olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetim ve <xref:System.Windows.Forms.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="ea319-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Son olarak, böylece her artış benzersiz bir miktar bir ilerleme çubuğu tarafından görüntülenen değeri artırabilirsiniz. <span data-ttu-id="ea319-137">Bu, bir dizi farklı boyutlarda dosyaları bir sabit diske yazma ya da bütün bir yüzdesi olarak ilerlemesini ölçme gibi benzersiz işlemlerini izleyen olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ea319-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="ea319-138">İlerleme çubuğu dinamik bir değerle artırmak için</span><span class="sxs-lookup"><span data-stu-id="ea319-138">To increase the progress bar by a dynamic value</span></span>  
  
1.  <span data-ttu-id="ea319-139">Ayarlama <xref:System.Windows.Forms.ProgressBar> denetimin <xref:System.Windows.Forms.ProgressBar.Minimum%2A> ve <xref:System.Windows.Forms.ProgressBar.Maximum%2A> değerleri.</span><span class="sxs-lookup"><span data-stu-id="ea319-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="ea319-140">Çağrı <xref:System.Windows.Forms.ProgressBar.Increment%2A> belirttiğiniz bir tamsayı tarafından görüntülenen değeri değiştirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ea319-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="ea319-141">Aşağıdaki kod örneğinde, ne kadar disk alanı kopyalama işlemi sırasında kullanılan bir ilerleme çubuğu nasıl hesaplayabilirsiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea319-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="ea319-142">Her dosya sabit diske yazılır olarak aşağıdaki örnekte, ilerleme çubuğu ve etiket kullanılabilir sabit disk alanı miktarını yansıtacak şekilde güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ea319-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="ea319-143">Bu örnekte, form olmasını gerektirir bir <xref:System.Windows.Forms.Label> denetim ve <xref:System.Windows.Forms.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="ea319-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea319-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea319-144">See Also</span></span>  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [<span data-ttu-id="ea319-145">ProgressBar denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="ea319-145">ProgressBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="ea319-146">ProgressBar denetimi</span><span class="sxs-lookup"><span data-stu-id="ea319-146">ProgressBar Control</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
