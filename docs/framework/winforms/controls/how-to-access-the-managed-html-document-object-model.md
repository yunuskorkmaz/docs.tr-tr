---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modeline Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 04d5f9e6f128d9b4ed3f07a5faebe06ae4ffdebf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315198"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="7fb67-102">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modeline Erişme</span><span class="sxs-lookup"><span data-stu-id="7fb67-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="7fb67-103">Yönetilen HTML belgesi nesne modeli (DOM) iki tür uygulamalar arasında erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7fb67-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
-   <span data-ttu-id="7fb67-104">Barındırılan yönetilen bir Windows Forms uygulaması (.exe) <xref:System.Windows.Forms.WebBrowser> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7fb67-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="7fb67-105">Bu iki teknoloji, ile tamamlayıcı <xref:System.Windows.Forms.WebBrowser> denetimi için kullanıcı ve belgenin mantıksal yapısını temsil eden HTML DOM sayfa görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="7fb67-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
-   <span data-ttu-id="7fb67-106">Bir Windows Forms <xref:System.Windows.Forms.UserControl> Internet Explorer içinde barındırılan.</span><span class="sxs-lookup"><span data-stu-id="7fb67-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="7fb67-107">Sayfayı temsil eden HTML DOM erişebilir, <xref:System.Windows.Forms.UserControl> belgenin yapısını değiştirebilir veya diğer birçok olası arasında kalıcı iletişim kutuları açmak için barındırılır.</span><span class="sxs-lookup"><span data-stu-id="7fb67-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="7fb67-108">DOM bir Windows Forms uygulamasından erişmek için</span><span class="sxs-lookup"><span data-stu-id="7fb67-108">To access DOM from a Windows Forms application</span></span>  
  
1. <span data-ttu-id="7fb67-109">Konak bir <xref:System.Windows.Forms.WebBrowser> Windows Forms uygulamanızdaki denetlemek ve izlemek için <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="7fb67-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="7fb67-110">Denetimleri barındırma ve olaylar için izleme hakkında daha fazla bilgi için bkz [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7fb67-110">For details on hosting controls and monitoring for events, see [Events](../../../standard/events/index.md).</span></span>  
  
2. <span data-ttu-id="7fb67-111">Alma <xref:System.Windows.Forms.HtmlDocument> erişerek geçerli sayfa için <xref:System.Windows.Forms.WebBrowser.Document%2A> özelliği <xref:System.Windows.Forms.WebBrowser> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7fb67-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="7fb67-112">Internet Explorer'da barındırılan bir UserControl DOM erişmek için</span><span class="sxs-lookup"><span data-stu-id="7fb67-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1. <span data-ttu-id="7fb67-113">Kendi özel bir türetilmiş sınıf, oluşturmak <xref:System.Windows.Forms.UserControl> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7fb67-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="7fb67-114">Daha fazla bilgi için [nasıl yapılır: Bileşik denetimler yazma](how-to-author-composite-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7fb67-114">For more information, see [How to: Author Composite Controls](how-to-author-composite-controls.md).</span></span>  
  
2. <span data-ttu-id="7fb67-115">Aşağıdaki kod, yük olay işleyicisi içine yerleştirin, <xref:System.Windows.Forms.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="7fb67-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7fb67-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7fb67-116">Robust Programming</span></span>  
  
1. <span data-ttu-id="7fb67-117">DOM ile kullanıldığında <xref:System.Windows.Forms.WebBrowser> denetimi, her zaman beklemesi gereken kadar <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olaylarının erişmeyi denemeden önce <xref:System.Windows.Forms.WebBrowser.Document%2A> özelliği <xref:System.Windows.Forms.WebBrowser> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7fb67-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="7fb67-118"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Tüm belgeyi yüklendikten sonra olayı oluşturulur; daha önce DOM kullanırsanız, uygulamanızda bir çalışma zamanı özel durumuna neden risk.</span><span class="sxs-lookup"><span data-stu-id="7fb67-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7fb67-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7fb67-119">.NET Framework Security</span></span>  
  
1. <span data-ttu-id="7fb67-120">Uygulamanızı veya <xref:System.Windows.Forms.UserControl> yönetilen HTML DOM erişmek için tam güven gerektirir</span><span class="sxs-lookup"><span data-stu-id="7fb67-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="7fb67-121">Bir Windows Forms uygulaması kullanarak dağıtıyorsanız [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], tam güven izni yükseltme ya da güvenilir uygulama dağıtımı kullanarak isteyebilir; bkz [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="7fb67-121">If you are deploying a Windows Forms application using [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb67-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fb67-122">See also</span></span>

- [<span data-ttu-id="7fb67-123">Yönetilen HTML Belgesi Nesne Modelini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7fb67-123">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
