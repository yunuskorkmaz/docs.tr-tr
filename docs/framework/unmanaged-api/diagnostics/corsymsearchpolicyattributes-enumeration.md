---
description: 'Daha fazla bilgi edinin: CorSymSearchPolicyAttributes numaralandırması'
title: CorSymSearchPolicyAttributes Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: a9af0e96809ec8eba5c03c2e372e818c74914baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800480"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="f9862-103">CorSymSearchPolicyAttributes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f9862-103">CorSymSearchPolicyAttributes Enumeration</span></span>

<span data-ttu-id="f9862-104">Sembol okuyucu ararken kullanılacak ilkeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9862-104">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="f9862-105">Bu sabitler, [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) ve [ISymUnmanagedBinder3:: GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9862-105">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f9862-106">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="f9862-106">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9862-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9862-107">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="f9862-108">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f9862-108">Members</span></span>  
  
|<span data-ttu-id="f9862-109">Üye</span><span class="sxs-lookup"><span data-stu-id="f9862-109">Member</span></span>|<span data-ttu-id="f9862-110">Description</span><span class="sxs-lookup"><span data-stu-id="f9862-110">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="f9862-111">Sembol arama yolları için kayıt defterini sorgular.</span><span class="sxs-lookup"><span data-stu-id="f9862-111">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="f9862-112">Bir sembol sunucusuna erişir.</span><span class="sxs-lookup"><span data-stu-id="f9862-112">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="f9862-113">Hata ayıklama dizininde belirtilen yolu arar.</span><span class="sxs-lookup"><span data-stu-id="f9862-113">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="f9862-114">PDB 'yi. exe dosyasının olduğu yerde arar.</span><span class="sxs-lookup"><span data-stu-id="f9862-114">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9862-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9862-115">Requirements</span></span>  

 <span data-ttu-id="f9862-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f9862-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9862-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9862-117">See also</span></span>

- [<span data-ttu-id="f9862-118">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f9862-118">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
