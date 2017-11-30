---
title: "CorSymAddrKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56bb55d9c9f85ae8f8112f16dcf552295699826d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="dcd6c-102">CorSymAddrKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dcd6c-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="dcd6c-103">Bellek adresi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcd6c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dcd6c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dcd6c-105">Members</span></span>  
  
|<span data-ttu-id="dcd6c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="dcd6c-106">Member</span></span>|<span data-ttu-id="dcd6c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcd6c-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="dcd6c-108">Bir Microsoft Ara dili (MSIL) yerel değişken veya parametre dizinini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="dcd6c-109">Göreli sanal adres bir modüle gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="dcd6c-110">Bir CPU kayıt gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="dcd6c-111">Bir kayıt ilk adresi olduğunu ve bir uzaklık ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="dcd6c-112">Temel adres uzaklık gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="dcd6c-113">İlk adres düşük bir kayıt bölümüdür ve yüksek bölümü ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="dcd6c-114">İlk adres düşük bir kayıt bölümüdür, ikinci yüksek bölümüdür ve üçüncü bir uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="dcd6c-115">Bir kayıt ilk adresidir, ikinci bir uzaklığı ve üçüncü kayıt yüksek bölümüdür gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="dcd6c-116">İlk adres alanının başlangıç ve ikinci adresi alan uzunluğu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="dcd6c-117">İlk adres bölümdür ve bir uzaklık ikinci adresidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcd6c-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcd6c-118">Requirements</span></span>  
 <span data-ttu-id="dcd6c-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dcd6c-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd6c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dcd6c-120">See Also</span></span>  
 [<span data-ttu-id="dcd6c-121">Tanılama sembol deposu numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="dcd6c-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
