---
title: URI'yı Windows Çalışma Zamanı'na Geçirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: f1998c0664be323902489a3d0c1fa66a2c0aa578
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272852"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="08222-102">URI'yı Windows Çalışma Zamanı'na Geçirme</span><span class="sxs-lookup"><span data-stu-id="08222-102">Passing a URI to the Windows Runtime</span></span>

<span data-ttu-id="08222-103">Windows Çalışma Zamanı yöntemler yalnızca mutlak URI 'Leri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="08222-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="08222-104">Bir Windows Çalışma Zamanı yöntemine göreli bir URI geçirirseniz, bir <xref:System.ArgumentException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08222-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="08222-105">Neden: Windows Çalışma Zamanı .NET Framework kodda kullandığınızda, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıf <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="08222-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="08222-106"><xref:System.Uri?displayProperty=nameWithType>Sınıfı göreli URI 'lere izin verir, ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="08222-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="08222-107">Bu Ayrıca, Windows Çalışma Zamanı bileşenlerinde kullanıma sunabileceğiniz yöntemler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="08222-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="08222-108">Bileşeniniz URI alan bir yöntemi kullanıma sunarsa, kodunuzdaki imza dahil değildir <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08222-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08222-109">Ancak, bileşeninizin kullanıcıları için imza şunları içerir <xref:Windows.Foundation.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08222-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08222-110">Bileşeninizin geçirildiği bir URI mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08222-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="08222-111">Bu konu, bir mutlak URI 'nin nasıl algılanacağını ve uygulama paketindeki bir kaynağa başvururken nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08222-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="08222-112">Mutlak bir URI algılama ve kullanma</span><span class="sxs-lookup"><span data-stu-id="08222-112">Detecting and using an absolute URI</span></span>  

<span data-ttu-id="08222-113"><xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>BIR URI 'nin Windows çalışma zamanı geçirmeden önce mutlak olduğundan emin olmak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="08222-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="08222-114">Bu özelliği kullanmak, özel durumu yakalama ve işlemeye kıyasla daha etkilidir <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="08222-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="08222-115">Uygulama paketindeki bir kaynak için mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="08222-115">Using an absolute URI for a resource in the app package</span></span>  

<span data-ttu-id="08222-116">Uygulama paketinizin içerdiği bir kaynak için bir URI belirtmek istiyorsanız, `ms-appx` veya `ms-appx-web` düzenini kullanarak mutlak bir URI oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08222-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="08222-117">Aşağıdaki örnek, <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> <xref:Windows.UI.Xaml.Controls.WebView> <xref:Windows.UI.Xaml.Controls.Image.Source%2A> <xref:Windows.UI.Xaml.Controls.Image> hem XAML hem de kod kullanarak, bir denetimin özelliğinin ve sayfalar adlı bir klasörde bulunan kaynaklar için nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08222-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="08222-118">Bu şemalar hakkında daha fazla bilgi için bkz. Windows Geliştirme Merkezi 'nde [URI düzenleri](/windows/uwp/app-resources/uri-schemes) .</span><span class="sxs-lookup"><span data-stu-id="08222-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08222-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08222-119">See also</span></span>

- [<span data-ttu-id="08222-120">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="08222-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
