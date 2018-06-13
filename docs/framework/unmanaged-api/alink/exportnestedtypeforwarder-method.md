---
title: ExportNestedTypeForwarder Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404117"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="b935c-102">ExportNestedTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="b935c-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="b935c-103">İç içe geçmiş tür için bir tür iletici verilen derleme türü tablosuna ekler.</span><span class="sxs-lookup"><span data-stu-id="b935c-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b935c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b935c-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b935c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b935c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b935c-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="b935c-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b935c-107">Dosya belirteç veya derleme kimliği türü tanımlayan dosyası.</span><span class="sxs-lookup"><span data-stu-id="b935c-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="b935c-108">Belirteç türü için.</span><span class="sxs-lookup"><span data-stu-id="b935c-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="b935c-109">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="b935c-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="b935c-110">Dışarı aktarmak için tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="b935c-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b935c-111">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="b935c-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="b935c-112">Dışarı aktarma türünde belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="b935c-112">Receives token of export type.</span></span> <span data-ttu-id="b935c-113">Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b935c-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b935c-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b935c-114">Return Value</span></span>  
 <span data-ttu-id="b935c-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b935c-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b935c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b935c-116">Requirements</span></span>  
 <span data-ttu-id="b935c-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="b935c-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b935c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b935c-118">See Also</span></span>  
 [<span data-ttu-id="b935c-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b935c-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b935c-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b935c-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b935c-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="b935c-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
