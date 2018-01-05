---
title: "Yönetilen HTML Belgesi Nesne Modelini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 876cee67f917291214d6ea8b9abf7d2975c1fd25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="f1717-102">Yönetilen HTML Belgesi Nesne Modelini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1717-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="f1717-103">Yönetilen HTML belgesi nesne modeli (DOM) dayalı bir sarmalayıcı sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Internet Explorer tarafından kullanıma sunulan HTML sınıfları için.</span><span class="sxs-lookup"><span data-stu-id="f1717-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="f1717-104">Barındırılan HTML sayfaları işlemek için bu sınıfları kullanan <xref:System.Windows.Forms.WebBrowser> denetimi veya başlangıçtan itibaren yeni sayfalar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f1717-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1717-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f1717-105">In This Section</span></span>  
 [<span data-ttu-id="f1717-106">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modeline Erişme</span><span class="sxs-lookup"><span data-stu-id="f1717-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1717-107">Geçerli bir örneği elde açıklar <xref:System.Windows.Forms.HtmlDocument> bir Windows Forms uygulamasında veya <xref:System.Windows.Forms.UserControl> Internet Explorer'da barındırılan.</span><span class="sxs-lookup"><span data-stu-id="f1717-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="f1717-108">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme</span><span class="sxs-lookup"><span data-stu-id="f1717-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1717-109">Özgün, değiştirilmemiş HTML kaynağını edinme ve DOM geçerli durumunu yansıtır "canlı" kaynak edinme açıklar</span><span class="sxs-lookup"><span data-stu-id="f1717-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="f1717-110">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f1717-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1717-111">Öğeleri görsel görünümünü denetlemek için kullanılan stiller işlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="f1717-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="f1717-112">Yönetilen HTML Belgesi Nesne Modelindeki Çerçevelere Erişme</span><span class="sxs-lookup"><span data-stu-id="f1717-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1717-113">Çerçeveleri ve çerçeve kümelerini nelerdir ve bir çerçeve DOM erişmek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="f1717-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="f1717-114">Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme</span><span class="sxs-lookup"><span data-stu-id="f1717-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1717-115">Yönetilen eşdeğeri olmayan temel DOM üyelerine erişmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="f1717-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1717-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f1717-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="f1717-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f1717-117">Related Sections</span></span>  
 [<span data-ttu-id="f1717-118">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="f1717-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1717-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1717-119">See Also</span></span>  
 [<span data-ttu-id="f1717-120">DHTML nesne modeli hakkında</span><span class="sxs-lookup"><span data-stu-id="f1717-120">About the DHTML Object Model</span></span>](http://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
