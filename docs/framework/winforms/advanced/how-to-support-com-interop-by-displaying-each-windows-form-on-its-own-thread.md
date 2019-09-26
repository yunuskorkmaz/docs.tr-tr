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
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306384"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="880ee-102">Nasıl yapılır: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme</span><span class="sxs-lookup"><span data-stu-id="880ee-102">How to: Support COM interop by displaying each Windows Form on its own thread</span></span>

<span data-ttu-id="880ee-103">Formunuzu, <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemini kullanarak oluşturabileceğiniz bir .NET Framework ileti döngüsünde görüntüleyerek com birlikte çalışabilirlik sorunlarını çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="880ee-103">You can resolve COM interoperability problems by displaying your form on a .NET Framework message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="880ee-104">Bir Windows formunun bir COM istemci uygulamasından düzgün çalışmasını sağlamak için, formu bir Windows Forms ileti döngüsünde çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="880ee-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="880ee-105">Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="880ee-105">To do this, use one of the following approaches:</span></span>

- <span data-ttu-id="880ee-106">Windows formunu göstermek için yönteminikullanın.<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="880ee-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="880ee-107">Daha fazla bilgi için [nasıl yapılır: ShowDialog yöntemi](com-interop-by-displaying-a-windows-form-shadow.md)Ile bir WINDOWS formunu görüntüleyerek com birlikte çalışabilirliğine destek.</span><span class="sxs-lookup"><span data-stu-id="880ee-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>

- <span data-ttu-id="880ee-108">Her Windows formunu ayrı bir iş parçacığında görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="880ee-108">Display each Windows Form on a separate thread.</span></span>

<span data-ttu-id="880ee-109">Visual Studio 'da bu özellik için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="880ee-109">There is extensive support for this feature in Visual Studio.</span></span>

<span data-ttu-id="880ee-110">Ayrıca bkz [. İzlenecek yol: Her bir Windows formunu kendi Iş parçacığında](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))görüntüleyerek com birlikte çalışmasını destekleme.</span><span class="sxs-lookup"><span data-stu-id="880ee-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="880ee-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="880ee-111">Example</span></span>

<span data-ttu-id="880ee-112">Aşağıdaki kod örneği, formun ayrı bir iş parçacığında nasıl görüntüleneceğini ve bu iş parçacığında bir Windows Forms <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> ileti göndericisi başlatmak için yöntemini çağırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="880ee-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="880ee-113">Bu yaklaşımı kullanmak için, <xref:System.Windows.Forms.Control.Invoke%2A> yöntemini kullanarak yönetilmeyen uygulamadan forma yapılan tüm çağrıları sıramalısınız.</span><span class="sxs-lookup"><span data-stu-id="880ee-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>

<span data-ttu-id="880ee-114">Bu yaklaşım, bir formun her örneğinin kendi iş parçacığında kendi ileti döngüsü kullanılarak çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="880ee-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="880ee-115">İş parçacığı başına birden fazla ileti döngüsü çalıştırıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="880ee-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="880ee-116">Bu nedenle, istemci uygulamanın ileti döngüsünü değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="880ee-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="880ee-117">Ancak, .NET Framework bileşenini kendi ileti döngüsünü kullanan yeni bir iş parçacığını başlatacak şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="880ee-117">However, you can modify the .NET Framework component to start a new thread that uses its own message loop.</span></span>

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a><span data-ttu-id="880ee-118">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="880ee-118">Compile the code</span></span>

<span data-ttu-id="880ee-119">, Ve türlerini adlı bir`COMWinform.dll`derlemedederleyin. `FormManager` `Form1` `COMForm`</span><span class="sxs-lookup"><span data-stu-id="880ee-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="880ee-120">Com [Için derleme paketleme](../../interop/packaging-an-assembly-for-com.md)bölümünde açıklanan yöntemlerden bırını kullanarak com birlikte çalışması için derlemeyi kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="880ee-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="880ee-121">Artık derlemeyi ve buna karşılık gelen tür kitaplığı (. tlb) dosyasını yönetilmeyen uygulamalarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="880ee-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="880ee-122">Örneğin, tür kitaplığını Visual Basic 6,0 yürütülebilir bir projede başvuru olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="880ee-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>

## <a name="see-also"></a><span data-ttu-id="880ee-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="880ee-123">See also</span></span>

- [<span data-ttu-id="880ee-124">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="880ee-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="880ee-125">COM için Bütünleştirilmiş Kod Paketleme</span><span class="sxs-lookup"><span data-stu-id="880ee-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="880ee-126">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="880ee-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="880ee-127">Nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışmasını destekleme</span><span class="sxs-lookup"><span data-stu-id="880ee-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="880ee-128">Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="880ee-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
