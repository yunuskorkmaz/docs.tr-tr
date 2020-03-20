---
title: CreateIDispatchSTAForwarder Fonksiyonu - WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174725"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="73501-102">CreateIDispatchSTAForwarder Fonksiyonu (WPF Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="73501-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="73501-103">Bu API, Windows Sunu Temeli (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="73501-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="73501-104">İş parçacığı ve windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73501-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73501-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73501-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="73501-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73501-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="73501-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="73501-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="73501-108">pDispatchTemsilcisi</span><span class="sxs-lookup"><span data-stu-id="73501-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="73501-109">`IDispatch` Arabirime işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73501-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="73501-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="73501-110">ppForwarder</span></span>  
 <span data-ttu-id="73501-111">`IDispatch` Arabirimin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73501-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73501-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73501-112">Requirements</span></span>  
 <span data-ttu-id="73501-113">**Platformlar:** Bkz. [.NET Çerçeve Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73501-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73501-114">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="73501-114">**DLL:**</span></span>  
  
 <span data-ttu-id="73501-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="73501-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="73501-116">.NET Framework 4 ve sonraki olarak: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="73501-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="73501-117">**.NET Çerçeve Sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73501-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73501-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73501-118">See also</span></span>

- [<span data-ttu-id="73501-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="73501-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
