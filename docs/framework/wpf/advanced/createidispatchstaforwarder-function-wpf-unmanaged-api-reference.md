---
title: "CreateIDispatchSTAForwarder işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f43d3-102">CreateIDispatchSTAForwarder işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f43d3-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f43d3-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="f43d3-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f43d3-104">Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f43d3-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43d3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f43d3-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f43d3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f43d3-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f43d3-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f43d3-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="f43d3-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="f43d3-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="f43d3-109">Bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f43d3-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="f43d3-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="f43d3-110">ppForwarder</span></span>  
 <span data-ttu-id="f43d3-111">Adresine bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f43d3-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f43d3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f43d3-112">Requirements</span></span>  
 <span data-ttu-id="f43d3-113">**Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f43d3-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f43d3-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="f43d3-114">**DLL:**</span></span>  
  
 <span data-ttu-id="f43d3-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f43d3-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f43d3-116">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f43d3-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f43d3-117">**.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f43d3-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43d3-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f43d3-118">See Also</span></span>  
 [<span data-ttu-id="f43d3-119">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f43d3-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
