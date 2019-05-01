---
title: IMetaDataEmit2 Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87b5b60d75d5d28e100ec75192d0cacf51765927
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042980"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="eabe5-102">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eabe5-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="eabe5-103">Genişletir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) öncelikle genel türlerle çalışma olanağı sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="eabe5-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eabe5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eabe5-104">Methods</span></span>  
  
|<span data-ttu-id="eabe5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eabe5-105">Method</span></span>|<span data-ttu-id="eabe5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eabe5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eabe5-107">DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="eabe5-108">Genel tür parametresi için bir tanım oluşturur ve o genel tür parametresi için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="eabe5-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="eabe5-109">DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="eabe5-110">Bir yöntem genel bir örneğini oluşturur ve tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="eabe5-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="eabe5-111">GetDeltaSaveSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="eabe5-112">Düzenle ve devam et geçerli oturum için değişiklikleri ifade etmek için gerekli olan verilerin boyutu arasındaki fark gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="eabe5-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="eabe5-113">ResetENCLog Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="eabe5-114">Düzenle ve devam et günlük sıfırlar ve yeni bir oturum başlatır.</span><span class="sxs-lookup"><span data-stu-id="eabe5-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="eabe5-115">SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="eabe5-116">Değişiklikleri geçerli Düzenle ve devam et oturumdan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eabe5-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="eabe5-117">SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="eabe5-118">Değişiklikleri geçerli Düzenle ve devam et oturumdan bellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eabe5-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="eabe5-119">SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="eabe5-120">Değişiklikleri geçerli Düzenle ve devam et oturumundan, belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eabe5-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="eabe5-121">SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabe5-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="eabe5-122">Belirtilen belirteç tarafından başvurulan genel parametre tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eabe5-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eabe5-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eabe5-123">Requirements</span></span>  
 <span data-ttu-id="eabe5-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eabe5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eabe5-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="eabe5-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eabe5-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="eabe5-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eabe5-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eabe5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabe5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eabe5-128">See also</span></span>

- [<span data-ttu-id="eabe5-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eabe5-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="eabe5-130">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eabe5-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
