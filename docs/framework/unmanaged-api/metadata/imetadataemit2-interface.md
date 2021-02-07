---
description: 'Daha fazla bilgi edinin: IMetaDataEmit2 Interface'
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
ms.openlocfilehash: db1880d64bf3b1e9084d6745251c174788a4afe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745690"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="e2a1c-103">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-103">IMetaDataEmit2 Interface</span></span>

<span data-ttu-id="e2a1c-104">Genel türlerle çalışma yeteneği sağlamak için öncelikle [ımetadatayayma](imetadataemit-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-104">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2a1c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e2a1c-105">Methods</span></span>  
  
|<span data-ttu-id="e2a1c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e2a1c-106">Method</span></span>|<span data-ttu-id="e2a1c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2a1c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2a1c-108">DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-108">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="e2a1c-109">Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-109">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="e2a1c-110">DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-110">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="e2a1c-111">Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-111">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="e2a1c-112">GetDeltaSaveSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-112">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="e2a1c-113">Geçerli Düzenle ve devam et oturumunun değişikliklerini ifade etmek için gereken verilerin boyutunun farkını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-113">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="e2a1c-114">ResetENCLog Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-114">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="e2a1c-115">Düzenle ve devam et günlüğünü sıfırlar ve yeni bir oturum başlatır.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-115">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="e2a1c-116">SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-116">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="e2a1c-117">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-117">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="e2a1c-118">SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-118">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="e2a1c-119">Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-119">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="e2a1c-120">SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-120">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="e2a1c-121">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-121">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="e2a1c-122">SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-122">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="e2a1c-123">Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-123">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2a1c-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2a1c-124">Requirements</span></span>  

 <span data-ttu-id="e2a1c-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2a1c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a1c-126">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2a1c-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2a1c-127">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e2a1c-127">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2a1c-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a1c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a1c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a1c-129">See also</span></span>

- [<span data-ttu-id="e2a1c-130">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2a1c-130">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="e2a1c-131">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2a1c-131">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
