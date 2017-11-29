---
title: "İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65882925c6fbe3e9b393b139a937bc9a1f95ed04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="2a653-102">İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Formlarına Kopyalama ve Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="2a653-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="2a653-103">Bu kılavuz bir Windows Presentation Foundation (WPF) denetimi bir Windows formundan kopyalama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2a653-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="2a653-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="2a653-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="2a653-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a653-105">Create the project.</span></span>  
  
-   <span data-ttu-id="2a653-106">WPF denetimi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2a653-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a653-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2a653-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2a653-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2a653-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2a653-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2a653-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2a653-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2a653-110">Prerequisites</span></span>  
 <span data-ttu-id="2a653-111">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="2a653-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="2a653-112">.</span><span class="sxs-lookup"><span data-stu-id="2a653-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2a653-113">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a653-113">Creating the Project</span></span>  
 <span data-ttu-id="2a653-114">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="2a653-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a653-115">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2a653-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="2a653-116">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2a653-116">To create the project</span></span>  
  
-   <span data-ttu-id="2a653-117">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="2a653-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="2a653-118">WPF denetimi kopyalama</span><span class="sxs-lookup"><span data-stu-id="2a653-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="2a653-119">Projeye bir WPF denetimi ekledikten sonra projeyi diğer formlara kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a653-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="2a653-120">WPF denetimi kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="2a653-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="2a653-121">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> çözüme proje.</span><span class="sxs-lookup"><span data-stu-id="2a653-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="2a653-122">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="2a653-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="2a653-123">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="2a653-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="2a653-124">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a653-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="2a653-125">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="2a653-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="2a653-126">Gelen **araç**, bir örneğini sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="2a653-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="2a653-127">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="2a653-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="2a653-128">İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="2a653-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="2a653-129">Yeni bir Windows Form projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a653-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="2a653-130">Form türü için varsayılan adı kullanacak `Form2`.</span><span class="sxs-lookup"><span data-stu-id="2a653-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="2a653-131">İle `Form2` bir kopyasını yapıştırmak için CTRL + V tuşlarına basın Windows Forms Tasarımcısı'nda açmak `elementHost1` forma.</span><span class="sxs-lookup"><span data-stu-id="2a653-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="2a653-132">Kopyalanan denetimi olarak da adlandırılır `elementHost1`, özel alanı olduğundan `Form2` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2a653-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="2a653-133">Hiçbir ad çakışması olan yoktur `elementHost1` içinde `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2a653-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a653-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a653-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="2a653-135">Geçiş ve birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="2a653-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="2a653-136">WPF denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2a653-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="2a653-137">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="2a653-137">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
