---
title: 'Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 9fd7f99b35730cf867bfad5da24bc3f223e9a0f8
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425327"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="6d51d-102">Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="6d51d-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="6d51d-103">Windows işletim sistemlerinde, bir kullanıcı, daha büyük veya küçük varsayılan yazı tipini görünür yapmak için sistem genelinde yazı tipi ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d51d-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="6d51d-104">Bu yazı tipi ayarları değiştirmek, ekranlarda metin okuma için daha büyük türü gerektirir ve görme engelli kullanıcılar için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6d51d-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="6d51d-105">Artırmayı veya yazı tipi düzeni değiştiğinde formun ve içerilen tüm metin boyutunu azaltmak için bu değişiklikler tepki vermek için Windows Forms uygulaması ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d51d-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="6d51d-106">Yazı tipi boyutlarını değişiklikleri dinamik olarak uyum sağlayacak şekilde formunuza istiyorsanız formunuza kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d51d-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="6d51d-107">Genellikle, Windows Forms tarafından kullanılan varsayılan yazı tipi tarafından döndürülen yazı tipi <xref:Microsoft.Win32> ad alanı çağrısına `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="6d51d-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="6d51d-108">Bu çağrı tarafından döndürülen yazı tipi, yalnızca ekran çözünürlüğü değiştiğinde değişir.</span><span class="sxs-lookup"><span data-stu-id="6d51d-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="6d51d-109">Aşağıdaki yordamda gösterildiği gibi kodunuzu için varsayılan yazı tipini değiştirmek <xref:System.Drawing.SystemFonts.IconTitleFont%2A> yazı tipi boyutu değişikliklere yanıt vermek için.</span><span class="sxs-lookup"><span data-stu-id="6d51d-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="6d51d-110">Masaüstü yazı tipini kullan ve yazı tipi şeması değişikliklerine yanıt</span><span class="sxs-lookup"><span data-stu-id="6d51d-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="6d51d-111">Formunuza oluşturun ve istediğiniz denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d51d-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="6d51d-112">Daha fazla bilgi için [nasıl yapılır: Komut satırından bir Windows Forms uygulaması oluşturma](how-to-create-a-windows-forms-application-from-the-command-line.md) ve [Windows Forms'da kullanılacak denetimler](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6d51d-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="6d51d-113">Bir başvuru ekleyin <xref:Microsoft.Win32> kodunuzda ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6d51d-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="6d51d-114">Oluşturucusu formunuz gerekli olay işleyicilerini yeteneklerinizi ve kullanım form için varsayılan yazı tipini değiştirmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d51d-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="6d51d-115">Uygulamak için bir işleyici <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> otomatik olarak ölçeklendirmek form neden olan bir olay olduğunda <xref:Microsoft.Win32.UserPreferenceCategory.Window> kategori değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="6d51d-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="6d51d-116">Son olarak, bir işleyici uygulamak <xref:System.Windows.Forms.Form.FormClosing> ayırır olay <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6d51d-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="6d51d-117">Bu kod eklemek için hata, uygulamanızın bellek sızıntısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6d51d-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="6d51d-118">Derleyin ve kod çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d51d-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="6d51d-119">El ile Windows XP'de yazı tipi düzeni değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="6d51d-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="6d51d-120">Windows Forms uygulamanız çalışırken Windows masaüstüne sağ tıklayın ve seçin **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="6d51d-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="6d51d-121">İçinde **görüntü özellikleri** iletişim kutusu, tıklayın **Görünüm** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6d51d-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="6d51d-122">Gelen **yazı tipi boyutu** aşağı açılan liste kutusunda, yeni bir yazı tipi boyutu seçin.</span><span class="sxs-lookup"><span data-stu-id="6d51d-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="6d51d-123">Form artık Masaüstü yazı tipi düzeni çalışma zamanı değişikliklere tepki verir olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d51d-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="6d51d-124">Kullanıcı değiştiğinde arasında **Normal**, **büyük yazı tipleri**, ve **ek büyük yazı tipleri**, form yazı tipi değiştirir ve doğru şekilde ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="6d51d-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d51d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d51d-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="6d51d-126">Bu kod örneği oluşturucuda bir çağrı içeren `InitializeComponent`, Visual Studio'da yeni bir Windows Forms projesi oluşturduğunuzda tanımlı olduğu.</span><span class="sxs-lookup"><span data-stu-id="6d51d-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="6d51d-127">Komut satırında, bir uygulama oluşturuyorsanız bu kod satırını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6d51d-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d51d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d51d-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="6d51d-129">Windows Forms'ta Otomatik Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="6d51d-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
