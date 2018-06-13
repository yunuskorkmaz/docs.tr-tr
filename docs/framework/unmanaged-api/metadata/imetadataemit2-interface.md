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
ms.openlocfilehash: 418e5287852b1a8d69d310d2ba71e4f2a3b5d7bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449237"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="1d213-102">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d213-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="1d213-103">Genişletir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) öncelikle genel türleri ile çalışma olanağı sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="1d213-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d213-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d213-104">Methods</span></span>  
  
|<span data-ttu-id="1d213-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1d213-105">Method</span></span>|<span data-ttu-id="1d213-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d213-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d213-107">DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="1d213-108">Genel tür parametresi için bir tanım oluşturur ve o genel tür parametresi için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="1d213-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="1d213-109">DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="1d213-110">Bir yöntem genel bir örneğini oluşturur ve tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="1d213-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="1d213-111">GetDeltaSaveSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="1d213-112">Düzenle ve devam et geçerli oturum için değişiklikleri ifade etmek için gerekli verilerin boyutunu fark belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1d213-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="1d213-113">ResetENCLog Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="1d213-114">Düzenle ve devam et günlük sıfırlar ve yeni bir oturum başlatır.</span><span class="sxs-lookup"><span data-stu-id="1d213-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="1d213-115">SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="1d213-116">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1d213-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="1d213-117">SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="1d213-118">Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1d213-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="1d213-119">SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="1d213-120">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1d213-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="1d213-121">SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d213-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="1d213-122">Belirtilen belirteç tarafından başvurulan genel parametresini tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1d213-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d213-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d213-123">Requirements</span></span>  
 <span data-ttu-id="1d213-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d213-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d213-125">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1d213-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d213-126">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1d213-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d213-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d213-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d213-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d213-128">See Also</span></span>  
 [<span data-ttu-id="1d213-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d213-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="1d213-130">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d213-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
