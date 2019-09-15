---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991373"
---
# <a name="getcustomui"></a><span data-ttu-id="5b811-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="5b811-102">GetCustomUI</span></span>
<span data-ttu-id="5b811-103">Uygulanırsa, konaktan Özel ilerleme ve hata iletilerini almak için PresentationHost. exe tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5b811-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b811-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b811-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b811-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b811-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="5b811-106">dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b811-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="5b811-107">dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimi olan sınıfın adı, tercihen içeren [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] <xref:System.Windows.Controls.Page> bir dosya en üst düzey öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5b811-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="5b811-108">Bu sınıf, tarafından `pwzProgressAssemblyName`belirtilen derlemede bulunur.</span><span class="sxs-lookup"><span data-stu-id="5b811-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="5b811-109">dışı Konak tarafından sağlanan hata Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b811-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="5b811-110">dışı Konak tarafından sağlanan hata Kullanıcı arabirimi olan sınıfın adı, tercihen içeren <xref:System.Windows.Controls.Page> bir xaml dosyası, en üst düzey öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5b811-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="5b811-111">Bu sınıf, tarafından `pwzErrorAssemblyName`belirtilen derlemede bulunur.</span><span class="sxs-lookup"><span data-stu-id="5b811-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5b811-112">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b811-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="5b811-113">HRESULT LIP.</span><span class="sxs-lookup"><span data-stu-id="5b811-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b811-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b811-114">Remarks</span></span>  
 <span data-ttu-id="5b811-115">Bir ana bilgisayar uygulaması, PresentationHost. exe ' nin varsayılan kullanıcı arabirimlerinin uygun olabileceği belirli bir temaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b811-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="5b811-116">Bu durumda, konak uygulama, PresentationHost. exe ' ye ilerleme ve hata kullanıcı arabirimlerini döndürmek için [GetCustomUI](getcustomui.md) uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="5b811-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="5b811-117">PresentationHost. exe, varsayılan kullanıcı arabirimlerini kullanmadan önce her zaman [GetCustomUI](getcustomui.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="5b811-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="5b811-118">Bu işlev, PresentationHost 'ın başlatılması sırasında bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5b811-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b811-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b811-119">See also</span></span>

- [<span data-ttu-id="5b811-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="5b811-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
