---
title: IMetaDataImport2::GetPEKind Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8dc31877ba3550fa8faf610b831dfd2e7b313ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="33a40-102">IMetaDataImport2::GetPEKind Metodu</span><span class="sxs-lookup"><span data-stu-id="33a40-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="33a40-103">Alır taşınabilir yürütülebilir (PE) kodda yapısını tanımlayan bir değer, geçerli meta veri kapsamda tanımlanan genellikle bir DLL veya EXE dosyası dosyasında.</span><span class="sxs-lookup"><span data-stu-id="33a40-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33a40-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33a40-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33a40-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="33a40-106">[out] Değerini gösteren bir işaretçi [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) PE dosya tanımlar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="33a40-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="33a40-107">[out] Makine mimarisi tanımlayan bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="33a40-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="33a40-108">Olası değerler için sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="33a40-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33a40-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33a40-109">Remarks</span></span>  
 <span data-ttu-id="33a40-110">Tarafından başvurulan değer `pdwMachine` parametresi şunlardan biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="33a40-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="33a40-111">Değer</span><span class="sxs-lookup"><span data-stu-id="33a40-111">Value</span></span>|<span data-ttu-id="33a40-112">Makine mimarisi</span><span class="sxs-lookup"><span data-stu-id="33a40-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="33a40-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="33a40-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="33a40-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="33a40-114">0x014C</span></span>|<span data-ttu-id="33a40-115">x86</span><span class="sxs-lookup"><span data-stu-id="33a40-115">x86</span></span>|  
|<span data-ttu-id="33a40-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="33a40-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="33a40-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="33a40-117">0x0200</span></span>|<span data-ttu-id="33a40-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="33a40-118">Intel IPF</span></span>|  
|<span data-ttu-id="33a40-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="33a40-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="33a40-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="33a40-120">0x8664</span></span>|<span data-ttu-id="33a40-121">X64</span><span class="sxs-lookup"><span data-stu-id="33a40-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33a40-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33a40-122">Requirements</span></span>  
 <span data-ttu-id="33a40-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a40-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a40-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="33a40-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33a40-125">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="33a40-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33a40-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a40-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a40-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33a40-127">See Also</span></span>  
 [<span data-ttu-id="33a40-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33a40-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="33a40-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33a40-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="33a40-130">CorPEKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="33a40-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
