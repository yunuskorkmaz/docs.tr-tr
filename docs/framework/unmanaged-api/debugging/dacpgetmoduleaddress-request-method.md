---
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
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860842"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="82f13-102">DacpGetModuleAddress::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82f13-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="82f13-103">Yapıyı verilen çalışma zamanı yapısından doldurma isteği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="82f13-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="82f13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82f13-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="82f13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82f13-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="82f13-106">'ndaki Çekirdek veri modülüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82f13-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="82f13-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82f13-107">Remarks</span></span>

<span data-ttu-id="82f13-108">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="82f13-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="82f13-109">Bunu kullanmak için, en kolay yöntem uygulamayı taklit etmek olur:</span><span class="sxs-lookup"><span data-stu-id="82f13-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="82f13-110">`IXCLRDataModule*` Parametre üzerinde `Request` yöntemi çağrılmadan elde edilen değeri aşağıdaki parametrelerle döndürün:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="82f13-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="82f13-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82f13-111">Requirements</span></span>

<span data-ttu-id="82f13-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="82f13-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="82f13-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="82f13-113">**Header:** None\</span></span>
<span data-ttu-id="82f13-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="82f13-114">**Library:** None\</span></span>
<span data-ttu-id="82f13-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82f13-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="82f13-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82f13-116">See also</span></span>

- [<span data-ttu-id="82f13-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="82f13-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="82f13-118">DacpGetModuleAddress yapısı</span><span class="sxs-lookup"><span data-stu-id="82f13-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
