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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200200"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="4cb67-102">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb67-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="4cb67-103">Genişletir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) öncelikle genel türlerle çalışma olanağı sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="4cb67-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4cb67-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4cb67-104">Methods</span></span>  
  
|<span data-ttu-id="4cb67-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4cb67-105">Method</span></span>|<span data-ttu-id="4cb67-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cb67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cb67-107">DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="4cb67-108">Genel tür parametresi için bir tanım oluşturur ve o genel tür parametresi için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="4cb67-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="4cb67-109">DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="4cb67-110">Bir yöntem genel bir örneğini oluşturur ve tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="4cb67-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="4cb67-111">GetDeltaSaveSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="4cb67-112">Düzenle ve devam et geçerli oturum için değişiklikleri ifade etmek için gerekli olan verilerin boyutu arasındaki fark gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4cb67-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="4cb67-113">ResetENCLog Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="4cb67-114">Düzenle ve devam et günlük sıfırlar ve yeni bir oturum başlatır.</span><span class="sxs-lookup"><span data-stu-id="4cb67-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="4cb67-115">SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="4cb67-116">Değişiklikleri geçerli Düzenle ve devam et oturumdan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4cb67-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="4cb67-117">SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="4cb67-118">Değişiklikleri geçerli Düzenle ve devam et oturumdan bellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4cb67-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="4cb67-119">SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="4cb67-120">Değişiklikleri geçerli Düzenle ve devam et oturumundan, belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4cb67-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="4cb67-121">SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cb67-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="4cb67-122">Belirtilen belirteç tarafından başvurulan genel parametre tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4cb67-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cb67-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cb67-123">Requirements</span></span>  
 <span data-ttu-id="4cb67-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb67-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb67-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4cb67-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4cb67-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="4cb67-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="4cb67-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4cb67-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4cb67-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cb67-128">See also</span></span>

- [<span data-ttu-id="4cb67-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4cb67-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="4cb67-130">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cb67-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
