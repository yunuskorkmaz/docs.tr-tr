---
title: IMetaDataImport2 Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211939"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="245c9-102">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="245c9-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="245c9-103">Genişletir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) genel türleri ile çalışmaktan yeteneği sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="245c9-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="245c9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="245c9-104">Methods</span></span>  
  
|<span data-ttu-id="245c9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="245c9-105">Method</span></span>|<span data-ttu-id="245c9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="245c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="245c9-107">EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="245c9-108">Genel parametre kısıtlama belirtilen belirteci tarafından temsil edilen genel parametre ile ilişkili bir dizi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="245c9-109">EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="245c9-110">Bir numaralandırıcı genel parametre belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizisi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="245c9-111">EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="245c9-112">Bir numaralandırıcı MethodSpec Neobsahuje belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizisi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="245c9-113">GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="245c9-114">Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlama ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="245c9-115">GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="245c9-116">Belirtilen belirteç tarafından temsil edilen genel parametre ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="245c9-117">GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="245c9-118">Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="245c9-119">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="245c9-120">Alır bir taşınabilir yürütülebilir (PE) kod yapısını tanımlayan bir değer dosya, geçerli meta veri kapsamda tanımlanan genellikle bir DLL veya EXE dosyası</span><span class="sxs-lookup"><span data-stu-id="245c9-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="245c9-121">GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="245c9-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="245c9-122">Derlemesi oluşturmak için kullanılan çalışma zamanı sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="245c9-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="245c9-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="245c9-123">Requirements</span></span>  
 <span data-ttu-id="245c9-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="245c9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="245c9-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="245c9-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="245c9-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="245c9-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="245c9-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="245c9-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="245c9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="245c9-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="245c9-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="245c9-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="245c9-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="245c9-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
