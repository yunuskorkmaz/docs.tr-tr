---
title: IXCLRDataMethodInstance Arabirimi
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0b1c982b25af9edea76a038b4314b4bd608f07df
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420896"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="66092-102">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66092-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="66092-103">Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="66092-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="66092-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="66092-104">Methods</span></span>

| <span data-ttu-id="66092-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="66092-105">Method</span></span>                                                                                                                  | <span data-ttu-id="66092-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66092-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="66092-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="66092-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="66092-108">Eşleme bilgilerini ele almak için Il 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="66092-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="66092-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="66092-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="66092-110">Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır.</span><span class="sxs-lookup"><span data-stu-id="66092-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="66092-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66092-111">Remarks</span></span>

<span data-ttu-id="66092-112">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="66092-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="66092-113">Ancak, `IUnknown` `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="66092-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="66092-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66092-114">Requirements</span></span>

<span data-ttu-id="66092-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66092-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="66092-116">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="66092-116">**Header:** None</span></span>  
<span data-ttu-id="66092-117">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="66092-117">**Library:** None</span></span>  
<span data-ttu-id="66092-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66092-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="66092-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66092-119">See also</span></span>

- [<span data-ttu-id="66092-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="66092-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="66092-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="66092-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
