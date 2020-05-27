---
title: CorGenericParamAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: ea84b742c901ba58a3bb730f1f5033a0d90610ce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007383"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="75807-102">CorGenericParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="75807-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="75807-103"><xref:System.Type> [Imetadataemit2::D efineGenericParam](imetadataemit2-definegenericparam-method.md)çağrılarında kullanılan genel türlerin parametrelerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="75807-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75807-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75807-104">Syntax</span></span>  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="75807-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="75807-105">Members</span></span>  
  
|<span data-ttu-id="75807-106">Üye</span><span class="sxs-lookup"><span data-stu-id="75807-106">Member</span></span>|<span data-ttu-id="75807-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75807-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="75807-108">Parametre varyansı yalnızca arabirimler ve temsilciler için genel parametreler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="75807-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="75807-109">Varyans yokluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="75807-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="75807-110">Kovaryansı gösterir.</span><span class="sxs-lookup"><span data-stu-id="75807-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="75807-111">Değişken varyansı gösterir.</span><span class="sxs-lookup"><span data-stu-id="75807-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="75807-112">Özel kısıtlamalar, herhangi bir <xref:System.Type> parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="75807-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="75807-113">Parametreye hiçbir kısıtlama uygulanacağını gösterir <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="75807-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="75807-114"><xref:System.Type>Parametrenin bir başvuru türü olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75807-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="75807-115"><xref:System.Type>Parametrenin null değer olmayan bir değer türü olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75807-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="75807-116"><xref:System.Type>Parametresinin parametre alan bir varsayılan genel oluşturucuya sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75807-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75807-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75807-117">Requirements</span></span>  
 <span data-ttu-id="75807-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75807-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75807-119">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="75807-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="75807-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75807-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75807-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75807-121">See also</span></span>

- [<span data-ttu-id="75807-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="75807-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
