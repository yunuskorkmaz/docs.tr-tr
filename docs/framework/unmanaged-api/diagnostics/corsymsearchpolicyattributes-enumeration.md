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
ms.openlocfilehash: 29766636cd151744d25cf66deb60cd2e066e1b32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775787"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="550ac-102">CorSymSearchPolicyAttributes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="550ac-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="550ac-103">Sembol Okuyucu için arama yaparken kullanılacak ilkeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="550ac-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="550ac-104">Bu sabitler tarafından kullanılan [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) ve [Isymunmanagedbinder3::getreaderfromcallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="550ac-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="550ac-105">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="550ac-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="550ac-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="550ac-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="550ac-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="550ac-107">Members</span></span>  
  
|<span data-ttu-id="550ac-108">Üye</span><span class="sxs-lookup"><span data-stu-id="550ac-108">Member</span></span>|<span data-ttu-id="550ac-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="550ac-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="550ac-110">Simge arama yolu için kayıt defterini sorgular.</span><span class="sxs-lookup"><span data-stu-id="550ac-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="550ac-111">Bir sembol sunucusu erişir.</span><span class="sxs-lookup"><span data-stu-id="550ac-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="550ac-112">Hata ayıklama dizin için belirtilen yol arar.</span><span class="sxs-lookup"><span data-stu-id="550ac-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="550ac-113">PDB .exe dosyasının bulunduğu yerde arar.</span><span class="sxs-lookup"><span data-stu-id="550ac-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="550ac-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="550ac-114">Requirements</span></span>  
 <span data-ttu-id="550ac-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="550ac-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550ac-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="550ac-116">See also</span></span>

- [<span data-ttu-id="550ac-117">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="550ac-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
