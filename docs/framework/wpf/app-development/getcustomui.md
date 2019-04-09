---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 30084143949d2243fd310448c52e6b861505ad66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191256"
---
# <a name="getcustomui"></a><span data-ttu-id="a845d-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="a845d-102">GetCustomUI</span></span>
<span data-ttu-id="a845d-103">Konaktan özel ilerleme durumu ve hata iletileri almak için PresentationHost.exe tarafından uygulanması durumunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a845d-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a845d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a845d-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a845d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a845d-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="a845d-106">[out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi içeren derleme için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a845d-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="a845d-107">[out] Ana bilgisayar tarafından sağlanan kullanıcı arabirimi, tercihen olduğu sınıfın adını bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ile dosya <xref:System.Windows.Controls.Page> kendi üst düzey bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="a845d-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="a845d-108">Bu sınıf tarafından belirtilen derlemede bulunan `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="a845d-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="a845d-109">[out] Ana bilgisayar tarafından sağlanan hata kullanıcı arabirimi içeren derleme için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a845d-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="a845d-110">[out] Ana bilgisayar tarafından sağlanan hata kullanıcı sınıf adı arabirim, tercihen bir XAML dosyasıyla <xref:System.Windows.Controls.Page> kendi üst düzey bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="a845d-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="a845d-111">Bu sınıf tarafından belirtilen derlemede bulunan `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="a845d-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a845d-112">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a845d-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="a845d-113">HRESULT: Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="a845d-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a845d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a845d-114">Remarks</span></span>  
 <span data-ttu-id="a845d-115">Bir ana bilgisayar uygulaması PresentationHost.exe ait varsayılan kullanıcı arabirimleri için uymayabilir belirli bir tema olabilir.</span><span class="sxs-lookup"><span data-stu-id="a845d-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="a845d-116">Bu durumda, ana bilgisayar uygulaması uygulayabilirsiniz [GetCustomUI](getcustomui.md) ilerleme durumu ve hata PresentationHost.exe için kullanıcı arabirimleri dönün.</span><span class="sxs-lookup"><span data-stu-id="a845d-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="a845d-117">PresentationHost.exe her zaman çağıracaktır [GetCustomUI](getcustomui.md) varsayılan kullanıcı arabirimlerini kullanmadan önce.</span><span class="sxs-lookup"><span data-stu-id="a845d-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="a845d-118">Bu işlev, bir kez PresentationHost'un sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a845d-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a845d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a845d-119">See also</span></span>

- [<span data-ttu-id="a845d-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="a845d-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
