---
title: Windows Forms uygulamasındaki yazı tipi şeması değişikliklerine yanıt verme
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739234"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="df44f-102">Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="df44f-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="df44f-103">Windows işletim sistemlerinde, bir Kullanıcı, varsayılan yazı tipinin daha büyük veya küçük görünmesini sağlamak için sistem genelindeki yazı tipi ayarlarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="df44f-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="df44f-104">Bu yazı tipi ayarlarının değiştirilmesi, görme engelli kullanıcılar için kritiktir ve ekranlarındaki metni okumak için daha büyük bir tür gerektirir.</span><span class="sxs-lookup"><span data-stu-id="df44f-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="df44f-105">Windows Forms uygulamanızı, form boyutunu artırarak veya azaltarak ve yazı tipi şeması her değiştiğinde içerilen tüm metinler için bu değişikliklere tepki verecek şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df44f-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="df44f-106">Formunuzun yazı tipi boyutlarında değişiklikleri dinamik olarak sığbilmesini istiyorsanız formunuza kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df44f-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="df44f-107">Genellikle, Windows Forms tarafından kullanılan varsayılan yazı tipi, `GetStockObject(DEFAULT_GUI_FONT)`<xref:Microsoft.Win32> ad alanı çağrısının döndürdüğü yazı tipidir.</span><span class="sxs-lookup"><span data-stu-id="df44f-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="df44f-108">Bu çağrının döndürdüğü yazı tipi yalnızca ekran çözünürlüğü değiştiğinde değişir.</span><span class="sxs-lookup"><span data-stu-id="df44f-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="df44f-109">Aşağıdaki yordamda gösterildiği gibi, yazı tipi boyutundaki değişikliklere yanıt vermek için kodunuzun varsayılan yazı tipini <xref:System.Drawing.SystemFonts.IconTitleFont%2A> değiştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="df44f-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="df44f-110">Masaüstü yazı tipini kullanmak ve yazı tipi şeması değişikliklerine yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="df44f-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="df44f-111">Formunuzu oluşturun ve istediğiniz denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="df44f-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="df44f-112">Daha fazla bilgi için, bkz. [nasıl yapılır: komut satırından Windows Forms uygulama oluşturma](how-to-create-a-windows-forms-application-from-the-command-line.md) ve [Windows Forms kullanılacak denetimler](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="df44f-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="df44f-113">Kodunuza <xref:Microsoft.Win32> ad alanına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="df44f-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="df44f-114">Aşağıdaki kodu, gerekli olay işleyicilerini bağlamak ve form için kullanılan varsayılan yazı tipini değiştirmek için formunuzun oluşturucusuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="df44f-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="df44f-115"><xref:Microsoft.Win32.UserPreferenceCategory.Window> kategorisi değiştiğinde formun otomatik olarak ölçeklendirilmesine neden olan <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="df44f-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="df44f-116">Son olarak, <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay işleyicisini ayırır <xref:System.Windows.Forms.Form.FormClosing> olayı için bir işleyici uygulayın.</span><span class="sxs-lookup"><span data-stu-id="df44f-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="df44f-117">Bu kodun dahil edilmemesi, uygulamanızın belleği sızdırmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="df44f-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="df44f-118">Kodu derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df44f-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="df44f-119">Windows XP 'de yazı tipi düzenini el ile değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="df44f-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="df44f-120">Windows Forms uygulamanız çalışırken, Windows masaüstüne sağ tıklayıp kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="df44f-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="df44f-121">**Görüntü özellikleri** Iletişim kutusunda **Görünüm** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df44f-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="df44f-122">**Yazı tipi boyutu** aşağı açılan liste kutusundan yeni bir yazı tipi boyutu seçin.</span><span class="sxs-lookup"><span data-stu-id="df44f-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="df44f-123">Formun artık Masaüstü yazı tipi düzeninde çalışma zamanı değişikliklerine tepki verdiğini fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="df44f-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="df44f-124">Kullanıcı **normal**, **büyük yazı tipleri**ve çok **büyük yazı tipleri**arasında değişiklik yaparken, form yazı tipini değiştirir ve doğru şekilde ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="df44f-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df44f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="df44f-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="df44f-126">Bu kod örnekteki Oluşturucu, Visual Studio 'da yeni bir Windows Forms projesi oluşturduğunuzda tanımlanan `InitializeComponent`için bir çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="df44f-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="df44f-127">Uygulamanızı komut satırında oluşturuyorsanız bu kod satırını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="df44f-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df44f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df44f-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="df44f-129">Windows Forms'ta Otomatik Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="df44f-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
