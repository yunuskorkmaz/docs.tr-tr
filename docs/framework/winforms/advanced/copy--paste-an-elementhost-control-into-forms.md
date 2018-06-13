---
title: 'İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 1cce981e4cb04ab6ed6ed41e0afac0121b242761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520948"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="f1196-102">İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="f1196-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="f1196-103">Bu kılavuz bir Windows Presentation Foundation (WPF) denetimi bir Windows formundan kopyalama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1196-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="f1196-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="f1196-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f1196-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f1196-105">Create the project.</span></span>  
  
-   <span data-ttu-id="f1196-106">WPF denetimi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f1196-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1196-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f1196-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f1196-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f1196-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f1196-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f1196-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f1196-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f1196-110">Prerequisites</span></span>  
 <span data-ttu-id="f1196-111">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="f1196-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="f1196-112">.</span><span class="sxs-lookup"><span data-stu-id="f1196-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f1196-113">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1196-113">Creating the Project</span></span>  
 <span data-ttu-id="f1196-114">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="f1196-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1196-115">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f1196-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f1196-116">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f1196-116">To create the project</span></span>  
  
-   <span data-ttu-id="f1196-117">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="f1196-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="f1196-118">WPF denetimi kopyalama</span><span class="sxs-lookup"><span data-stu-id="f1196-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="f1196-119">Projeye bir WPF denetimi ekledikten sonra projeyi diğer formlara kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1196-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="f1196-120">WPF denetimi kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="f1196-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="f1196-121">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="f1196-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="f1196-122">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f1196-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="f1196-123">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f1196-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="f1196-124">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f1196-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="f1196-125">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="f1196-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="f1196-126">Gelen **araç**, bir örneğini sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="f1196-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="f1196-127">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="f1196-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="f1196-128">İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f1196-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="f1196-129">Yeni bir Windows Form projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1196-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="f1196-130">Form türü için varsayılan adı kullanacak `Form2`.</span><span class="sxs-lookup"><span data-stu-id="f1196-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="f1196-131">İle `Form2` bir kopyasını yapıştırmak için CTRL + V tuşlarına basın Windows Forms Tasarımcısı'nda açmak `elementHost1` forma.</span><span class="sxs-lookup"><span data-stu-id="f1196-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="f1196-132">Kopyalanan denetimi olarak da adlandırılır `elementHost1`, özel alanı olduğundan `Form2` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f1196-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="f1196-133">Hiçbir ad çakışması olan yoktur `elementHost1` içinde `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f1196-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1196-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1196-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f1196-135">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f1196-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="f1196-136">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1196-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="f1196-137">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="f1196-137">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
