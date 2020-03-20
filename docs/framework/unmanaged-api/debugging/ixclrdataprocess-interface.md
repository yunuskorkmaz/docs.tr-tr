---
title: IXCLRDataProcess Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178371"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="f9f66-102">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9f66-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="f9f66-103">Bir işlem hakkında bilgi sorgulama yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9f66-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="f9f66-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f9f66-104">Methods</span></span>

| <span data-ttu-id="f9f66-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f9f66-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="f9f66-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9f66-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="f9f66-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="f9f66-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="f9f66-108">Kendine `AppDomain` özgü kimliğiyle bir süreçten geçer.</span><span class="sxs-lookup"><span data-stu-id="f9f66-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="f9f66-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="f9f66-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="f9f66-110">Bir işlemin modüllerini sayısallandırmak için bir tutamaç sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9f66-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="f9f66-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="f9f66-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="f9f66-112">Bu işlemin modüllerini oyalar.</span><span class="sxs-lookup"><span data-stu-id="f9f66-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="f9f66-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="f9f66-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="f9f66-114">Modül numaralandırması sırasında kullanılan dahili yinelemeciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="f9f66-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="f9f66-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="f9f66-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="f9f66-116">Belirli bir adresten `AppDomain` başlama yöntemi örneklerini sayısallandırmak için bir tutamaç sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9f66-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="f9f66-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="f9f66-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="f9f66-118">Bir adres mahsup adresinden başlayan bu işlemin yöntem örneklerini dizir.</span><span class="sxs-lookup"><span data-stu-id="f9f66-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="f9f66-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="f9f66-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="f9f66-120">Örnek numaralandırma sırasında kullanılan iç yinelemeciler tarafından kullanılan kaynakları söyler.</span><span class="sxs-lookup"><span data-stu-id="f9f66-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="f9f66-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9f66-121">Remarks</span></span>

<span data-ttu-id="f9f66-122">Bu arabirim çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="f9f66-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f9f66-123">Ancak, her zamanki COM mekanizmaları ile `IUnknown` elde `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` edilebilir GUID ile türetilmiştir bir COM arayüzü.</span><span class="sxs-lookup"><span data-stu-id="f9f66-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9f66-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9f66-124">Requirements</span></span>

<span data-ttu-id="f9f66-125">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9f66-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="f9f66-126">**Üstbilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f9f66-126">**Header:** None</span></span>  
<span data-ttu-id="f9f66-127">**Kütüphane:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f9f66-127">**Library:** None</span></span>  
<span data-ttu-id="f9f66-128">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9f66-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f9f66-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f66-129">See also</span></span>

- [<span data-ttu-id="f9f66-130">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f9f66-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="f9f66-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f9f66-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
