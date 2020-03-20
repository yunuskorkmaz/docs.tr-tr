---
title: IMetaDataAssemblyEmit::DefineFile Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176064"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="91468-102">IMetaDataAssemblyEmit::DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91468-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="91468-103">Bu derleme `File` tarafından başvurulan derleme için meta veri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="91468-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91468-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91468-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91468-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91468-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="91468-106">[içinde] Tüketilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="91468-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="91468-107">[içinde] Derleme ile ilişkili karma verilere işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91468-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="91468-108">[içinde] `pbHashValue`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="91468-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="91468-109">[içinde] Özellik ayarlarını `FileFlags` belirten değerlerin bitwise birleşimi.</span><span class="sxs-lookup"><span data-stu-id="91468-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="91468-110">[çıkış] Döndürülen `File` belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91468-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91468-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91468-111">Remarks</span></span>  
 <span data-ttu-id="91468-112">Meta `File` verileri içeren dosya hariç olmak üzere, bu derlemenin yapıldığı sırada bu derlemenin parçası olan her dosya için bir meta veri yapısı tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91468-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91468-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91468-113">Requirements</span></span>  
 <span data-ttu-id="91468-114">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91468-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91468-115">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="91468-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91468-116">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="91468-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91468-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91468-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91468-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91468-118">See also</span></span>

- [<span data-ttu-id="91468-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91468-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
