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
ms.openlocfilehash: 7318a7ea3eb1ddb047a799e58ebdfd9ce6cd76d1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007591"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags Numaralandırması
Bildirim dosyalarını açtıktan sonra meta veri davranışını denetleyen bayrak değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`ofRead`|Dosyanın yalnızca okuma için açılması gerektiğini gösterir.|  
|`ofWrite`|Dosyanın yazma için açılması gerektiğini gösterir.<br /><br /> `ofWrite`Bir. winmd dosyasını açarken bayrak kullanıyorsanız, bayrağını da geçirmeniz gerekir `ofNoTransform` .|  
|`ofReadWriteMask`|Okuma ve yazma için bir maske.|  
|`ofCopyMemory`|Dosyanın belleğe okunup okunmayacağını belirtir. Meta veriler kendi kopyasını korumalıdır.|  
|`ofCacheImage`|Kullanımdan kalktı. Bu bayrak yoksayıldı.|  
|`ofManifestMetadata`|Kullanımdan kalktı. Bu bayrak yoksayıldı.|  
|`ofReadOnly`|Dosyanın okuma için açılması gerektiğini ve bir `QueryInterface` [ımetadatayayın](imetadataemit-interface.md) çağrısı yapılamıyor olduğunu gösterir.|  
|`ofTakeOwnership`|Belleğin [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) çağrısı kullanılarak ayrıldığını belirtir ve meta veriler tarafından serbest bırakılır.|  
|`ofNoTypeLib`|Kullanımdan kalktı. Bu bayrak yoksayıldı.|  
|`ofNoTransform`|. Winmd dosyalarının otomatik dönüştürmesinin devre dışı bırakılacağını belirtir. Diğer bir deyişle, bir Windows Çalışma Zamanı türünün .NET Framework türüne projeksiyonu devre dışı bırakılmalıdır. Daha fazla bilgi için bkz. [.net ve Windows çalışma zamanı ile birlikte Windows çalışma zamanı ve clr](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).|  
|`ofReserved1`|Dahili kullanım için ayrılmıştır.|  
|`ofReserved2`|Dahili kullanım için ayrılmıştır.|  
|`ofReserved`|Dahili kullanım için ayrılmıştır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
