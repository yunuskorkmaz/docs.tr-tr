---
title: 'Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 2451885c673515eb6690b0784fd5bd22de629209
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071152"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="f1027-102">Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="f1027-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="f1027-103">Windows işletim sistemlerinde, bir kullanıcı daha büyük veya küçük görünür varsayılan yazı tipi yapmak için sistem genelinde yazı tipi ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1027-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="f1027-104">Bu yazı tipi ayarlarını değiştirme ekranlarını üzerindeki metin okumak büyük türü gerektirir ve görme engelli kullanıcılar için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f1027-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="f1027-105">Bu değişiklikleri artırarak veya yazı tipi düzenini değiştiğinde form ve içerdiği tüm metin boyutunu azaltarak tepki vermek için Windows Forms uygulaması ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1027-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="f1027-106">Formunuz yazı tipi boyutlarını değişiklikleri dinamik olarak sağlamak istiyorsanız, kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1027-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="f1027-107">Genellikle, Windows Forms tarafından kullanılan varsayılan yazı tipi tarafından döndürülen yazı tipidir <xref:Microsoft.Win32> ad alanı çağrısına `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="f1027-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="f1027-108">Bu çağrı tarafından döndürülen yazı tipi yalnızca ekran çözünürlüğü değiştiğinde değişir.</span><span class="sxs-lookup"><span data-stu-id="f1027-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="f1027-109">Aşağıdaki yordamda gösterildiği gibi kodunuz için varsayılan yazı tipi değiştirmelisiniz <xref:System.Drawing.SystemFonts.IconTitleFont%2A> yazı tipi boyutunu değişikliklere yanıt.</span><span class="sxs-lookup"><span data-stu-id="f1027-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="f1027-110">Masaüstü yazı tipi kullanın ve yazı tipi şeması değişikliklerine yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="f1027-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="f1027-111">Formunuz oluşturun ve istediğiniz denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1027-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="f1027-112">Daha fazla bilgi için bkz: [nasıl yapılır: komut satırından bir Windows Forms uygulaması oluşturma](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) ve [Windows Forms'ta kullanılacak denetimler](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f1027-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="f1027-113">Bir başvuru ekleyin <xref:Microsoft.Win32> kodunuz için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f1027-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="f1027-114">Oluşturucuya formunuzu gerekli olay işleyicilerini bağlanmanıza ve form için kullanılan varsayılan yazı tipini değiştirmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1027-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="f1027-115">Uygulama için bir işleyici <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> otomatik olarak ölçeklendirme forma neden olan olay olduğunda <xref:Microsoft.Win32.UserPreferenceCategory.Window> kategori değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="f1027-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="f1027-116">Son olarak, uygulama için bir işleyici <xref:System.Windows.Forms.Form.FormClosing> ayırır olay <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f1027-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="f1027-117">Bu kod dahil etmek için hata bellek sızıntısı uygulamanıza neden olur.</span><span class="sxs-lookup"><span data-stu-id="f1027-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  <span data-ttu-id="f1027-118">Derleme ve kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f1027-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="f1027-119">El ile Windows XP'de yazı tipi düzenini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f1027-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="f1027-120">Windows Forms uygulamanızı çalışırken, Windows Masaüstü sağ tıklatın ve seçin **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f1027-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f1027-121">İçinde **görüntü özellikleri** iletişim kutusu, tıklatın **Görünüm** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f1027-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="f1027-122">Gelen **yazı tipi boyutu** aşağı açılan liste kutusunda, yeni bir yazı tipi boyutu seçin.</span><span class="sxs-lookup"><span data-stu-id="f1027-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="f1027-123">Form artık çalışma zamanı değişiklikleri Masaüstü yazı tipi düzenindeki tepki verdiğini olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f1027-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="f1027-124">Kullanıcı değiştiğinde arasında **Normal**, **büyük yazı tipleri**, ve **ekstra büyük yazı tipleri**, form yazı tipini değiştirir ve doğru şekilde ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="f1027-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1027-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1027-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="f1027-126">Bu kod örneğinde constructer yapılan bir çağrı içerir `InitializeComponent`, hangi Visual Studio'da yeni bir Windows Forms projesi oluşturduğunuzda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f1027-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="f1027-127">Bu kod satırı, komut satırında, uygulamanızın oluşturuluyorsa kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f1027-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1027-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1027-128">See Also</span></span>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [<span data-ttu-id="f1027-129">Windows Forms'ta Otomatik Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="f1027-129">Automatic Scaling in Windows Forms</span></span>](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
