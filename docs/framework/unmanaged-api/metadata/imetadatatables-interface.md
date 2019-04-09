---
title: IMetaDataTables Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131423"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="fe4f9-102">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="fe4f9-103">Tablo meta veri bilgilerini alma ve depolama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe4f9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe4f9-104">Methods</span></span>  
  
|<span data-ttu-id="fe4f9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe4f9-105">Method</span></span>|<span data-ttu-id="fe4f9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe4f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe4f9-107">GetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="fe4f9-108">Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="fe4f9-109">GetBlobHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="fe4f9-110">BLOB yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="fe4f9-111">GetCodedTokenInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="fe4f9-112">Belirteçlerin belirtilen satır dizini ile ilişkili bir diziye bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="fe4f9-113">GetColumn Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="fe4f9-114">Belirtilen tablo dizini altındaki tabloda belirtilen sütun dizinindeki sütunda bulunan değerleri için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="fe4f9-115">GetColumnInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="fe4f9-116">Belirtilen tabloda belirtilen sütuna ilişkin verileri alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="fe4f9-117">GetGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="fe4f9-118">Belirtilen dizindeki satırdaki bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="fe4f9-119">GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="fe4f9-120">GUID yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="fe4f9-121">GetNextBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="fe4f9-122">Sonraki blob dizin tablosunda alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="fe4f9-123">GetNextGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="fe4f9-124">Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="fe4f9-125">GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="fe4f9-126">Geçerli bir tablo sütununda sonraki dize dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="fe4f9-127">GetNextUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="fe4f9-128">Sonraki sabit kodlanmış dize geçerli bir tablo sütunu içeren satırı dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="fe4f9-129">GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="fe4f9-130">Tablo sayısı geçerli kapsamda alır `IMetaDataTables` örneği.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="fe4f9-131">GetRow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="fe4f9-132">Belirtilen tablo dizini altındaki tabloda belirtilen satır dizinindeki bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="fe4f9-133">GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="fe4f9-134">Dize, geçerli başvuru kapsamda tablo sütunuyla bağlantısı belirtilen dizindeki alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="fe4f9-135">GetStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="fe4f9-136">Dize yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="fe4f9-137">GetTableIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="fe4f9-138">Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="fe4f9-139">GetTableInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="fe4f9-140">Belirtilen tablo dizin adı, satır boyutu, satır sayısı, sütun sayısı ve tablonun anahtar sütunu dizini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="fe4f9-141">GetUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="fe4f9-142">Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="fe4f9-143">GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="fe4f9-144">Kullanıcı dize yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe4f9-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe4f9-145">Requirements</span></span>  
 <span data-ttu-id="fe4f9-146">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f9-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe4f9-147">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fe4f9-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe4f9-148">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="fe4f9-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fe4f9-149">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="fe4f9-149">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe4f9-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4f9-150">See also</span></span>

- [<span data-ttu-id="fe4f9-151">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe4f9-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="fe4f9-152">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe4f9-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
