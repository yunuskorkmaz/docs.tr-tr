---
title: Createıdispatchstaforwarder Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738037"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="a8f0f-102">Createıdispatchstaforwarder Işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a8f0f-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="a8f0f-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="a8f0f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="a8f0f-104">İş parçacığı ve Windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8f0f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f0f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8f0f-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8f0f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8f0f-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a8f0f-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a8f0f-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="a8f0f-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="a8f0f-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="a8f0f-109">`IDispatch` arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8f0f-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="a8f0f-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="a8f0f-110">ppForwarder</span></span>  
 <span data-ttu-id="a8f0f-111">`IDispatch` arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8f0f-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f0f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8f0f-112">Requirements</span></span>  
 <span data-ttu-id="a8f0f-113">**Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8f0f-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f0f-114">**DOSYASıNı**</span><span class="sxs-lookup"><span data-stu-id="a8f0f-114">**DLL:**</span></span>  
  
 <span data-ttu-id="a8f0f-115">.NET Framework 3,0 ve 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="a8f0f-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="a8f0f-116">.NET Framework 4 ve üzeri: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="a8f0f-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="a8f0f-117">**.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8f0f-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f0f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f0f-118">See also</span></span>

- [<span data-ttu-id="a8f0f-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a8f0f-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
