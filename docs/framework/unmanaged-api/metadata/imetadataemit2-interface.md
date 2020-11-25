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
ms.openlocfilehash: b8ad159dace734c343297b256092162f17ab829b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726489"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="617d8-102">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="617d8-102">IMetaDataEmit2 Interface</span></span>

<span data-ttu-id="617d8-103">Genel türlerle çalışma yeteneği sağlamak için öncelikle [ımetadatayayma](imetadataemit-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="617d8-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="617d8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="617d8-104">Methods</span></span>  
  
|<span data-ttu-id="617d8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="617d8-105">Method</span></span>|<span data-ttu-id="617d8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="617d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="617d8-107">DefineGenericParam Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="617d8-108">Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="617d8-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="617d8-109">DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="617d8-110">Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="617d8-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="617d8-111">GetDeltaSaveSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="617d8-112">Geçerli Düzenle ve devam et oturumunun değişikliklerini ifade etmek için gereken verilerin boyutunun farkını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="617d8-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="617d8-113">ResetENCLog Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="617d8-114">Düzenle ve devam et günlüğünü sıfırlar ve yeni bir oturum başlatır.</span><span class="sxs-lookup"><span data-stu-id="617d8-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="617d8-115">SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="617d8-116">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="617d8-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="617d8-117">SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="617d8-118">Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="617d8-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="617d8-119">SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="617d8-120">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="617d8-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="617d8-121">SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="617d8-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="617d8-122">Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="617d8-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="617d8-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="617d8-123">Requirements</span></span>  

 <span data-ttu-id="617d8-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="617d8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="617d8-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="617d8-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="617d8-126">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="617d8-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="617d8-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="617d8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617d8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="617d8-128">See also</span></span>

- [<span data-ttu-id="617d8-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="617d8-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="617d8-130">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="617d8-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
