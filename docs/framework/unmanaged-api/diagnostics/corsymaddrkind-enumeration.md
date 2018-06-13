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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98cf49714829b4b2f80e0240c2ebde7fa6c280e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425411"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="0bab1-102">CorSymAddrKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0bab1-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="0bab1-103">Bellek adresi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bab1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bab1-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0bab1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0bab1-105">Members</span></span>  
  
|<span data-ttu-id="0bab1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0bab1-106">Member</span></span>|<span data-ttu-id="0bab1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bab1-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="0bab1-108">Bir Microsoft Ara dili (MSIL) yerel değişken veya parametre dizinini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="0bab1-109">Göreli sanal adres bir modüle gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="0bab1-110">Bir CPU kayıt gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="0bab1-111">Bir kayıt ilk adresi olduğunu ve bir uzaklık ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="0bab1-112">Temel adres uzaklık gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="0bab1-113">İlk adres düşük bir kayıt bölümüdür ve yüksek bölümü ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="0bab1-114">İlk adres düşük bir kayıt bölümüdür, ikinci yüksek bölümüdür ve üçüncü bir uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="0bab1-115">Bir kayıt ilk adresidir, ikinci bir uzaklığı ve üçüncü kayıt yüksek bölümüdür gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="0bab1-116">İlk adres alanının başlangıç ve ikinci adresi alan uzunluğu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="0bab1-117">İlk adres bölümdür ve bir uzaklık ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bab1-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bab1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bab1-118">Requirements</span></span>  
 <span data-ttu-id="0bab1-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0bab1-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bab1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bab1-120">See Also</span></span>  
 [<span data-ttu-id="0bab1-121">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0bab1-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
