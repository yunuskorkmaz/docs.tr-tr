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
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes Numaralandırması

Sembol okuyucu ararken kullanılacak ilkeyi belirtir. Bu sabitler, [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) ve [ISymUnmanagedBinder3:: GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) yöntemleri tarafından kullanılır.  
  
> [!IMPORTANT]
> Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`AllowRegistryAccess`|Sembol arama yolları için kayıt defterini sorgular.|  
|`AllowSymbolServerAccess`|Bir sembol sunucusuna erişir.|  
|`AllowOriginalPathAccess`|Hata ayıklama dizininde belirtilen yolu arar.|  
|`AllowReferencePathAccess`|PDB 'yi. exe dosyasının olduğu yerde arar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Numaralandırmaları](diagnostics-symbol-store-enumerations.md)
