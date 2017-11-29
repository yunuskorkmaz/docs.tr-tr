---
title: "CorSymSearchPolicyAttributes Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymSearchPolicyAttributes
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymSearchPolicyAttributes
helpviewer_keywords: CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 016378de8d4ba4b6f16f7e7b91b6427f73c9687d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="88bfd-102">CorSymSearchPolicyAttributes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="88bfd-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="88bfd-103">Bir simge Okuyucu için arama yaparken kullanılacak ilkeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="88bfd-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="88bfd-104">Bu sabitler tarafından kullanılan [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) ve [Isymunmanagedbinder3::getreaderfromcallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="88bfd-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="88bfd-105">Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyasını açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88bfd-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88bfd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88bfd-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="88bfd-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="88bfd-107">Members</span></span>  
  
|<span data-ttu-id="88bfd-108">Üye</span><span class="sxs-lookup"><span data-stu-id="88bfd-108">Member</span></span>|<span data-ttu-id="88bfd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88bfd-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="88bfd-110">Sembol arama yolları için kayıt defterini sorgular.</span><span class="sxs-lookup"><span data-stu-id="88bfd-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="88bfd-111">Bir simge sunucusunu erişir.</span><span class="sxs-lookup"><span data-stu-id="88bfd-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="88bfd-112">Hata ayıklama dizininde belirtilen yolu arar.</span><span class="sxs-lookup"><span data-stu-id="88bfd-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="88bfd-113">PDB .exe dosyası olduğu yerde arar.</span><span class="sxs-lookup"><span data-stu-id="88bfd-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88bfd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88bfd-114">Requirements</span></span>  
 <span data-ttu-id="88bfd-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="88bfd-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bfd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88bfd-116">See Also</span></span>  
 [<span data-ttu-id="88bfd-117">Tanılama sembol deposu numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="88bfd-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
