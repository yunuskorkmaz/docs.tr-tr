---
title: Windows Forms'ta Kullanıcı Girdisi
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
ms.openlocfilehash: fef51f57dd3c14c91572041a72c805823d6019a3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740941"
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="56101-102">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="56101-102">User Input in Windows Forms</span></span>
<span data-ttu-id="56101-103">Windows Forms ilgili Windows iletilerini işleme sırasında başlatılan olaylara dayalı bir kullanıcı giriş modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="56101-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="56101-104">Bu bölümdeki konular, belirli görevlerin nasıl gerçekleştirileceğini gösteren kod örnekleri dahil olmak üzere, fare ve klavye kullanıcı girişi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56101-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56101-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="56101-105">In This Section</span></span>  
 [<span data-ttu-id="56101-106">Bir Windows Forms Uygulamasında Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="56101-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="56101-107">Kullanıcı giriş olayları ve Windows iletileri işleyen yöntemler hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="56101-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="56101-108">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="56101-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="56101-109">Klavye ileti işleme, anahtarları ve klavye olaylarının farklı türde bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56101-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="56101-110">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="56101-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="56101-111">Bilgi üzerinde fare olayları ve fare imleçleri ve fare yakalamayı dahil olmak üzere diğer fare güvenlikle ilgili özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="56101-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="56101-112">Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma</span><span class="sxs-lookup"><span data-stu-id="56101-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="56101-113">Program aracılığıyla fare ve klavye girdisi benzetimini yapmak için birkaç farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56101-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="56101-114">Nasıl yapılır: Windows Forms Denetimlerinde Kullanıcı Girdi Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="56101-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="56101-115">Çoğu kullanıcı girdi olaylarını işleme ve her olay hakkında bilgiler raporları bir kod örneği sunar.</span><span class="sxs-lookup"><span data-stu-id="56101-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="56101-116">Windows Forms'ta Kullanıcı Girdisi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="56101-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="56101-117">Windows Forms uygulamalarında kullanıcı girişini doğrulama yöntemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56101-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56101-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="56101-118">Related Sections</span></span>  
 <span data-ttu-id="56101-119">Ayrıca bkz: [Windows Forms'ta olay işleyicileri oluşturma](https://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="56101-119">Also see [Creating Event Handlers in Windows Forms](https://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span></span>
