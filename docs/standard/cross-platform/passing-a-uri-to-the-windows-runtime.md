---
title: URI'yı Windows Çalışma Zamanı'na Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: 7152fb02abf430c0d0e27b82550e4006e3958e93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288894"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="95183-102">URI'yı Windows Çalışma Zamanı'na Geçirme</span><span class="sxs-lookup"><span data-stu-id="95183-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="95183-103">Windows Çalışma Zamanı yöntemler yalnızca mutlak URI 'Leri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="95183-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="95183-104">Bir Windows Çalışma Zamanı yöntemine göreli bir URI geçirirseniz, bir <xref:System.ArgumentException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95183-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="95183-105">Neden: Windows Çalışma Zamanı .NET Framework kodda kullandığınızda, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıf <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="95183-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="95183-106"><xref:System.Uri?displayProperty=nameWithType>Sınıfı göreli URI 'lere izin verir, ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="95183-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="95183-107">Bu Ayrıca, Windows Çalışma Zamanı bileşenlerinde kullanıma sunabileceğiniz yöntemler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="95183-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="95183-108">Bileşeniniz URI alan bir yöntemi kullanıma sunarsa, kodunuzdaki imza dahil değildir <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95183-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95183-109">Ancak, bileşeninizin kullanıcıları için imza şunları içerir <xref:Windows.Foundation.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95183-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95183-110">Bileşeninizin geçirildiği bir URI mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95183-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="95183-111">Bu konu, bir mutlak URI 'nin nasıl algılanacağını ve uygulama paketindeki bir kaynağa başvururken nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95183-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="95183-112">Mutlak bir URI algılama ve kullanma</span><span class="sxs-lookup"><span data-stu-id="95183-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="95183-113"><xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>BIR URI 'nin Windows çalışma zamanı geçirmeden önce mutlak olduğundan emin olmak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="95183-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="95183-114">Bu özelliği kullanmak, özel durumu yakalama ve işlemeye kıyasla daha etkilidir <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="95183-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="95183-115">Uygulama paketindeki bir kaynak için mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="95183-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="95183-116">Uygulama paketinizin içerdiği bir kaynak için bir URI belirtmek istiyorsanız, `ms-appx` veya `ms-appx-web` düzenini kullanarak mutlak bir URI oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95183-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="95183-117">Aşağıdaki örnek, <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> <xref:Windows.UI.Xaml.Controls.WebView> <xref:Windows.UI.Xaml.Controls.Image.Source%2A> <xref:Windows.UI.Xaml.Controls.Image> hem XAML hem de kod kullanarak, bir denetimin özelliğinin ve sayfalar adlı bir klasörde bulunan kaynaklar için nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95183-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="95183-118">Bu şemalar hakkında daha fazla bilgi için bkz. Windows Geliştirme Merkezi 'nde [URI düzenleri](/windows/uwp/app-resources/uri-schemes) .</span><span class="sxs-lookup"><span data-stu-id="95183-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95183-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95183-119">See also</span></span>

- [<span data-ttu-id="95183-120">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="95183-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
