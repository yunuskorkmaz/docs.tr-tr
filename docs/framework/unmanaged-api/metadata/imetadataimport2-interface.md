---
description: 'Daha fazla bilgi edinin: IMetaDataImport2 Interface'
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
ms.openlocfilehash: de1b190ae174c6028e4f116d7f6fc0b9af0aac6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688552"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="5c7d9-103">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-103">IMetaDataImport2 Interface</span></span>

<span data-ttu-id="5c7d9-104">, Genel türlerle çalışma yeteneği sağlamak için [IMetaDataImport](imetadataimport-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-104">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c7d9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c7d9-105">Methods</span></span>  
  
|<span data-ttu-id="5c7d9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5c7d9-106">Method</span></span>|<span data-ttu-id="5c7d9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c7d9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c7d9-108">EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-108">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="5c7d9-109">Belirtilen belirteçle temsil edilen genel parametreyle ilişkili genel parametre kısıtlamaları dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-109">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="5c7d9-110">EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-110">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="5c7d9-111">Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-111">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="5c7d9-112">EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-112">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="5c7d9-113">Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-113">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="5c7d9-114">GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-114">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="5c7d9-115">Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlamasıyla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-115">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="5c7d9-116">GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-116">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="5c7d9-117">Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-117">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="5c7d9-118">GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-118">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="5c7d9-119">Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-119">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="5c7d9-120">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-120">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="5c7d9-121">Geçerli meta veri kapsamında tanımlanan, genellikle bir DLL veya EXE dosyası olan Taşınabilir çalıştırılabilir (PE) dosyasındaki kodun yapısını tanımlayan bir değer alır</span><span class="sxs-lookup"><span data-stu-id="5c7d9-121">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="5c7d9-122">GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-122">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="5c7d9-123">Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-123">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c7d9-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c7d9-124">Requirements</span></span>  

 <span data-ttu-id="5c7d9-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c7d9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7d9-126">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5c7d9-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c7d9-127">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5c7d9-127">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c7d9-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7d9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7d9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c7d9-129">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="5c7d9-130">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c7d9-130">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="5c7d9-131">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c7d9-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
