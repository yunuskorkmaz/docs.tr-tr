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
ms.openlocfilehash: 7188c516d3d0a5192251697ec743e9d41f8d9072
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913737"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="65b0f-102">CorSymSearchPolicyAttributes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="65b0f-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="65b0f-103">Sembol okuyucu ararken kullanılacak ilkeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="65b0f-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="65b0f-104">Bu sabitler, [ISymUnmanagedBinder2:: GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) ve [ISymUnmanagedBinder3:: GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65b0f-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65b0f-105">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="65b0f-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b0f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65b0f-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="65b0f-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="65b0f-107">Members</span></span>  
  
|<span data-ttu-id="65b0f-108">Üye</span><span class="sxs-lookup"><span data-stu-id="65b0f-108">Member</span></span>|<span data-ttu-id="65b0f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65b0f-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="65b0f-110">Sembol arama yolları için kayıt defterini sorgular.</span><span class="sxs-lookup"><span data-stu-id="65b0f-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="65b0f-111">Bir sembol sunucusuna erişir.</span><span class="sxs-lookup"><span data-stu-id="65b0f-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="65b0f-112">Hata ayıklama dizininde belirtilen yolu arar.</span><span class="sxs-lookup"><span data-stu-id="65b0f-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="65b0f-113">PDB 'yi. exe dosyasının olduğu yerde arar.</span><span class="sxs-lookup"><span data-stu-id="65b0f-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65b0f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65b0f-114">Requirements</span></span>  
 <span data-ttu-id="65b0f-115">**Üst bilgi** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="65b0f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b0f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65b0f-116">See also</span></span>

- [<span data-ttu-id="65b0f-117">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="65b0f-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
