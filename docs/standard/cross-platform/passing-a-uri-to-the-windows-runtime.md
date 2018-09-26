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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f019c1075c119c3d814b3b7add8fe30f3e4d107
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156627"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="5e19a-102">URI'yı Windows Çalışma Zamanı'na Geçirme</span><span class="sxs-lookup"><span data-stu-id="5e19a-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="5e19a-103">Windows çalışma zamanı yöntemleri, yalnızca mutlak URI kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5e19a-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="5e19a-104">Göreli bir URI geçirirseniz bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemi, bir <xref:System.ArgumentException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e19a-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="5e19a-105">İşte nedenleri: kullandığınızda [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework kodunda <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı olarak görünür <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde.</span><span class="sxs-lookup"><span data-stu-id="5e19a-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="5e19a-106"><xref:System.Uri?displayProperty=nameWithType> Sınıfı göreli URI'ler sağlar ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı yok.</span><span class="sxs-lookup"><span data-stu-id="5e19a-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="5e19a-107">Bu da içinde ortaya çıkarttığınız yöntemler için doğru [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="5e19a-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="5e19a-108">Bileşeniniz URI alan bir yöntem sunarsa, kodunuzdaki imzası içerir <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e19a-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e19a-109">Ancak bileşeninizin kullanıcıları için imza içerir <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e19a-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e19a-110">Bileşeninize iletilen bir URI mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e19a-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="5e19a-111">Bu konuda, bir mutlak URI tespit etme ve bir uygulama paketinde bir kaynağa başvuran nasıl oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e19a-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="5e19a-112">Algılama ve mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="5e19a-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="5e19a-113">Kullanım <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> geçirmeden önce bir URI mutlak olduğundan emin olmak için özellik [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e19a-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="5e19a-114">Bu özellik kullanılarak durumunun yakalanmasından ve işlenmesinden verimlidir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="5e19a-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="5e19a-115">Uygulama paketinde bir kaynak için bir mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="5e19a-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="5e19a-116">Uygulama paketinizi içeren bir kaynak için URI belirtmek istiyorsanız, kullanabileceğiniz `ms-appx` veya `ms-appx-web` düzenini mutlak URI oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5e19a-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="5e19a-117">Aşağıdaki örnek nasıl ayarlanacağını gösterir [kaynak](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) özelliği için bir [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) denetimi ve [kaynak](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) özelliği için bir [görüntü](https://msdn.microsoft.com/library/windows/apps/br242752.aspx) denetimi XAML hem kod kullanarak sayfaları adlı bir klasörde bulunan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="5e19a-117">The following example shows how to set the [Source](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](https://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="5e19a-118">Bu şemalar hakkında daha fazla bilgi için bkz. [URI düzenleri](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx) Windows geliştirme Merkezi'nde.</span><span class="sxs-lookup"><span data-stu-id="5e19a-118">For more information about these schemes, see [URI schemes](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e19a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e19a-119">See also</span></span>

- [<span data-ttu-id="5e19a-120">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="5e19a-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
