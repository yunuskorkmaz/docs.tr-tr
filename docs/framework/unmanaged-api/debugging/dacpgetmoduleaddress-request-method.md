---
title: DacpGetModuleAddress::İstek Yöntemi
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
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179207"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="71dfd-102">DacpGetModuleAddress::İstek Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71dfd-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="71dfd-103">Yapıyı verilen çalışma zamanı yapısından doldurmak için bir istek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="71dfd-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="71dfd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71dfd-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="71dfd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71dfd-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="71dfd-106">[içinde] Tohum veri modülü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71dfd-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="71dfd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71dfd-107">Remarks</span></span>

<span data-ttu-id="71dfd-108">Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="71dfd-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="71dfd-109">Kullanmak için en kolay yolu uygulamayı taklit etmektir:</span><span class="sxs-lookup"><span data-stu-id="71dfd-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="71dfd-110">`IXCLRDataModule*` Parametreüzerindeki `Request` yöntemi çağırarak elde edilen değeri aşağıdaki parametrelerle döndür`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="71dfd-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="71dfd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71dfd-111">Requirements</span></span>

<span data-ttu-id="71dfd-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71dfd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="71dfd-113">**Üstbilgi:** Yok **Kütüphane:** Yok</span><span class="sxs-lookup"><span data-stu-id="71dfd-113">**Header:** None **Library:** None</span></span>  
<span data-ttu-id="71dfd-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="71dfd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="71dfd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71dfd-115">See also</span></span>

- [<span data-ttu-id="71dfd-116">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="71dfd-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="71dfd-117">DacpGetModuleAdres Arayüzü</span><span class="sxs-lookup"><span data-stu-id="71dfd-117">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)
