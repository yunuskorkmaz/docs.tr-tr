---
title: EnumImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90319886dfe149a3d2d76451c1a8526299cf5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401654"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="f6710-102">EnumImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6710-102">EnumImportTypes Method</span></span>
<span data-ttu-id="f6710-103">Her kapsamda her türünü numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f6710-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6710-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6710-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6710-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6710-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f6710-106">Numaralandırıcı işleci.</span><span class="sxs-lookup"><span data-stu-id="f6710-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="f6710-107">Alınacak türleri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="f6710-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="f6710-108">Recieves yazın aşmayan belirteçleri `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="f6710-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="f6710-109">Türü gerçek sayısını alır `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="f6710-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6710-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f6710-110">Return Value</span></span>  
 <span data-ttu-id="f6710-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6710-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6710-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6710-112">Requirements</span></span>  
 <span data-ttu-id="f6710-113">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="f6710-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6710-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6710-114">See Also</span></span>  
 [<span data-ttu-id="f6710-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6710-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f6710-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6710-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f6710-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="f6710-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
