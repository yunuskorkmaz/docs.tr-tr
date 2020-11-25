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
ms.openlocfilehash: a845ecfde6583d625d2a8f165443344ff9e40d05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702558"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="f170c-102">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f170c-102">IMetaDataImport2 Interface</span></span>

<span data-ttu-id="f170c-103">, Genel türlerle çalışma yeteneği sağlamak için [IMetaDataImport](imetadataimport-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="f170c-103">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f170c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f170c-104">Methods</span></span>  
  
|<span data-ttu-id="f170c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f170c-105">Method</span></span>|<span data-ttu-id="f170c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f170c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f170c-107">EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-107">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="f170c-108">Belirtilen belirteçle temsil edilen genel parametreyle ilişkili genel parametre kısıtlamaları dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="f170c-109">EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-109">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="f170c-110">Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="f170c-111">EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-111">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="f170c-112">Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="f170c-113">GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-113">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="f170c-114">Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlamasıyla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="f170c-115">GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-115">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="f170c-116">Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="f170c-117">GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-117">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="f170c-118">Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="f170c-119">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-119">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="f170c-120">Geçerli meta veri kapsamında tanımlanan, genellikle bir DLL veya EXE dosyası olan Taşınabilir çalıştırılabilir (PE) dosyasındaki kodun yapısını tanımlayan bir değer alır</span><span class="sxs-lookup"><span data-stu-id="f170c-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="f170c-121">GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f170c-121">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="f170c-122">Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="f170c-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f170c-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f170c-123">Requirements</span></span>  

 <span data-ttu-id="f170c-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f170c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f170c-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f170c-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f170c-126">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f170c-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f170c-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f170c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f170c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f170c-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="f170c-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f170c-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="f170c-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f170c-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
