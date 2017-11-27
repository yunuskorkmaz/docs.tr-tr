---
title: "URI'yı Windows Çalışma Zamanı'na Geçirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4ef77fb9e196abf046e0d4648a49b5d4d3fad47e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="1307c-102">URI'yı Windows Çalışma Zamanı'na Geçirme</span><span class="sxs-lookup"><span data-stu-id="1307c-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="1307c-103">Windows çalışma zamanı yöntemleri yalnızca mutlak URI kabul edin.</span><span class="sxs-lookup"><span data-stu-id="1307c-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="1307c-104">Göreli URI'yı geçirirseniz bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemi, bir <xref:System.ArgumentException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="1307c-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="1307c-105">Neden şöyledir: kullandığınızda [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework kodda, [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) sınıfı görünür olarak <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde.</span><span class="sxs-lookup"><span data-stu-id="1307c-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="1307c-106"><xref:System.Uri?displayProperty=nameWithType> Sınıfı göreli URI'ler sağlar ancak [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) sınıfı yok.</span><span class="sxs-lookup"><span data-stu-id="1307c-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class does not.</span></span> <span data-ttu-id="1307c-107">Bu, aynı zamanda, kullanıma yöntemleri için geçerlidir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="1307c-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="1307c-108">Bileşeniniz bir URI götüren bir yöntemi gösterir, kodunuzda imza içeren <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1307c-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1307c-109">Ancak, bileşeniniz kullanıcılara imza içeren [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span><span class="sxs-lookup"><span data-stu-id="1307c-109">However, to users of your component, the signature includes [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span></span> <span data-ttu-id="1307c-110">Bileşeniniz için geçirilen bir URI mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1307c-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="1307c-111">Bu konu, bir mutlak URI algılanması ve bir uygulama paketinde bir kaynağa başvuran oluşturduğunuzda gösterir.</span><span class="sxs-lookup"><span data-stu-id="1307c-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="1307c-112">Algılama ve bir mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="1307c-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="1307c-113">Kullanım <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> geçirmeden önce bir URI mutlak olduğundan emin olmak için özellik [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1307c-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="1307c-114">Bu özellik kullanılarak yakalama ve işleme daha verimli <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="1307c-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="1307c-115">Uygulama paketini bir kaynak için bir mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="1307c-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="1307c-116">Uygulama paketinizi içeren bir kaynak için bir URI belirtmek istiyorsanız, kullanabileceğiniz `ms-appx` veya `ms-appx-web` bir mutlak URI oluşturmak için düzeni.</span><span class="sxs-lookup"><span data-stu-id="1307c-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="1307c-117">Aşağıdaki örnekte nasıl ayarlanacağını gösterir [kaynak](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) özelliği için bir [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) denetim ve [kaynak](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) özelliği için bir [görüntü](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) denetimi XAML ve kod sayfaları adlı bir klasörde yer alan kaynakları için kullanma.</span><span class="sxs-lookup"><span data-stu-id="1307c-117">The following example shows how to set the [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="1307c-118">Bu düzenleri hakkında daha fazla bilgi için bkz: [URI şemaları](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) Windows geliştirme Merkezi'ndeki.</span><span class="sxs-lookup"><span data-stu-id="1307c-118">For more information about these schemes, see [URI schemes](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1307c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1307c-119">See Also</span></span>  
 [<span data-ttu-id="1307c-120">Windows mağazası uygulamaları ve Windows çalışma zamanı için .NET framework desteği</span><span class="sxs-lookup"><span data-stu-id="1307c-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
