---
title: ExportNestedTypeForwarder Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eee41e9f71d600a74cc9f74b538ad9e215f0d905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="a7b82-102">ExportNestedTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="a7b82-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="a7b82-103">İç içe geçmiş tür için bir tür iletici verilen derleme türü tablosuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a7b82-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7b82-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7b82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7b82-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a7b82-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="a7b82-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a7b82-107">Dosya belirteç veya derleme kimliği türü tanımlayan dosyası.</span><span class="sxs-lookup"><span data-stu-id="a7b82-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="a7b82-108">Belirteç türü için.</span><span class="sxs-lookup"><span data-stu-id="a7b82-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="a7b82-109">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="a7b82-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="a7b82-110">Dışarı aktarmak için tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="a7b82-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a7b82-111">`ComType`gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="a7b82-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="a7b82-112">Dışarı aktarma türünde belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="a7b82-112">Receives token of export type.</span></span> <span data-ttu-id="a7b82-113">Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7b82-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7b82-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7b82-114">Return Value</span></span>  
 <span data-ttu-id="a7b82-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7b82-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b82-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7b82-116">Requirements</span></span>  
 <span data-ttu-id="a7b82-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a7b82-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b82-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7b82-118">See Also</span></span>  
 [<span data-ttu-id="a7b82-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b82-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a7b82-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b82-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a7b82-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="a7b82-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
