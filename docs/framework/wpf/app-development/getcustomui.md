---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005716"
---
# <a name="getcustomui"></a><span data-ttu-id="230a2-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="230a2-102">GetCustomUI</span></span>
<span data-ttu-id="230a2-103">Uygulanırsa, konaktan Özel ilerleme ve hata iletilerini almak için PresentationHost. exe tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="230a2-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="230a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="230a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="230a2-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="230a2-106">dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="230a2-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="230a2-107">dışı Konak tarafından sağlanan ilerleme Kullanıcı arabirimi olan sınıfın adı, tercihen <xref:System.Windows.Controls.Page> olan XAML dosyası en üst düzey öğesidir.</span><span class="sxs-lookup"><span data-stu-id="230a2-107">[out] The name of the class that is the host-supplied progress user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="230a2-108">Bu sınıf `pwzProgressAssemblyName` tarafından belirtilen derlemede bulunur.</span><span class="sxs-lookup"><span data-stu-id="230a2-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="230a2-109">dışı Konak tarafından sağlanan hata Kullanıcı arabirimini içeren derlemeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="230a2-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="230a2-110">dışı Konak tarafından sağlanan hata Kullanıcı arabirimi olan sınıfın adı, tercihen <xref:System.Windows.Controls.Page> olan XAML dosyası en üst düzey öğesidir.</span><span class="sxs-lookup"><span data-stu-id="230a2-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="230a2-111">Bu sınıf `pwzErrorAssemblyName` tarafından belirtilen derlemede bulunur.</span><span class="sxs-lookup"><span data-stu-id="230a2-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="230a2-112">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="230a2-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="230a2-113">HRESULT: yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="230a2-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="230a2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="230a2-114">Remarks</span></span>  
 <span data-ttu-id="230a2-115">Bir ana bilgisayar uygulaması, PresentationHost. exe ' nin varsayılan kullanıcı arabirimlerinin uygun olabileceği belirli bir temaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="230a2-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="230a2-116">Bu durumda, konak uygulama, PresentationHost. exe ' ye ilerleme ve hata kullanıcı arabirimlerini döndürmek için [GetCustomUI](getcustomui.md) uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="230a2-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="230a2-117">PresentationHost. exe, varsayılan kullanıcı arabirimlerini kullanmadan önce her zaman [GetCustomUI](getcustomui.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="230a2-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="230a2-118">Bu işlev, PresentationHost 'ın başlatılması sırasında bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="230a2-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="230a2-119">See also</span></span>

- [<span data-ttu-id="230a2-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="230a2-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
