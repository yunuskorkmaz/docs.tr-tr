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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926457"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="fef27-102">Createıdispatchstaforwarder işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fef27-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="fef27-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="fef27-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="fef27-104">Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fef27-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fef27-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="fef27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fef27-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fef27-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fef27-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="fef27-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="fef27-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="fef27-109">Bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fef27-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="fef27-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="fef27-110">ppForwarder</span></span>  
 <span data-ttu-id="fef27-111">Adresine bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fef27-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef27-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fef27-112">Requirements</span></span>  
 <span data-ttu-id="fef27-113">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fef27-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef27-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="fef27-114">**DLL:**</span></span>  
  
 <span data-ttu-id="fef27-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="fef27-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="fef27-116">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="fef27-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="fef27-117">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef27-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef27-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fef27-118">See also</span></span>

- [<span data-ttu-id="fef27-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fef27-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
