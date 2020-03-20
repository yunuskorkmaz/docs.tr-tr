---
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179405"
---
# <a name="getscope2-method"></a><span data-ttu-id="d54c6-102">GetScope2 Metodu</span><span class="sxs-lookup"><span data-stu-id="d54c6-102">GetScope2 Method</span></span>
<span data-ttu-id="d54c6-103">Bir alma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="d54c6-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d54c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="d54c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d54c6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d54c6-106">Hedef montaj kimliği.</span><span class="sxs-lookup"><span data-stu-id="d54c6-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d54c6-107">Hangi dosyanın kimlik almak için.</span><span class="sxs-lookup"><span data-stu-id="d54c6-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d54c6-108">Almak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="d54c6-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d54c6-109">Belirtilen kapsam için [IMetaDataImport2 Arabirim](../metadata/imetadataimport2-interface.md) arabirimine işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d54c6-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d54c6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d54c6-110">Return Value</span></span>  
 <span data-ttu-id="d54c6-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d54c6-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d54c6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d54c6-112">Requirements</span></span>  
 <span data-ttu-id="d54c6-113">Alink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d54c6-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54c6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d54c6-114">See also</span></span>

- [<span data-ttu-id="d54c6-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d54c6-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d54c6-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d54c6-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d54c6-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="d54c6-117">ALink API</span></span>](index.md)
