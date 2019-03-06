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
ms.openlocfilehash: c4da322bf779e084f12529d0da6949ef6ada5cf3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379659"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f7959-102">Createıdispatchstaforwarder işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f7959-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f7959-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="f7959-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f7959-104">Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7959-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7959-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7959-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7959-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7959-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f7959-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7959-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="f7959-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="f7959-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="f7959-109">Bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f7959-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="f7959-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="f7959-110">ppForwarder</span></span>  
 <span data-ttu-id="f7959-111">Adresine bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f7959-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7959-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7959-112">Requirements</span></span>  
 <span data-ttu-id="f7959-113">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7959-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7959-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="f7959-114">**DLL:**</span></span>  
  
 <span data-ttu-id="f7959-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f7959-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f7959-116">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f7959-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f7959-117">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7959-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7959-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7959-118">See also</span></span>
- [<span data-ttu-id="f7959-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7959-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
