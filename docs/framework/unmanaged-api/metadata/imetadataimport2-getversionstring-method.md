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
ms.openlocfilehash: 5e041efed929255d4ce3af2d051a391bc4179cda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630924"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="0ad89-102">IMetaDataImport2::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="0ad89-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="0ad89-103">Derlemesi oluşturmak için kullanılan çalışma zamanı sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="0ad89-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ad89-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ad89-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ad89-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="0ad89-106">[out] Sürümünü belirten bir dize depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="0ad89-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="0ad89-107">[in] Geniş karakter cinsinden boyutu, `pwzBuf` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0ad89-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="0ad89-108">[out] Null sonlandırıcıyı da dahil olmak üzere geniş karakter sayısına göre döndürülen `pwzBuf` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0ad89-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ad89-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ad89-109">Remarks</span></span>  
 <span data-ttu-id="0ad89-110">`GetVersionString` Yöntemi geçerli meta veri kapsamı için yerleşik sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="0ad89-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="0ad89-111">Kapsamı hiç kaydedilmemişse, yerleşik bir sürüm olmaz ve boş bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0ad89-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ad89-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ad89-112">Requirements</span></span>  
 <span data-ttu-id="0ad89-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ad89-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ad89-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0ad89-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ad89-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="0ad89-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ad89-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ad89-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad89-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ad89-117">See also</span></span>
- [<span data-ttu-id="0ad89-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ad89-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="0ad89-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ad89-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
