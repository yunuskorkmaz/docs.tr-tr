---
title: ASSEMBLY_INFO Yapısı
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110883"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO Yapısı
Genel derleme önbelleğinde kayıtlı bir derlemeyle ilgili bilgiler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`cbAssemblyInfo`|Yapının bayt cinsinden boyutu. Bu alan sonra genişletilebilmek için ayrılmış.|  
|`dwAssemblyFlags`|Derlemeyle ilgili yükleme ayrıntılarını gösteren bayrak. Aşağıdaki değerleri desteklenir:<br /><br /> -Derleme yüklü olduğunu gösterecek ASSEMBLYINFO_FLAG_INSTALLED değeri. Her zaman geçerli sürümü .NET Framework'ün ayarlar `dwAssemblyFlags` şu değer.<br />-Yerleşik bir yükü derleme gösterir ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri. Hiçbir zaman geçerli sürümü .NET Framework'ün ayarlar `dwAssemblyFlags` şu değer.|  
|`uliAssemblySizeInKB`|İçeren derleme dosyalarının kilobayt cinsinden toplam boyutu.|  
|`pszCurrentAssemblyPathBuf`|Bildirim dosyası için geçerli yol tutan dize arabellek için işaretçi. Yol, bir null karakterle bitmelidir.|  
|`cchBuf`|Null sonlandırıcıyı da dahil olmak üzere geniş karakter sayısı, `pszCurrentAssemblyPathBuf` içerir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)
