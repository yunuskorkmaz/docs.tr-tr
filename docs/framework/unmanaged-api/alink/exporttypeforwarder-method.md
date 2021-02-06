---
description: 'Daha fazla bilgi edinin: ExportTypeForwarder yöntemi'
title: ExportTypeForwarder Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 59fb74c83f6d30dda87d908353795fb218190022
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637995"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="6d2ee-103">ExportTypeForwarder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2ee-103">ExportTypeForwarder Method</span></span>

<span data-ttu-id="6d2ee-104">Verilen derlemenin tür tablosuna bir tür ileticisi ekler.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-104">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d2ee-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d2ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d2ee-106">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="6d2ee-107">Tür ileticinin başvurduğu derlemeye başvuru.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-107">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="6d2ee-108">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-108">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6d2ee-109">`ComType` veya gibi bayraklar `tdPublic` `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="6d2ee-109">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="6d2ee-110">Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-110">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="6d2ee-111">, Dışarıya aktarılmış türün belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-111">Receives the token of the exported type.</span></span> <span data-ttu-id="6d2ee-112">Bu yalnızca iç içe geçmiş türleri yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-112">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d2ee-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d2ee-113">Return Value</span></span>  

 <span data-ttu-id="6d2ee-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2ee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d2ee-115">Requirements</span></span>  

 <span data-ttu-id="6d2ee-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="6d2ee-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2ee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2ee-117">See also</span></span>

- [<span data-ttu-id="6d2ee-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d2ee-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6d2ee-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d2ee-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6d2ee-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="6d2ee-120">ALink API</span></span>](index.md)
