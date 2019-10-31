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
ms.openlocfilehash: 3859752fd92a76f3fef1ceced0e792109b65106a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108286"
---
# <a name="fusion_install_reference-structure"></a>FUSION_INSTALL_REFERENCE Yapısı
Uygulamanın, uygulamanın genel derleme önbelleğinde yüklediği bir derlemeye yaptığı bir başvuruyu temsil eder.  
  
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
|`dwFlags`|Gelecekteki genişletilebilirlik için ayrılmıştır. Bu değer 0 (sıfır) olmalıdır.|  
|`guidScheme`|Başvuruyu ekleyen varlık. Bu alan aşağıdaki değerlerden birine sahip olabilir:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: derlemeye, Microsoft Windows Installer kullanılarak yüklenen bir uygulama tarafından başvuruluyor. `szIdentifier` alanı `MSI`olarak ayarlanır ve `szNonCanonicalData` alanı `Windows Installer`olarak ayarlanır. Bu düzen Windows yan yana derlemeler için kullanılır.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: derlemeye **Program Ekle/Kaldır** arabiriminde görünen bir uygulama tarafından başvuruluyor. `szIdentifier` alanı, uygulamayı **Program Ekle/Kaldır** arabirimiyle kaydeden belirteci sağlar.<br />-FUSION_REFCOUNT_FILEPATH_GUID: derlemeye dosya sistemindeki bir dosya tarafından temsil edilen bir uygulama tarafından başvuruluyor. `szIdentifier` alanı bu dosyanın yolunu sağlar.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: derlemeye yalnızca donuk bir dize tarafından temsil edilen bir uygulama tarafından başvuruluyor. `szIdentifier` alanı bu donuk dizeyi sağlar. Genel bütünleştirilmiş kod önbelleği, bu değeri kaldırdığınızda donuk başvuruların varlığını denetlemez.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Bu değer ayrılmıştır.|  
|`szIdentifier`|Derlemeyi genel derleme önbelleğine yükleyen uygulamayı tanımlayan benzersiz bir dize. Değeri `guidScheme` alanın değerine bağlıdır.|  
|`szNonCanonicalData`|Yalnızca başvuruyu ekleyen varlık tarafından anlaşılan bir dize. Genel bütünleştirilmiş kod önbelleği bu dizeyi depolar, ancak kullanmaz.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Yapıları](fusion-structures.md)
- [Genel Derleme Önbelleği](../../app-domains/gac.md)
