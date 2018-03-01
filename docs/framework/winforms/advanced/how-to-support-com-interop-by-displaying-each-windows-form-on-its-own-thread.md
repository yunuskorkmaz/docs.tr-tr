---
title: "Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60e52bc1486f74bdce44062a4ac861032b7b660c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="3393c-102">Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="3393c-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="3393c-103">Üzerinde formunu görüntüleyerek COM birlikte çalışma sorunları çözebilirsiniz bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanarak oluşturabilirsiniz ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3393c-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3393c-104">Bir COM istemci uygulamasından doğru şekilde bir Windows Form çalışmasını sağlamak için bir Windows Forms ileti döngüsü formun çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3393c-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="3393c-105">Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="3393c-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="3393c-106">Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows formunu görüntüleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3393c-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="3393c-107">Daha fazla bilgi için bkz: [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte'çalışma Destek](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="3393c-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="3393c-108">Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3393c-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="3393c-109">Bu özellik için kapsamlı destek [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3393c-109">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="3393c-110">Ayrıca bkz. [izlenecek yol: COM birlikte çalışma destekleme görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3393c-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3393c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3393c-111">Example</span></span>  
 <span data-ttu-id="3393c-112">Aşağıdaki kod örneğinde bir ayrı bir iş parçacığı ve çağrı formu görüntülenecek gösterilmiştir <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> o iş parçacığı üzerinde bir Windows Forms ileti Pompalama başlatmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3393c-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="3393c-113">Bu yaklaşımı kullanmak için formun yapılan her çağrı yönetilmeyen uygulamasından kullanarak sıralamanız gerekir <xref:System.Windows.Forms.Control.Invoke%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3393c-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="3393c-114">Bu yaklaşım, her bir form örneği kendi ileti döngüsü kullanarak kendi iş parçacığında çalıştırmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3393c-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="3393c-115">İş parçacığı çalışan birden fazla ileti döngüsüne sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="3393c-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="3393c-116">Bu nedenle, istemci uygulamanın ileti döngüsü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3393c-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="3393c-117">Ancak, değiştirebileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bileşeni için kendi ileti döngüsü kullanan yeni bir iş parçacığı başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3393c-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3393c-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3393c-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3393c-119">Derleme `COMForm`, `Form1`, ve `FormManager` bir bütünleştirilmiş türleri olarak da adlandırılır `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="3393c-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="3393c-120">COM birlikte çalışma için derleme açıklanan yöntemlerden birini kullanarak kaydedin [COM için derlemeyi paketleme](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="3393c-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="3393c-121">Artık derleme ve yönetilmeyen uygulamalar karşılık gelen alt türü kitaplığı (.tlb) dosyasında da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3393c-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="3393c-122">Örneğin, tür kitaplığı Visual Basic 6.0 yürütülebilir bir proje başvuru olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3393c-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3393c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3393c-123">See Also</span></span>  
 [<span data-ttu-id="3393c-124">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="3393c-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="3393c-125">COM için Bütünleştirilmiş Kod Paketleme</span><span class="sxs-lookup"><span data-stu-id="3393c-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [<span data-ttu-id="3393c-126">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="3393c-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="3393c-127">Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="3393c-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [<span data-ttu-id="3393c-128">Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3393c-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
