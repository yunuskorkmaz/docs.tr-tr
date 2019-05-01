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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986511"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes Numaralandırması
Sembol Okuyucu için arama yaparken kullanılacak ilkeyi belirtir. Bu sabitler tarafından kullanılan [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) ve [Isymunmanagedbinder3::getreaderfromcallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri.  
  
> [!IMPORTANT]
>  Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`AllowRegistryAccess`|Simge arama yolu için kayıt defterini sorgular.|  
|`AllowSymbolServerAccess`|Bir sembol sunucusu erişir.|  
|`AllowOriginalPathAccess`|Hata ayıklama dizin için belirtilen yol arar.|  
|`AllowReferencePathAccess`|PDB .exe dosyasının bulunduğu yerde arar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Sabit Listeleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
