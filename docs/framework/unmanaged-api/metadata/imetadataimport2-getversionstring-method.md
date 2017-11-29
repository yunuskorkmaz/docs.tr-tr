---
title: IMetaDataImport2::GetVersionString Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d08f43a790305c960d557064539de680a2d04af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="71010-102">IMetaDataImport2::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="71010-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="71010-103">Derleme oluşturma için kullanılan çalışma zamanı sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="71010-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71010-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71010-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71010-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71010-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="71010-106">[out] Sürüm belirten bir dize depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="71010-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="71010-107">[in] Geniş karakterler boyutu, `pwzBuf` dizi.</span><span class="sxs-lookup"><span data-stu-id="71010-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="71010-108">[out] Null Sonlandırıcı dahil olmak üzere geniş karakter sayısını döndürülen `pwzBuf` dizi.</span><span class="sxs-lookup"><span data-stu-id="71010-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71010-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71010-109">Remarks</span></span>  
 <span data-ttu-id="71010-110">`GetVersionString` Yöntemi geçerli meta veri kapsamı yerleşik için sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="71010-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="71010-111">Kapsam hiçbir zaman kaydedilmişse, bir yerleşik için sürümüne sahip değil ve boş bir dize döndürdü.</span><span class="sxs-lookup"><span data-stu-id="71010-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71010-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71010-112">Requirements</span></span>  
 <span data-ttu-id="71010-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71010-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71010-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71010-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71010-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="71010-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71010-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71010-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71010-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71010-117">See Also</span></span>  
 [<span data-ttu-id="71010-118">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="71010-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="71010-119">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="71010-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
