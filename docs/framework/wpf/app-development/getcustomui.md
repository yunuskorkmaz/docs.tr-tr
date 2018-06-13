---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: ff68c30c4e58cebb70c59352593d7b084413dce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548652"
---
# <a name="getcustomui"></a><span data-ttu-id="10162-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="10162-102">GetCustomUI</span></span>
<span data-ttu-id="10162-103">Ana bilgisayardan özel ilerleme durumu ve hata iletileri almak için PresentationHost.exe tarafından uygulanırsa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="10162-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10162-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10162-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10162-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10162-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="10162-106">[out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi içeren bütünleştirilmiş kodun bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="10162-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="10162-107">[out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi, tercihen olduğu sınıfın adını bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ile dosya <xref:System.Windows.Controls.Page> kendi üst seviye öğesidir.</span><span class="sxs-lookup"><span data-stu-id="10162-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="10162-108">Bu sınıf tarafından belirtilen derleme bulunur `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="10162-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="10162-109">[out] Ana bilgisayar tarafından sağlanan hata kullanıcı arabirimi içeren bütünleştirilmiş kodun bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="10162-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="10162-110">[out] Ana bilgisayar tarafından sağlanan hata kullanıcı sınıfının arabirim adı, tercihen ile bir XAML dosyası <xref:System.Windows.Controls.Page> kendi üst seviye öğesidir.</span><span class="sxs-lookup"><span data-stu-id="10162-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="10162-111">Bu sınıf tarafından belirtilen derleme bulunur `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="10162-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="10162-112">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10162-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="10162-113">HRESULT: yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="10162-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10162-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10162-114">Remarks</span></span>  
 <span data-ttu-id="10162-115">Bir ana bilgisayar uygulaması PresentationHost.exe'nin varsayılan kullanıcı arabirimleri için uygun olmayabilir belirli bir temaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="10162-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="10162-116">Bu durumda, ana bilgisayar uygulamasını uygulayabilirsiniz [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) ilerleme durumu ve hata kullanıcı arabirimleri PresentationHost.exe'ye izin verilecek.</span><span class="sxs-lookup"><span data-stu-id="10162-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="10162-117">PresentationHost.exe her zaman çağıracaktır [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) varsayılan kullanıcı arabirimlerinden kullanmadan önce.</span><span class="sxs-lookup"><span data-stu-id="10162-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="10162-118">Bu işlev bir kez PresentationHost'un sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="10162-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10162-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10162-119">See Also</span></span>  
 [<span data-ttu-id="10162-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="10162-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
