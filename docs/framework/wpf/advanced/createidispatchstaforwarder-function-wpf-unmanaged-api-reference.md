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
ms.openlocfilehash: 1a19b7699c7a9e2b663149ea31bccb67189e68c4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487830"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b74d8-102">Createıdispatchstaforwarder işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b74d8-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b74d8-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="b74d8-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b74d8-104">Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b74d8-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b74d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b74d8-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="b74d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b74d8-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b74d8-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b74d8-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b74d8-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="b74d8-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="b74d8-109">Bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b74d8-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="b74d8-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="b74d8-110">ppForwarder</span></span>  
 <span data-ttu-id="b74d8-111">Adresine bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b74d8-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b74d8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b74d8-112">Requirements</span></span>  
 <span data-ttu-id="b74d8-113">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b74d8-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b74d8-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="b74d8-114">**DLL:**</span></span>  
  
 <span data-ttu-id="b74d8-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b74d8-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b74d8-116">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b74d8-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b74d8-117">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b74d8-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74d8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b74d8-118">See also</span></span>
- [<span data-ttu-id="b74d8-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b74d8-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
