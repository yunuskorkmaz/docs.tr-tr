---
title: IMetaDataImport2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1b00879f1d22d49e5f0dc3bdb072e0545feda68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="be64e-102">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be64e-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="be64e-103">Genişletir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi genel türleri ile çalışma özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="be64e-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be64e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="be64e-104">Methods</span></span>  
  
|<span data-ttu-id="be64e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="be64e-105">Method</span></span>|<span data-ttu-id="be64e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be64e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be64e-107">EnumGenericParamConstraints yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="be64e-108">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili genel parametresi kısıtlamaları dizisi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="be64e-109">EnumGenericParams yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="be64e-110">Bir numaralandırıcı genel parametresini belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="be64e-111">EnumMethodSpecs yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="be64e-112">Bir numaralandırıcı MethodSpec belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="be64e-113">GetGenericParamConstraintProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="be64e-114">Belirtilen kısıtlama belirtecin tarafından temsil edilen genel parametresini kısıtlaması ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="be64e-115">GetGenericParamProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="be64e-116">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="be64e-117">GetMethodSpecProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="be64e-118">Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="be64e-119">GetPEKind yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="be64e-120">Alır taşınabilir yürütülebilir (PE) kodda yapısını tanımlayan bir değer, geçerli meta veri kapsamda tanımlı genellikle bir DLL veya EXE dosyası dosyasında,</span><span class="sxs-lookup"><span data-stu-id="be64e-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="be64e-121">GetVersionString yöntemi</span><span class="sxs-lookup"><span data-stu-id="be64e-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="be64e-122">Derleme oluşturma için kullanılan çalışma zamanı sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="be64e-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be64e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be64e-123">Requirements</span></span>  
 <span data-ttu-id="be64e-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be64e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be64e-125">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be64e-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be64e-126">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="be64e-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be64e-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be64e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be64e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be64e-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="be64e-129">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be64e-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="be64e-130">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="be64e-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
