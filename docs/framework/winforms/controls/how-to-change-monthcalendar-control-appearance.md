---
title: MonthCalendar denetiminin görünümünü değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: ded9059ede4ad03f637c0e697b880c41a9a8ba32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746645"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="17439-102">Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="17439-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="17439-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi takvimin görünümünü birçok şekilde özelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="17439-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="17439-104">Örneğin, renk şemasını ayarlayabilir ve hafta numaralarını ve geçerli tarihi görüntülemeyi veya gizlemeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17439-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="17439-105">Aylık takvimin renk düzenini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="17439-105">To change the month calendar's color scheme</span></span>  
  
- <span data-ttu-id="17439-106"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ve <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17439-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="17439-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> özelliği, haftanın günleri için yazı tipi rengini de belirler.</span><span class="sxs-lookup"><span data-stu-id="17439-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="17439-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özelliği, görüntülenen aya veya aya önce gelen tarihlerin rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="17439-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    > <span data-ttu-id="17439-109">Windows Vista ile başlayıp temaya bağlı olarak, bazı özelliklerin ayarlanması takvimin görünümünü değiştiremeyebilir.</span><span class="sxs-lookup"><span data-stu-id="17439-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="17439-110">Örneğin, Windows, Aero temasını kullanmak üzere ayarlandıysa <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>veya <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özelliklerinin ayarlanması etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="17439-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="17439-111">Bunun nedeni, takvimin güncelleştirilmiş bir sürümünün geçerli işletim sistemi temasından çalışma zamanında elde edilen bir görünümle işlenmesinden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="17439-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="17439-112">Bu özellikleri kullanmak ve takvimin önceki sürümünü etkinleştirmek istiyorsanız, uygulamanız için görsel stilleri devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17439-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="17439-113">Görsel stilleri devre dışı bırakmak, uygulamanızdaki diğer denetimlerin görünümünü ve davranışını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="17439-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="17439-114">Visual Basic 'de görsel stilleri devre dışı bırakmak için proje tasarımcısını açın ve **XP görsel stillerini etkinleştir** onay kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="17439-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="17439-115">İçinde C#görsel stilleri devre dışı bırakmak için, program.cs açın ve dışarı açıklama `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="17439-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="17439-116">Görsel stiller hakkında daha fazla bilgi için bkz. [görsel stilleri etkinleştirme](/windows/desktop/controls/cookbook-overview).</span><span class="sxs-lookup"><span data-stu-id="17439-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="17439-117">Denetimin en altındaki geçerli tarihi görüntüleme</span><span class="sxs-lookup"><span data-stu-id="17439-117">To display the current date at the bottom of the control</span></span>  
  
- <span data-ttu-id="17439-118"><xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17439-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="17439-119">Aşağıdaki örnek, form çift tıklandığında bugünün tarihini görüntüleme ve atlama arasında geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="17439-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="17439-120">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="17439-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="17439-121">Hafta numaralarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="17439-121">To display week numbers</span></span>  
  
- <span data-ttu-id="17439-122"><xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17439-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="17439-123">Bu özelliği kodda ya da Özellikler penceresi olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17439-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="17439-124">Hafta numaraları, haftanın ilk gününün solunda ayrı bir sütunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="17439-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17439-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17439-125">See also</span></span>

- [<span data-ttu-id="17439-126">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="17439-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="17439-127">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme</span><span class="sxs-lookup"><span data-stu-id="17439-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="17439-128">Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="17439-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="17439-129">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="17439-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
