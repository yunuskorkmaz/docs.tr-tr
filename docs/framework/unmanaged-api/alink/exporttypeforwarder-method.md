---
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
ms.openlocfilehash: 4e6ceabf37056bfc25247266be2c7801cb0e13e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684778"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="417cf-102">ExportTypeForwarder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="417cf-102">ExportTypeForwarder Method</span></span>

<span data-ttu-id="417cf-103">Verilen derlemenin tür tablosuna bir tür ileticisi ekler.</span><span class="sxs-lookup"><span data-stu-id="417cf-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="417cf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="417cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="417cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="417cf-105">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="417cf-106">Tür ileticinin başvurduğu derlemeye başvuru.</span><span class="sxs-lookup"><span data-stu-id="417cf-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="417cf-107">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="417cf-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="417cf-108">`ComType` veya gibi bayraklar `tdPublic` `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="417cf-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="417cf-109">Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="417cf-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="417cf-110">, Dışarıya aktarılmış türün belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="417cf-110">Receives the token of the exported type.</span></span> <span data-ttu-id="417cf-111">Bu yalnızca iç içe geçmiş türleri yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="417cf-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="417cf-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="417cf-112">Return Value</span></span>  

 <span data-ttu-id="417cf-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="417cf-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="417cf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="417cf-114">Requirements</span></span>  

 <span data-ttu-id="417cf-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="417cf-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="417cf-116">See also</span></span>

- [<span data-ttu-id="417cf-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="417cf-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="417cf-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="417cf-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="417cf-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="417cf-119">ALink API</span></span>](index.md)
