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
ms.openlocfilehash: c5ce0d4ac2b95dc4d51e785e3a00026f56c13d2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921387"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="f0401-102">URI'yı Windows Çalışma Zamanı'na Geçirme</span><span class="sxs-lookup"><span data-stu-id="f0401-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="f0401-103">Windows çalışma zamanı yöntemleri, yalnızca mutlak URI kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f0401-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="f0401-104">Göreli bir URI geçirirseniz bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemi, bir <xref:System.ArgumentException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f0401-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="f0401-105">Bunu istememizin nedeni: Kullanırken [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework kodunda <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı olarak görünür <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde.</span><span class="sxs-lookup"><span data-stu-id="f0401-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="f0401-106"><xref:System.Uri?displayProperty=nameWithType> Sınıfı göreli URI'ler sağlar ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı yok.</span><span class="sxs-lookup"><span data-stu-id="f0401-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="f0401-107">Bu da içinde ortaya çıkarttığınız yöntemler için doğru [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="f0401-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="f0401-108">Bileşeniniz URI alan bir yöntem sunarsa, kodunuzdaki imzası içerir <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0401-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f0401-109">Ancak bileşeninizin kullanıcıları için imza içerir <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0401-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f0401-110">Bileşeninize iletilen bir URI mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0401-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="f0401-111">Bu konuda, bir mutlak URI tespit etme ve bir uygulama paketinde bir kaynağa başvuran nasıl oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0401-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="f0401-112">Algılama ve mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="f0401-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="f0401-113">Kullanım <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> geçirmeden önce bir URI mutlak olduğundan emin olmak için özellik [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0401-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="f0401-114">Bu özellik kullanılarak durumunun yakalanmasından ve işlenmesinden verimlidir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="f0401-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="f0401-115">Uygulama paketinde bir kaynak için bir mutlak URI kullanma</span><span class="sxs-lookup"><span data-stu-id="f0401-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="f0401-116">Uygulama paketinizi içeren bir kaynak için URI belirtmek istiyorsanız, kullanabileceğiniz `ms-appx` veya `ms-appx-web` düzenini mutlak URI oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f0401-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="f0401-117">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> özelliği için bir <xref:Windows.UI.Xaml.Controls.WebView> denetimi ve <xref:Windows.UI.Xaml.Controls.Image.Source%2A> özelliği için bir <xref:Windows.UI.Xaml.Controls.Image> hem XAML hem kod kullanarak sayfaları adlı bir klasörde bulunan kaynaklara denetimi.</span><span class="sxs-lookup"><span data-stu-id="f0401-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="f0401-118">Bu şemalar hakkında daha fazla bilgi için bkz. [URI düzenleri](/windows/uwp/app-resources/uri-schemes) Windows geliştirme Merkezi'nde.</span><span class="sxs-lookup"><span data-stu-id="f0401-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0401-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0401-119">See also</span></span>

- [<span data-ttu-id="f0401-120">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="f0401-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
