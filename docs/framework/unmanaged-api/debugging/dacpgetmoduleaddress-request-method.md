---
description: 'Şu konuda daha fazla bilgi edinin: DacpGetModuleAddress:: Request Yöntemi'
title: DacpGetModuleAddress::Request Yöntemi
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4cdec9cf6b9bd818ce1137fb5b2c691532fab94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801507"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="8869a-103">DacpGetModuleAddress::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8869a-103">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="8869a-104">Yapıyı verilen çalışma zamanı yapısından doldurma isteği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8869a-104">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8869a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8869a-105">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="8869a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8869a-106">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="8869a-107">'ndaki Çekirdek veri modülüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8869a-107">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="8869a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8869a-108">Remarks</span></span>

<span data-ttu-id="8869a-109">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="8869a-109">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="8869a-110">Bunu kullanmak için, en kolay yöntem uygulamayı taklit etmek olur:</span><span class="sxs-lookup"><span data-stu-id="8869a-110">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="8869a-111">Parametre üzerinde yöntemi çağrılmadan elde edilen değeri `Request` `IXCLRDataModule*` aşağıdaki parametrelerle döndürün: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="8869a-111">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="8869a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8869a-112">Requirements</span></span>

<span data-ttu-id="8869a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="8869a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="8869a-114">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="8869a-114">**Header:** None\</span></span>
<span data-ttu-id="8869a-115">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="8869a-115">**Library:** None\</span></span>
<span data-ttu-id="8869a-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8869a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8869a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8869a-117">See also</span></span>

- [<span data-ttu-id="8869a-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8869a-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="8869a-119">DacpGetModuleAddress yapısı</span><span class="sxs-lookup"><span data-stu-id="8869a-119">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
