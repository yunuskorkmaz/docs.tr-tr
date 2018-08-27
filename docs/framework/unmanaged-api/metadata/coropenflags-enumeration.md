---
title: CorOpenFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa9e7a4dacceb492dfe037b4b64f22f231323de5
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933228"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags Numaralandırması
Bildirim dosyaları açma bağlı meta veri davranışını denetleyen bayrak değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ofRead`|Yalnızca okumak için dosyanın açılması gerektiğini gösterir.|  
|`ofWrite`|Dosya yazma için açılması gerektiğini gösterir.<br /><br /> Kullanıyorsanız `ofWrite` ne zaman bayrağı da geçmesi bir .winmd dosyası açılırken, `ofNoTransform` bayrağı.|  
|`ofReadWriteMask`|Okuma ve yazma için bir maske.|  
|`ofCopyMemory`|Dosya belleğe okunmalıdır gösterir. Meta verileri kendi kopyalama korumanız gerekir.|  
|`ofCacheImage`|Kullanımdan kalktı. Bu bayrak göz ardı edilir.|  
|`ofManifestMetadata`|Kullanımdan kalktı. Bu bayrak göz ardı edilir.|  
|`ofReadOnly`|Okuma ve bu dosyanın açılması gerektiğini belirten bir çağrı `QueryInterface` için bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yapılamaz.|  
|`ofTakeOwnership`|Bellek yapılan bir çağrı kullanılarak ayrıldı gösterir [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) ve meta verileri tarafından serbest bırakılacak.|  
|`ofNoTypeLib`|Kullanımdan kalktı. Bu bayrak göz ardı edilir.|  
|`ofNoTransform`|Otomatik dönüştürmeler .winmd dosyaları devre dışı olduğunu gösterir. Diğer bir deyişle, bir .NET Framework türü için bir Windows çalışma zamanı tür projeksiyonu devre dışı bırakılmalıdır. Daha fazla bilgi için [altındaki Seçenekler .NET ve Windows çalışma zamanı ile](http://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|İç kullanım için ayrılmıştır.|  
|`ofReserved2`|İç kullanım için ayrılmıştır.|  
|`ofReserved`|İç kullanım için ayrılmıştır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
