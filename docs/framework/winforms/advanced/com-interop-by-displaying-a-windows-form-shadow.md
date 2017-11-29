---
title: "Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f01fc82be38f7c5acb02c28960785e97a782909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="eef21-102">Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="eef21-102">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>
<span data-ttu-id="eef21-103">Üzerinde Windows formunu görüntüleyerek Bileşen Nesne Modeli (COM) birlikte çalışabilirlik sorunlarını çözebilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanılarak oluşturulan ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eef21-103">You can resolve Component Object Model (COM) interoperability problems by displaying your Windows Form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which is created by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="eef21-104">Doğru bir COM istemci uygulamasından çalışması bir form yapmak için bir Windows Forms ileti döngüsü çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eef21-104">To make a form work correctly from a COM client application, you must run it on a Windows Forms message loop.</span></span> <span data-ttu-id="eef21-105">Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="eef21-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="eef21-106">Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows Form; görüntülenecek yöntemi</span><span class="sxs-lookup"><span data-stu-id="eef21-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form;</span></span>  
  
-   <span data-ttu-id="eef21-107">Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="eef21-107">Display each Windows Form on a separate thread.</span></span> <span data-ttu-id="eef21-108">Daha fazla bilgi için bkz: [nasıl yapılır: Destek COM birlikte çalışma görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span><span class="sxs-lookup"><span data-stu-id="eef21-108">For more information, see [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="eef21-109">Yordam</span><span class="sxs-lookup"><span data-stu-id="eef21-109">Procedure</span></span>  
 <span data-ttu-id="eef21-110">Kullanarak <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemi, bir form görüntülemek için en kolay yolu olabilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] olduğundan, döngü ileti isteğe bağlı olarak tüm yaklaşımlardan, uygulamak için en az kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eef21-110">Using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method can be the easiest way to display a form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop because, of all the approaches, it requires the least code to implement.</span></span>  
  
 <span data-ttu-id="eef21-111"><xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Yöntemi yönetilmeyen uygulamanın ileti döngüsü askıya alır ve formu olarak iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="eef21-111">The <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method suspends the unmanaged application's message loop and displays the form as a dialog box.</span></span> <span data-ttu-id="eef21-112">Konak uygulamanın ileti döngüsü askıya alındığından <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemi yeni bir oluşturur [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] formun iletileri işlemek için ileti döngüsü.</span><span class="sxs-lookup"><span data-stu-id="eef21-112">Because the host application's message loop has been suspended, the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method creates a new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop to process the form's messages.</span></span>  
  
 <span data-ttu-id="eef21-113">Kullanmanın olumsuz yanı <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemdir form kalıcı bir iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="eef21-113">The disadvantage of using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method is that the form will be opened as a modal dialog box.</span></span> <span data-ttu-id="eef21-114">Windows formu açıkken bu davranış herhangi bir kullanıcı arabirimi (UI) çağıran uygulamada engeller.</span><span class="sxs-lookup"><span data-stu-id="eef21-114">This behavior blocks any user interface (UI) in the calling application while the Windows Form is open.</span></span> <span data-ttu-id="eef21-115">Kullanıcı formu çıktığında [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ileti döngüsü kapatır ve döngü başlatır yeniden çalıştırmayı önceki uygulamanın ileti.</span><span class="sxs-lookup"><span data-stu-id="eef21-115">When the user exits the form, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop closes and the earlier application's message loop starts running again.</span></span>  
  
 <span data-ttu-id="eef21-116">Windows Forms içinde formu göstermek için bir yöntem olan bir sınıf kitaplığı oluşturmak ve COM birlikte çalışma için sınıf kitaplığı oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="eef21-116">You can create a class library in Windows Forms which has a method to show the form, and then build the class library for COM interop.</span></span> <span data-ttu-id="eef21-117">Visual Basic 6.0 veya Microsoft Foundation sınıfları (MFC) bu DLL dosyasını kullanabilirsiniz ve bu ortamları birinden çağırabilirsiniz <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> formun görüntülenecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eef21-117">You can use this DLL file from Visual Basic 6.0 or Microsoft Foundation Classes (MFC), and from either of these environments you can call the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the form.</span></span>  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="eef21-118">ShowDialog yöntemi ile bir windows formunu görüntüleyerek COM birlikte çalışma desteklemek için</span><span class="sxs-lookup"><span data-stu-id="eef21-118">To support COM interop by displaying a windows form with the ShowDialog method</span></span>  
  
-   <span data-ttu-id="eef21-119">Tüm çağrıları Değiştir <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> çağrıları yöntemiyle <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönteminde, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bileşeni.</span><span class="sxs-lookup"><span data-stu-id="eef21-119">Replace all calls to the <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> method with calls to the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method in your [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef21-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eef21-120">See Also</span></span>  
 [<span data-ttu-id="eef21-121">.NET Framework bileşenlerini COM'da gösterme</span><span class="sxs-lookup"><span data-stu-id="eef21-121">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="eef21-122">Nasıl yapılır: her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme</span><span class="sxs-lookup"><span data-stu-id="eef21-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [<span data-ttu-id="eef21-123">Windows Forms ve yönetilmeyen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="eef21-123">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
