---
title: IMetaDataConverter Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter
helpviewer_keywords: IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f551a774a860f595cc90a7cca9eee2c726ef50ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="1e12a-102">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e12a-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="1e12a-103">Tür kitaplıkları kendi meta verileri imzalar için eşleme ve diğerine dönüştürmek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e12a-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e12a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1e12a-104">Methods</span></span>  
  
|<span data-ttu-id="1e12a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1e12a-105">Method</span></span>|<span data-ttu-id="1e12a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e12a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e12a-107">Getmetadatafromtypeınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e12a-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="1e12a-108">Bir işaretçi alır bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) belirtilen tarafından başvurulan tür kitaplığı için meta veri imzası temsil eden örneği `ITypeInfo` örneği.</span><span class="sxs-lookup"><span data-stu-id="1e12a-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="1e12a-109">GetMetaDataFromTypeLib yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e12a-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="1e12a-110">Bir işaretçi alır bir `IMetaDataImport` belirtilen tarafından temsil edilen tür kitaplığı için meta veri imzası temsil eden örneği `ITypeLib` örneği.</span><span class="sxs-lookup"><span data-stu-id="1e12a-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="1e12a-111">GetTypeLibFromMetaData yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e12a-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="1e12a-112">Bir işaretçi alır bir `ITypeLib` belirtilen modülü ve kitaplık adlara sahip tür kitaplığı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="1e12a-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e12a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e12a-113">Requirements</span></span>  
 <span data-ttu-id="1e12a-114">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e12a-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e12a-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1e12a-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e12a-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1e12a-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e12a-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e12a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e12a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e12a-118">See Also</span></span>  
 [<span data-ttu-id="1e12a-119">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1e12a-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="1e12a-120">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e12a-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
