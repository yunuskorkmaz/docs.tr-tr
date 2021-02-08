---
description: ': IMetaDataConverter arabirimi hakkında daha fazla bilgi edinin'
title: IMetaDataConverter Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 6ed84083bad924e760c576afe485bd7ccad012cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789261"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="96d56-103">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96d56-103">IMetaDataConverter Interface</span></span>

<span data-ttu-id="96d56-104">Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d56-104">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96d56-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="96d56-105">Methods</span></span>  
  
|<span data-ttu-id="96d56-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="96d56-106">Method</span></span>|<span data-ttu-id="96d56-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96d56-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96d56-108">GetMetaDataFromTypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96d56-108">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="96d56-109">Belirtilen örnek tarafından başvurulan tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) örneğine yönelik bir işaretçi alır `ITypeInfo` .</span><span class="sxs-lookup"><span data-stu-id="96d56-109">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="96d56-110">GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96d56-110">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="96d56-111">`IMetaDataImport`Belirtilen örnek tarafından temsil edilen tür kitaplığı için meta veri imzasını temsil eden bir örneğe yönelik bir işaretçi alır `ITypeLib` .</span><span class="sxs-lookup"><span data-stu-id="96d56-111">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="96d56-112">GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96d56-112">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="96d56-113">`ITypeLib`Belirtilen modüle ve kitaplık adlarına sahip tür kitaplığını temsil eden bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="96d56-113">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96d56-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96d56-114">Requirements</span></span>  

 <span data-ttu-id="96d56-115">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96d56-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96d56-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96d56-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96d56-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="96d56-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96d56-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96d56-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d56-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96d56-119">See also</span></span>

- [<span data-ttu-id="96d56-120">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96d56-120">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="96d56-121">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96d56-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
