---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9b0f085820bac12638c0310ab23b2eafacb23b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186179"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="e53e2-102">CorSymSearchPolicyAttributes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e53e2-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="e53e2-103">Sembol Okuyucu için arama yaparken kullanılacak ilkeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e53e2-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="e53e2-104">Bu sabitler tarafından kullanılan [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) ve [Isymunmanagedbinder3::getreaderfromcallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e53e2-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e53e2-105">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e53e2-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53e2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e53e2-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="e53e2-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e53e2-107">Members</span></span>  
  
|<span data-ttu-id="e53e2-108">Üye</span><span class="sxs-lookup"><span data-stu-id="e53e2-108">Member</span></span>|<span data-ttu-id="e53e2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e53e2-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="e53e2-110">Simge arama yolu için kayıt defterini sorgular.</span><span class="sxs-lookup"><span data-stu-id="e53e2-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="e53e2-111">Bir sembol sunucusu erişir.</span><span class="sxs-lookup"><span data-stu-id="e53e2-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="e53e2-112">Hata ayıklama dizin için belirtilen yol arar.</span><span class="sxs-lookup"><span data-stu-id="e53e2-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="e53e2-113">PDB .exe dosyasının bulunduğu yerde arar.</span><span class="sxs-lookup"><span data-stu-id="e53e2-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e53e2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e53e2-114">Requirements</span></span>  
 <span data-ttu-id="e53e2-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e53e2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53e2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e53e2-116">See also</span></span>

- [<span data-ttu-id="e53e2-117">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e53e2-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
