---
title: Windows Forms'ta Kullanıcı Girdisi
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
ms.openlocfilehash: 2a618dae8d5f2f5ea6a6581fff2758fe8419f511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537739"
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="50dcc-102">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="50dcc-102">User Input in Windows Forms</span></span>
<span data-ttu-id="50dcc-103">Windows Forms ilgili Windows iletilerini işlerken oluşan olayları temel alan bir kullanıcı giriş modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="50dcc-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="50dcc-104">Bu bölümdeki konular, belirli görevler gerçekleştirmek üzere nasıl gösteren kod örnekleri dahil olmak üzere, fare ve klavye kullanıcı girişi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="50dcc-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50dcc-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="50dcc-105">In This Section</span></span>  
 [<span data-ttu-id="50dcc-106">Bir Windows Forms Uygulamasında Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="50dcc-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="50dcc-107">Kullanıcı giriş olaylarını ve Windows iletilerini işleme yöntemlerini genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="50dcc-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="50dcc-108">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="50dcc-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="50dcc-109">Klavye ileti işleme, anahtarları ve klavye olaylarının farklı türleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="50dcc-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="50dcc-110">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="50dcc-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="50dcc-111">Olayları ve fare imleçleri ve fare yakalama dahil olmak üzere diğer fare güvenlikle ilgili özellikler fareyi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="50dcc-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="50dcc-112">Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma</span><span class="sxs-lookup"><span data-stu-id="50dcc-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="50dcc-113">Program aracılığıyla fare ve klavye girdisi benzetimini yapmak için birkaç farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50dcc-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="50dcc-114">Nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı Girdi Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="50dcc-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="50dcc-115">Çoğu kullanıcı girdi olaylarını işleme ve rapor, her olay ilgili bilgiler bir kod örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="50dcc-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="50dcc-116">Windows Forms'ta Kullanıcı Girdisi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="50dcc-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="50dcc-117">Windows Forms uygulamalarında kullanıcı girişi doğrulamak için yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="50dcc-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="50dcc-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="50dcc-118">Related Sections</span></span>  
 <span data-ttu-id="50dcc-119">Ayrıca bkz. [Windows Forms'ta olay işleyicileri oluşturma](http://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="50dcc-119">Also see [Creating Event Handlers in Windows Forms](http://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span></span>
