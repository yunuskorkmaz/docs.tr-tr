---
title: IMetaDataImport2::GetVersionString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 112ddcf51a5637bb89df9479850c2a4a70d2e1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448732"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="2311e-102">IMetaDataImport2::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="2311e-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="2311e-103">Derleme oluşturma için kullanılan çalışma zamanı sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="2311e-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2311e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2311e-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2311e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2311e-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="2311e-106">[out] Sürüm belirten bir dize depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2311e-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="2311e-107">[in] Geniş karakterler boyutu, `pwzBuf` dizi.</span><span class="sxs-lookup"><span data-stu-id="2311e-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="2311e-108">[out] Null Sonlandırıcı dahil olmak üzere geniş karakter sayısını döndürülen `pwzBuf` dizi.</span><span class="sxs-lookup"><span data-stu-id="2311e-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2311e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2311e-109">Remarks</span></span>  
 <span data-ttu-id="2311e-110">`GetVersionString` Yöntemi geçerli meta veri kapsamı yerleşik için sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="2311e-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="2311e-111">Kapsam hiçbir zaman kaydedilmişse, bir yerleşik için sürümüne sahip değil ve boş bir dize döndürdü.</span><span class="sxs-lookup"><span data-stu-id="2311e-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2311e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2311e-112">Requirements</span></span>  
 <span data-ttu-id="2311e-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2311e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2311e-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2311e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2311e-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2311e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2311e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2311e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2311e-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2311e-117">See Also</span></span>  
 [<span data-ttu-id="2311e-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2311e-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="2311e-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2311e-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
