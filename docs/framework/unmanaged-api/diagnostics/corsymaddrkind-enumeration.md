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
ms.openlocfilehash: 5991b0abaedabe2337cd754c7bd19f96c5e9b685
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420623"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="29a36-102">CorSymAddrKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="29a36-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="29a36-103">Bellek adresi türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a36-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="29a36-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="29a36-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="29a36-105">Members</span></span>  
  
|<span data-ttu-id="29a36-106">Üye</span><span class="sxs-lookup"><span data-stu-id="29a36-106">Member</span></span>|<span data-ttu-id="29a36-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29a36-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="29a36-108">Bir Microsoft ara dili (MSIL) yerel değişkenini veya parametre dizinini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="29a36-109">Bir modülün göreli bir sanal adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="29a36-110">Bir CPU kaydını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="29a36-111">İlk adresin bir kayıt olduğunu ve ikinci adresin bir konum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="29a36-112">Temel adresten bir konum gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="29a36-113">İlk adresin kaydın alt kısmı olduğunu ve ikinci adresin ise yüksek bir kısmını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="29a36-114">İlk adresin bir kaydın alt kısmı olduğunu, ikincinin Yüksek kısmını ve üçüncüsü de bir konum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="29a36-115">İlk adresin bir yazmaç olduğunu, ikincinin bir konum olduğunu ve üçüncü öğenin, kaydın yüksek kısmıdır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="29a36-116">İlk adresin bir alanın başlangıcı olduğunu ve ikinci adresin alan uzunluğu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="29a36-117">İlk adresin bölüm olduğunu ve ikinci adresin bir konum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29a36-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29a36-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29a36-118">Requirements</span></span>  
 <span data-ttu-id="29a36-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="29a36-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a36-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29a36-120">See also</span></span>

- [<span data-ttu-id="29a36-121">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="29a36-121">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
