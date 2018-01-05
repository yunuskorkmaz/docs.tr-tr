---
title: "Nasıl yapılır: Windows Forms MonthCalendar denetimi &#39; Değiştir s görünümü"
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
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9c401532fa7a5f09462cf12084f32bca3f721cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a><span data-ttu-id="5ddcb-102">Nasıl yapılır: Windows Forms MonthCalendar denetimi &#39; Değiştir s görünümü</span><span class="sxs-lookup"><span data-stu-id="5ddcb-102">How to: Change the Windows Forms MonthCalendar Control&#39;s Appearance</span></span>
<span data-ttu-id="5ddcb-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetim birçok yolla Takvim görünümünü özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="5ddcb-104">Örneğin, renk düzenini ayarlama ve hafta numaralarını ve geçerli tarih görüntüleme veya gizleme seçin.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="5ddcb-105">Ay takvim renk düzenini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="5ddcb-105">To change the month calendar's color scheme</span></span>  
  
-   <span data-ttu-id="5ddcb-106">Özellikleri ayarlamak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ve <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="5ddcb-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Özelliği için haftanın günlerini de yazı tipi rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="5ddcb-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Özelliği koyun ve görüntülenen ay ya da ay takip tarihleri rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5ddcb-109">Temanın bağlı olarak Windows Vista ile başlayarak, bazı özelliklerin ayarlanmasını Takvim görünümünü değişmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="5ddcb-110">Örneğin, Windows Aero teması kullanmak üzere ayarlanmışsa ayarlama <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, veya <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özellikleri etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="5ddcb-111">Takvim güncelleştirilmiş bir sürümünü çalışma zamanında geçerli işletim sistemi temayı türetilmiş bir görünümü ile işlenen olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="5ddcb-112">Bu özellikleri kullanın ve Takvim önceki sürümünü etkinleştirmek istiyorsanız, uygulamanız için görsel stiller devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="5ddcb-113">Görsel stiller devre dışı bırakma görünümü ve davranışı, uygulamanızdaki diğer denetimlerin etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="5ddcb-114">Visual Basic'te görsel stiller devre dışı bırakmak için Proje Tasarımcısı'nı açın ve kutusunun işaretini kaldırın **etkinleştirmek XP görsel stilleri** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="5ddcb-115">C# görsel stiller devre dışı bırakmak için Program.cs açın ve çıkışı açıklama `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="5ddcb-116">Görsel stiller hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows XP görsel stilleri etkinleştir](http://msdn.microsoft.com/en-us/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span><span class="sxs-lookup"><span data-stu-id="5ddcb-116">For more information about visual styles, see [How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/en-us/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="5ddcb-117">Geçerli tarih denetimi altında görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="5ddcb-117">To display the current date at the bottom of the control</span></span>  
  
-   <span data-ttu-id="5ddcb-118">Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="5ddcb-119">Aşağıdaki örnek, görüntüleme ve form tıklatıldığında olduğunda bugünün tarihini atlama arasında geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     <span data-ttu-id="5ddcb-120">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-120">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="5ddcb-121">Hafta numaralarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="5ddcb-121">To display week numbers</span></span>  
  
-   <span data-ttu-id="5ddcb-122">Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="5ddcb-123">Bu özellik, kod veya özellikleri penceresinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="5ddcb-124">Haftanın ilk günü soluna ayrı bir sütunda hafta numaraları görünür.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5ddcb-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ddcb-125">See Also</span></span>  
 [<span data-ttu-id="5ddcb-126">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="5ddcb-126">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="5ddcb-127">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme</span><span class="sxs-lookup"><span data-stu-id="5ddcb-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="5ddcb-128">Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5ddcb-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="5ddcb-129">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5ddcb-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
