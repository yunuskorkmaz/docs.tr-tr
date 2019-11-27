---
title: CorSymAddrKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 12f31d0bf224e38418818122dad3586ec687b2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448583"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="7ff15-102">CorSymAddrKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7ff15-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="7ff15-103">Bellek adresi türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ff15-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="7ff15-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="7ff15-105">Members</span></span>  
  
|<span data-ttu-id="7ff15-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="7ff15-106">Member</span></span>|<span data-ttu-id="7ff15-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ff15-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="7ff15-108">Bir Microsoft ara dili (MSIL) yerel değişkenini veya parametre dizinini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="7ff15-109">Bir modülün göreli bir sanal adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="7ff15-110">Bir CPU kaydını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="7ff15-111">İlk adresin bir kayıt olduğunu ve ikinci adresin bir konum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="7ff15-112">Temel adresten bir konum gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="7ff15-113">İlk adresin kaydın alt kısmı olduğunu ve ikinci adresin ise yüksek bir kısmını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="7ff15-114">İlk adresin bir kaydın alt kısmı olduğunu, ikincinin Yüksek kısmını ve üçüncüsü de bir konum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="7ff15-115">İlk adresin bir yazmaç olduğunu, ikincinin bir konum olduğunu ve üçüncü öğenin, kaydın yüksek kısmıdır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="7ff15-116">İlk adresin bir alanın başlangıcı olduğunu ve ikinci adresin alan uzunluğu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="7ff15-117">İlk adresin bölüm olduğunu ve ikinci adresin bir konum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff15-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ff15-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff15-118">Requirements</span></span>  
 <span data-ttu-id="7ff15-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7ff15-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff15-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff15-120">See also</span></span>

- [<span data-ttu-id="7ff15-121">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7ff15-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
