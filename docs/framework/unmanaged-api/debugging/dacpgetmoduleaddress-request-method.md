---
title: DacpGetModuleAddress::Request yöntemi
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
ms.openlocfilehash: 07ad83da2bc608e3c5925664a68eec4a548860e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739221"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="1dfcb-102">DacpGetModuleAddress::Request yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dfcb-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="1dfcb-103">Belirtilen çalışma zamanı yapısı yapısından doldurmak için bir istek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1dfcb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dfcb-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="1dfcb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dfcb-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="1dfcb-106">[in] Çekirdek veri modülü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="1dfcb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dfcb-107">Remarks</span></span>

<span data-ttu-id="1dfcb-108">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1dfcb-109">Kullanmak için uygulama taklit etmek için en kolay yolu şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1dfcb-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="1dfcb-110">Arama öğesinden alınan değer döndürmek `Request` metodunda `IXCLRDataModule*` parametre şu parametrelerle: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="1dfcb-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="1dfcb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dfcb-111">Requirements</span></span>

<span data-ttu-id="1dfcb-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dfcb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1dfcb-113">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="1dfcb-113">**Header:** None</span></span>     
<span data-ttu-id="1dfcb-114">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-114">**Library:** None</span></span>  
<span data-ttu-id="1dfcb-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfcb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1dfcb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-116">See also</span></span>

- [<span data-ttu-id="1dfcb-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1dfcb-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="1dfcb-118">DacpGetModuleAddress arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dfcb-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)
