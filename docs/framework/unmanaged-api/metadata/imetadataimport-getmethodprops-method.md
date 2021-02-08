---
description: ': IMetaDataImport:: GetMethodProps Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetMethodProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 5fb344d72378a806e0e71820b55a90998e497916
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783891"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="d96b4-103">IMetaDataImport::GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d96b4-103">IMetaDataImport::GetMethodProps Method</span></span>

<span data-ttu-id="d96b4-104">Belirtilen MethodDef belirtecinin başvurduğu metotla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="d96b4-104">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d96b4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d96b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d96b4-106">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="d96b4-107">'ndaki Meta verilerini döndürecek yöntemi temsil eden MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="d96b4-107">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d96b4-108">dışı Yöntemi uygulayan türü temsil eden bir TypeDef belirtecinin Işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d96b4-108">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="d96b4-109">dışı Metodun adına sahip bir arabelleğin Işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d96b4-109">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="d96b4-110">'ndaki İstenen boyutu `szMethod` .</span><span class="sxs-lookup"><span data-stu-id="d96b4-110">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="d96b4-111">dışı Geniş karakterdeki boyut Işaretçisi `szMethod` veya kesme durumunda, yöntem adındaki geniş karakterlerin gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="d96b4-111">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d96b4-112">dışı Yöntemiyle ilişkili bayrakların bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d96b4-112">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d96b4-113">dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d96b4-113">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d96b4-114">dışı Bayt cinsinden boyut Işaretçisi `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d96b4-114">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="d96b4-115">dışı Metodun göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d96b4-115">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="d96b4-116">dışı Yöntemi için herhangi bir uygulama bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d96b4-116">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96b4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d96b4-117">Requirements</span></span>  

 <span data-ttu-id="d96b4-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d96b4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96b4-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d96b4-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d96b4-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d96b4-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d96b4-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d96b4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96b4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d96b4-122">See also</span></span>

- [<span data-ttu-id="d96b4-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d96b4-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d96b4-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d96b4-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
