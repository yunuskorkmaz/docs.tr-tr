---
title: FUSION_INSTALL_REFERENCE Yapısı
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec18d5d5a6574cb0e08a6c4d6eaedcbcbf6886cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759367"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE Yapısı
Uygulama genel derleme önbelleğinde yüklü olduğu bir derlemeye bir uygulama sağlar. bir başvuruyu temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`cbSize`|Yapının bayt cinsinden boyutu.|  
|`dwFlags`|Sonra genişletilebilmek için ayrılmış. Bu değer, 0 (sıfır) olmalıdır.|  
|`guidScheme`|Varlık başvurusu ekler. Bu alan şu değerlerden biri olabilir:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: Derleme, Microsoft Windows Installer kullanarak yüklenen bir uygulama tarafından başvuruluyor. `szIdentifier` Ayarlanmış `MSI`ve `szNonCanonicalData` ayarlanmış `Windows Installer`. Bu düzen, Windows yan yana derlemeler için kullanılır.<br />-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Derlemenin görünen bir uygulama tarafından başvurulan **Program Ekle/Kaldır** arabirimi. `szIdentifier` Alan uygulamayla kayıtlarını belirteci sağlar **Program Ekle/Kaldır** arabirimi.<br />-   FUSION_REFCOUNT_FILEPATH_GUID: Derleme, dosya sisteminde dosya tarafından temsil edilen bir uygulama tarafından başvuruluyor. `szIdentifier` Alanı, bu dosyanın yolunu sağlar.<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Derleme, yalnızca genel olmayan bir dize tarafından temsil edilen bir uygulama tarafından başvuruluyor. `szIdentifier` Alanı donuk Bu dize sağlar. Bu değer kaldırdığınızda, Genel Derleme Önbelleği donuk başvuruları varlığını denetlemez.<br />-   FUSION_REFCOUNT_OSINSTALL_GUID: Bu değer ayrılmış.|  
|`szIdentifier`|Derleme genel derleme önbelleğinde yüklü uygulama tanımlayan benzersiz bir dize. Değerin değerine bağlıdır `guidScheme` alan.|  
|`szNonCanonicalData`|Yalnızca başvuru ekler varlık tarafından anlaşılan bir dize. Genel Derleme Önbelleği, bu dizesi depolar, ancak bunları kullanmaz.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)
