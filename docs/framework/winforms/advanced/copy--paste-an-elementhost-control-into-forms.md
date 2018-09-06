---
title: 'İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037259"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="c95b8-102">İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="c95b8-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="c95b8-103">Bu izlenecek yol, bir Windows formdan başka bir Windows Presentation Foundation (WPF) denetimi kopyalamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c95b8-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="c95b8-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="c95b8-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="c95b8-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c95b8-105">Create the project.</span></span>  
  
-   <span data-ttu-id="c95b8-106">Bir WPF denetiminde kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c95b8-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c95b8-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c95b8-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c95b8-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c95b8-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c95b8-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c95b8-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c95b8-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c95b8-110">Prerequisites</span></span>  
 <span data-ttu-id="c95b8-111">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="c95b8-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="c95b8-112">.</span><span class="sxs-lookup"><span data-stu-id="c95b8-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="c95b8-113">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c95b8-113">Creating the Project</span></span>  
 <span data-ttu-id="c95b8-114">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="c95b8-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c95b8-115">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c95b8-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="c95b8-116">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c95b8-116">To create the project</span></span>  
  
-   <span data-ttu-id="c95b8-117">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="c95b8-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="c95b8-118">Bir WPF denetiminde kopyalama</span><span class="sxs-lookup"><span data-stu-id="c95b8-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="c95b8-119">Bir WPF denetiminde projeye ekledikten sonra projedeki diğer formlara kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c95b8-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="c95b8-120">Bir WPF denetiminde kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="c95b8-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="c95b8-121">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> çözüme bir proje.</span><span class="sxs-lookup"><span data-stu-id="c95b8-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c95b8-122">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c95b8-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c95b8-123">Daha fazla bilgi için [izlenecek yol: oluşturma yeni WPF içeriği Windows Forms'ta tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c95b8-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="c95b8-124">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c95b8-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="c95b8-125">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="c95b8-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="c95b8-126">Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="c95b8-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="c95b8-127">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c95b8-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="c95b8-128">İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="c95b8-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="c95b8-129">Projeye yeni bir Windows formu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c95b8-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="c95b8-130">Form türü için varsayılan adı kullanacak `Form2`.</span><span class="sxs-lookup"><span data-stu-id="c95b8-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="c95b8-131">İle `Form2` Windows Form Tasarımcısı'nda bir kopyasını yapıştırmak için CTRL + V tuşlarına basarak açın `elementHost1` forma.</span><span class="sxs-lookup"><span data-stu-id="c95b8-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="c95b8-132">Kopyalanan denetimi olarak da adlandırılır `elementHost1`, özel bir alan olduğundan `Form2` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c95b8-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="c95b8-133">İle hiçbir ad çakışması var. `elementHost1` içinde `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c95b8-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95b8-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c95b8-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="c95b8-135">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="c95b8-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="c95b8-136">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c95b8-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="c95b8-137">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="c95b8-137">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
