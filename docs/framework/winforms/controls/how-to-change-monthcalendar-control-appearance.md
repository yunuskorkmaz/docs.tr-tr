---
title: 'Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 2e26f7a9db8e19b584000089f99e99aab7c25a32
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716380"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="fcebc-102">Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="fcebc-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="fcebc-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi birçok yönden Takvim görünümünü özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcebc-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="fcebc-104">Örneğin, bir renk şeması ayarlayın ve hafta sayıları ve geçerli tarih görüntülemek veya gizlemek seçin.</span><span class="sxs-lookup"><span data-stu-id="fcebc-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="fcebc-105">Ay takvim renk düzenini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="fcebc-105">To change the month calendar's color scheme</span></span>  
  
-   <span data-ttu-id="fcebc-106">Özellikleri ayarlamak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ve <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcebc-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="fcebc-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Özelliği için haftanın günlerini de yazı tipi rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="fcebc-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="fcebc-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Özelliği koyun ve görüntülenen ayı veya ay izleyen tarihleri rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="fcebc-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    >  <span data-ttu-id="fcebc-109">Tema bağlı olarak Windows Vista ile başlayarak, bazı özellikleri ayarlama Takvim görünümünü değişmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="fcebc-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="fcebc-110">Örneğin, Windows Aero teması kullanmak üzere ayarlanmışsa ayarlamak <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, veya <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özellikleri etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="fcebc-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="fcebc-111">Takvim güncelleştirilmiş bir sürümünü geçerli işletim sistemi temayı çalışma zamanında türetilmiş bir görünümle işlenen olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fcebc-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="fcebc-112">Bu özellikleri kullanmak ve Takvim önceki sürümünü etkinleştirmek istiyorsanız, uygulamanız için görsel stil devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcebc-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="fcebc-113">Görsel stiller devre dışı bırakma, görünümünü ve davranışını uygulamanızdaki diğer denetimlerin etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fcebc-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="fcebc-114">Visual Basic'te görsel stiller devre dışı bırakmak için Proje Tasarımcısı'nı açın ve işaretini kaldırın **etkinleştirme XP görsel stilleri** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="fcebc-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="fcebc-115">C# görsel stiller devre dışı bırakmak için program.cs dosyasını açın ve açıklama `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="fcebc-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="fcebc-116">Görsel stiller hakkında daha fazla bilgi için bkz: [görsel stilleri etkinleştirme](/windows/desktop/controls/cookbook-overview).</span><span class="sxs-lookup"><span data-stu-id="fcebc-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="fcebc-117">Geçerli bir tarih denetiminin altındaki görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="fcebc-117">To display the current date at the bottom of the control</span></span>  
  
-   <span data-ttu-id="fcebc-118">Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fcebc-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="fcebc-119">Aşağıdaki örnekte, görüntüleme ve ne zaman formun çift tıklandığında bugünün tarihini atlama arasında geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="fcebc-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="fcebc-120">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fcebc-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="fcebc-121">Hafta sayıları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="fcebc-121">To display week numbers</span></span>  
  
-   <span data-ttu-id="fcebc-122">Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fcebc-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="fcebc-123">Bu özellik, kod veya Özellikler penceresinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcebc-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="fcebc-124">Hafta sayıları haftanın ilk günü solundaki ayrı bir sütunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fcebc-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fcebc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcebc-125">See also</span></span>
- [<span data-ttu-id="fcebc-126">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="fcebc-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="fcebc-127">Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin</span><span class="sxs-lookup"><span data-stu-id="fcebc-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="fcebc-128">Nasıl yapılır: Windows ile belirli günleri kalın olarak görüntüleme Forms MonthCalendar denetimi</span><span class="sxs-lookup"><span data-stu-id="fcebc-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="fcebc-129">Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fcebc-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
