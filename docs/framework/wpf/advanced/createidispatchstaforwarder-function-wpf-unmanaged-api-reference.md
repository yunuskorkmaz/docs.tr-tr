---
title: Createıdispatchstaforwarder işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: a89b29cd459060c93d5ca77bb2154e1a10b02d03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213656"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="7cc43-102">Createıdispatchstaforwarder işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7cc43-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="7cc43-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="7cc43-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="7cc43-104">Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7cc43-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc43-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cc43-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc43-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cc43-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7cc43-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7cc43-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="7cc43-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="7cc43-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="7cc43-109">Bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7cc43-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="7cc43-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="7cc43-110">ppForwarder</span></span>  
 <span data-ttu-id="7cc43-111">Adresine bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7cc43-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc43-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cc43-112">Requirements</span></span>  
 <span data-ttu-id="7cc43-113">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cc43-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cc43-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="7cc43-114">**DLL:**</span></span>  
  
 <span data-ttu-id="7cc43-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="7cc43-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="7cc43-116">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="7cc43-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="7cc43-117">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc43-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc43-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cc43-118">See also</span></span>

- [<span data-ttu-id="7cc43-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7cc43-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
