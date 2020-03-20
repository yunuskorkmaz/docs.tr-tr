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
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178342"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="73159-102">CorSymSearchPolicyAttributes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="73159-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="73159-103">Sembol okuyucu için arama yaparken kullanılacak ilkeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="73159-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="73159-104">Bu sabitler [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) ve [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73159-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73159-105">Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="73159-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73159-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73159-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="73159-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="73159-107">Members</span></span>  
  
|<span data-ttu-id="73159-108">Üye</span><span class="sxs-lookup"><span data-stu-id="73159-108">Member</span></span>|<span data-ttu-id="73159-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73159-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="73159-110">Simge arama yolları için kayıt defterini sorgular.</span><span class="sxs-lookup"><span data-stu-id="73159-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="73159-111">Bir sembol sunucusuna erişir.</span><span class="sxs-lookup"><span data-stu-id="73159-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="73159-112">Hata Ayıklama dizininde belirtilen yolu arar.</span><span class="sxs-lookup"><span data-stu-id="73159-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="73159-113">.exe dosyasının bulunduğu yerde PDB'yi arar.</span><span class="sxs-lookup"><span data-stu-id="73159-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73159-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73159-114">Requirements</span></span>  
 <span data-ttu-id="73159-115">**Üstbilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="73159-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73159-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73159-116">See also</span></span>

- [<span data-ttu-id="73159-117">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="73159-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
