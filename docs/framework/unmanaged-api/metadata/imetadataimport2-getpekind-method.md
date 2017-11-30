---
title: IMetaDataImport2::GetPEKind Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9fc963f38a845db67bb5b5d377ecabf9a40c359f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="a38ba-102">IMetaDataImport2::GetPEKind Metodu</span><span class="sxs-lookup"><span data-stu-id="a38ba-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="a38ba-103">Alır taşınabilir yürütülebilir (PE) kodda yapısını tanımlayan bir değer, geçerli meta veri kapsamda tanımlanan genellikle bir DLL veya EXE dosyası dosyasında.</span><span class="sxs-lookup"><span data-stu-id="a38ba-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a38ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a38ba-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a38ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a38ba-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="a38ba-106">[out] Değerini gösteren bir işaretçi [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) PE dosya tanımlar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="a38ba-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="a38ba-107">[out] Makine mimarisi tanımlayan bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a38ba-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="a38ba-108">Olası değerler için sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="a38ba-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a38ba-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a38ba-109">Remarks</span></span>  
 <span data-ttu-id="a38ba-110">Tarafından başvurulan değer `pdwMachine` parametresi şunlardan biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a38ba-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="a38ba-111">Değer</span><span class="sxs-lookup"><span data-stu-id="a38ba-111">Value</span></span>|<span data-ttu-id="a38ba-112">Makine mimarisi</span><span class="sxs-lookup"><span data-stu-id="a38ba-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="a38ba-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="a38ba-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="a38ba-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="a38ba-114">0x014C</span></span>|<span data-ttu-id="a38ba-115">x86</span><span class="sxs-lookup"><span data-stu-id="a38ba-115">x86</span></span>|  
|<span data-ttu-id="a38ba-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="a38ba-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="a38ba-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="a38ba-117">0x0200</span></span>|<span data-ttu-id="a38ba-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="a38ba-118">Intel IPF</span></span>|  
|<span data-ttu-id="a38ba-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="a38ba-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="a38ba-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="a38ba-120">0x8664</span></span>|<span data-ttu-id="a38ba-121">x64</span><span class="sxs-lookup"><span data-stu-id="a38ba-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a38ba-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a38ba-122">Requirements</span></span>  
 <span data-ttu-id="a38ba-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a38ba-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a38ba-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a38ba-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a38ba-125">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a38ba-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a38ba-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38ba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38ba-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a38ba-127">See Also</span></span>  
 [<span data-ttu-id="a38ba-128">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="a38ba-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="a38ba-129">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="a38ba-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a38ba-130">CorPEKind numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a38ba-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
