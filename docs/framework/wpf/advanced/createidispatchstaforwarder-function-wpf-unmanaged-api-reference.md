---
title: "CreateIDispatchSTAForwarder işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9502e-102">CreateIDispatchSTAForwarder işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9502e-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="9502e-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="9502e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="9502e-104">Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9502e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9502e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9502e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9502e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9502e-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9502e-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9502e-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="9502e-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="9502e-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="9502e-109">Bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9502e-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="9502e-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="9502e-110">ppForwarder</span></span>  
 <span data-ttu-id="9502e-111">Adresine bir işaretçi bir `IDispatch` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9502e-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9502e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9502e-112">Requirements</span></span>  
 <span data-ttu-id="9502e-113">**Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9502e-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9502e-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="9502e-114">**DLL:**</span></span>  
  
 <span data-ttu-id="9502e-115">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="9502e-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="9502e-116">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="9502e-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="9502e-117">**.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9502e-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9502e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9502e-118">See Also</span></span>  
 [<span data-ttu-id="9502e-119">WPF yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9502e-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
