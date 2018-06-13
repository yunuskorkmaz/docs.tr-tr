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
ms.openlocfilehash: 1328e40c74c17c55cc476bba761c1c3be9af034e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449344"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="8dd9a-102">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="8dd9a-103">Genişletir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi genel türleri ile çalışma özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8dd9a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8dd9a-104">Methods</span></span>  
  
|<span data-ttu-id="8dd9a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8dd9a-105">Method</span></span>|<span data-ttu-id="8dd9a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dd9a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8dd9a-107">EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="8dd9a-108">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili genel parametresi kısıtlamaları dizisi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="8dd9a-109">EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="8dd9a-110">Bir numaralandırıcı genel parametresini belirteçleri belirtilen TypeDef veya MethodDef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="8dd9a-111">EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="8dd9a-112">Bir numaralandırıcı MethodSpec belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="8dd9a-113">GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="8dd9a-114">Belirtilen kısıtlama belirtecin tarafından temsil edilen genel parametresini kısıtlaması ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="8dd9a-115">GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="8dd9a-116">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="8dd9a-117">GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="8dd9a-118">Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="8dd9a-119">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="8dd9a-120">Alır taşınabilir yürütülebilir (PE) kodda yapısını tanımlayan bir değer, geçerli meta veri kapsamda tanımlı genellikle bir DLL veya EXE dosyası dosyasında,</span><span class="sxs-lookup"><span data-stu-id="8dd9a-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="8dd9a-121">GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="8dd9a-122">Derleme oluşturma için kullanılan çalışma zamanı sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8dd9a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dd9a-123">Requirements</span></span>  
 <span data-ttu-id="8dd9a-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dd9a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dd9a-125">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8dd9a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dd9a-126">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8dd9a-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8dd9a-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dd9a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd9a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd9a-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="8dd9a-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8dd9a-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="8dd9a-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dd9a-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
