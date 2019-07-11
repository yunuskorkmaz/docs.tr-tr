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
ms.openlocfilehash: 981829500e499be05a8de7c1ffb4683429a903e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781858"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="cf11c-102">CorGenericParamAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cf11c-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="cf11c-103">Açıklayan değerleri içeren <xref:System.Type> kullanılan çağrıları olarak genel türler için parametreleri [Imetadataemit2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="cf11c-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf11c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf11c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cf11c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cf11c-105">Members</span></span>  
  
|<span data-ttu-id="cf11c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cf11c-106">Member</span></span>|<span data-ttu-id="cf11c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf11c-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="cf11c-108">Parametre değişikliklerinin yalnızca arabirimlerde ve temsilcilerde genel parametreleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cf11c-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="cf11c-109">Fark olmaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf11c-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="cf11c-110">Birlikte değişkenlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf11c-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="cf11c-111">Kontravaryans gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf11c-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="cf11c-112">Özel kısıtlamalar için uygulayabileceğiniz <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="cf11c-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="cf11c-113">Hiçbir kısıtlaması için geçerli olduğunu gösterir <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="cf11c-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="cf11c-114">Bildiren <xref:System.Type> parametresi, bir başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf11c-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="cf11c-115">Bildiren <xref:System.Type> parametre bir null değer olamaz bir değer türü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf11c-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="cf11c-116">Bildiren <xref:System.Type> parametresi, parametre almayan varsayılan bir public Oluşturucu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf11c-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf11c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf11c-117">Requirements</span></span>  
 <span data-ttu-id="cf11c-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf11c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf11c-119">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cf11c-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cf11c-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf11c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf11c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf11c-121">See also</span></span>

- [<span data-ttu-id="cf11c-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cf11c-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
