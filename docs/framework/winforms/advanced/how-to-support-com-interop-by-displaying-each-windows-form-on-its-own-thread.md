---
title: 'Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 39a9793f3046960032da32795e60314ea05a00fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072681"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="f7cef-102">Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="f7cef-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="f7cef-103">Üzerinde formunu görüntüleyerek COM birlikte çalışabilirlik sorunları çözebilirsiniz bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanarak oluşturabileceğiniz ileti döngüsü, <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7cef-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f7cef-104">Bir COM istemci uygulamasından doğru şekilde bir Windows Form çalışmasını sağlamak için form üzerinde bir Windows Forms ileti döngüsü çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7cef-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="f7cef-105">Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7cef-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="f7cef-106">Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows formu görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7cef-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="f7cef-107">Daha fazla bilgi için [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışmasını destekleme](com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="f7cef-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="f7cef-108">Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f7cef-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="f7cef-109">Visual Studio'da bu özellik için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7cef-109">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="f7cef-110">Ayrıca bkz: [izlenecek yol: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f7cef-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7cef-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7cef-111">Example</span></span>  
 <span data-ttu-id="f7cef-112">Aşağıdaki kod örneği, bir ayrı iş parçacığı ve çağrı formu görüntülemek gösterilmiştir <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> o iş parçacığı üzerinde bir Windows Forms ileti pompası başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7cef-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="f7cef-113">Bu yaklaşımı kullanmak için form yönetilmeyen bir uygulamadan gelen çağrıları kullanarak sıralamanız gerekir <xref:System.Windows.Forms.Control.Invoke%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7cef-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="f7cef-114">Bu yaklaşım, formu her örneği, kendi ileti döngüsü kullanarak kendi iş parçacığında çalıştıran gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f7cef-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="f7cef-115">Çalışan iş parçacığı birden fazla ileti döngüsü sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7cef-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="f7cef-116">Bu nedenle, istemci uygulamanın ileti döngüsü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7cef-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="f7cef-117">Ancak, değiştirebileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kendi ileti döngüsü kullanan yeni bir iş parçacığı bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f7cef-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7cef-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f7cef-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f7cef-119">Derleme `COMForm`, `Form1`, ve `FormManager` tür bir derleme olarak adlandırılan `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="f7cef-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="f7cef-120">COM birlikte çalışma bütünleştirilmiş kod içinde açıklanan yöntemlerden birini kullanarak kayıt [COM için derlemeyi paketleme](../../interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="f7cef-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="f7cef-121">Artık, derleme ve yönetilmeyen uygulamalarda karşılık gelen tür kitaplığını (.tlb) dosyasını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7cef-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="f7cef-122">Örneğin, bir Visual Basic 6.0 yürütülebilir projeyi başvuru olarak tür kitaplığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7cef-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7cef-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7cef-123">See also</span></span>

- [<span data-ttu-id="f7cef-124">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="f7cef-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="f7cef-125">COM için Bütünleştirilmiş Kod Paketleme</span><span class="sxs-lookup"><span data-stu-id="f7cef-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="f7cef-126">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="f7cef-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="f7cef-127">Nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışma desteği</span><span class="sxs-lookup"><span data-stu-id="f7cef-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="f7cef-128">Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f7cef-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
