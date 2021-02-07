---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyEmit::D efineAssembly yöntemi'
title: IMetaDataAssemblyEmit::DefineAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: cd53a4398f49ca96072fc5f5b6dcac35a94bdc59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706766"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="75419-103">IMetaDataAssemblyEmit::DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75419-103">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>

<span data-ttu-id="75419-104">`Assembly`Belirtilen derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="75419-104">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75419-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75419-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75419-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75419-106">Parameters</span></span>  

 `pbPublicKey`  
 <span data-ttu-id="75419-107">'ndaki Derlemenin yayımcısını tanımlayan ortak anahtar veya derleme kesin olarak adlandırılmamışsa NULL.</span><span class="sxs-lookup"><span data-stu-id="75419-107">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="75419-108">'ndaki Bayt cinsinden boyut `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="75419-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="75419-109">'ndaki Derlemedeki dosyaları şifrelemek için kullanılan karma algoritmanın tanımlayıcısı ya da SHA-1 algoritmasını belirtmek için NULL.</span><span class="sxs-lookup"><span data-stu-id="75419-109">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="75419-110">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="75419-110">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="75419-111">Bu değerin 1024 karakteri aşmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="75419-111">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="75419-112">'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75419-112">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="75419-113">'ndaki Derlemenin özelliklerini tanımlayan [CorAssemblyFlags](corassemblyflags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="75419-113">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="75419-114">dışı Meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75419-114">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75419-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75419-115">Remarks</span></span>  

 <span data-ttu-id="75419-116">`Assembly`Bir bildirim içinde yalnızca bir meta veri yapısı tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="75419-116">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75419-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75419-117">Requirements</span></span>  

 <span data-ttu-id="75419-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75419-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75419-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="75419-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75419-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="75419-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75419-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75419-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75419-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75419-122">See also</span></span>

- [<span data-ttu-id="75419-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75419-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
