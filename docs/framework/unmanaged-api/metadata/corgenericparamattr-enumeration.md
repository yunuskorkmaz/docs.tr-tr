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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf73f382c1da15e0285ee95be9e8bce39575ae0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557372"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="e5df7-102">CorGenericParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e5df7-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="e5df7-103">Açıklayan değerleri içeren <xref:System.Type> kullanılan çağrıları olarak genel türler için parametreleri [Imetadataemit2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5df7-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5df7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5df7-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="e5df7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e5df7-105">Members</span></span>  
  
|<span data-ttu-id="e5df7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e5df7-106">Member</span></span>|<span data-ttu-id="e5df7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5df7-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="e5df7-108">Parametre değişikliklerinin yalnızca arabirimlerde ve temsilcilerde genel parametreleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e5df7-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="e5df7-109">Fark olmaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5df7-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="e5df7-110">Birlikte değişkenlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5df7-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="e5df7-111">Kontravaryans gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5df7-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="e5df7-112">Özel kısıtlamalar için uygulayabileceğiniz <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="e5df7-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="e5df7-113">Hiçbir kısıtlaması için geçerli olduğunu gösterir <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="e5df7-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="e5df7-114">Bildiren <xref:System.Type> parametresi, bir başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5df7-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="e5df7-115">Bildiren <xref:System.Type> parametre bir null değer olamaz bir değer türü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5df7-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="e5df7-116">Bildiren <xref:System.Type> parametresi, parametre almayan varsayılan bir public Oluşturucu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5df7-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5df7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5df7-117">Requirements</span></span>  
 <span data-ttu-id="e5df7-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5df7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5df7-119">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e5df7-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e5df7-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5df7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5df7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5df7-121">See also</span></span>
- [<span data-ttu-id="e5df7-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e5df7-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
