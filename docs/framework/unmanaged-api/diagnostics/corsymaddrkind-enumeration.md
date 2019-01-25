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
ms.openlocfilehash: 389cf2e77728002ce1078f63df3d741d1847c105
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744979"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="62058-102">CorSymAddrKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="62058-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="62058-103">Bellek adresi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="62058-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62058-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62058-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="62058-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="62058-105">Members</span></span>  
  
|<span data-ttu-id="62058-106">Üye</span><span class="sxs-lookup"><span data-stu-id="62058-106">Member</span></span>|<span data-ttu-id="62058-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62058-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="62058-108">Bir Microsoft Ara dili (MSIL) yerel değişken veya parametre dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62058-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="62058-109">Bir göreli sanal adres, bir modül olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="62058-110">Bir CPU kaydı gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="62058-111">Bir kayıt ilk adresidir ve bir uzaklık ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="62058-112">Temel adres bir uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="62058-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="62058-113">İlk adres bir kayıt düşük bölümüdür ve yüksek bölümü ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="62058-114">İlk adres bir kayıt düşük bölümüdür, ikinci yüksek bölümüdür ve üçüncü bir uzaklık olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="62058-115">Bir kayıt ilk adresidir, ikincisi ise bir uzaklık ve üçüncü kayıt yüksek bölümüdür gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="62058-116">İlk adres alanının başlangıç ve ikinci adresini alan uzunluğu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="62058-117">İlk adres bölümdür ve bir uzaklık ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="62058-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62058-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62058-118">Requirements</span></span>  
 <span data-ttu-id="62058-119">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="62058-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62058-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62058-120">See also</span></span>
- [<span data-ttu-id="62058-121">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="62058-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
