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
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102913"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="6f090-102">DacpGetModuleAddress::İstek Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f090-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="6f090-103">Yapıyı verilen çalışma zamanı yapısından doldurmak için bir istek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f090-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6f090-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f090-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="6f090-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f090-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="6f090-106">[içinde] Tohum veri modülü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f090-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f090-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f090-107">Remarks</span></span>

<span data-ttu-id="6f090-108">Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="6f090-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6f090-109">Kullanmak için en kolay yolu uygulamayı taklit etmektir:</span><span class="sxs-lookup"><span data-stu-id="6f090-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="6f090-110">`IXCLRDataModule*` Parametreüzerindeki `Request` yöntemi çağırarak elde edilen değeri aşağıdaki parametrelerle döndür`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="6f090-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="6f090-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f090-111">Requirements</span></span>

<span data-ttu-id="6f090-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="6f090-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md)</span></span>\
<span data-ttu-id="6f090-113">**Üstbilgi:** Yok</span><span class="sxs-lookup"><span data-stu-id="6f090-113">**Header:** None</span></span>\
<span data-ttu-id="6f090-114">**Kütüphane:** Yok</span><span class="sxs-lookup"><span data-stu-id="6f090-114">**Library:** None</span></span>\
<span data-ttu-id="6f090-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6f090-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6f090-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f090-116">See also</span></span>

- [<span data-ttu-id="6f090-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6f090-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="6f090-118">DacpGetModuleAdres yapısı</span><span class="sxs-lookup"><span data-stu-id="6f090-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
