---
title: GetAssemblyRefHash Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
ms.openlocfilehash: c68f43ce2f79ee6e4ec44ce4b2f0dbfb1c1185fa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433878"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="e2e13-102">GetAssemblyRefHash Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2e13-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="e2e13-103">Retrieves a hash blob for a given assembly.</span><span class="sxs-lookup"><span data-stu-id="e2e13-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2e13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2e13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2e13-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="e2e13-106">ID of assembly to which the hash will refer.</span><span class="sxs-lookup"><span data-stu-id="e2e13-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="e2e13-107">Receives the resulting hash blob.</span><span class="sxs-lookup"><span data-stu-id="e2e13-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="e2e13-108">Receives size, in bytes, of hash blob.</span><span class="sxs-lookup"><span data-stu-id="e2e13-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2e13-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2e13-109">Return Value</span></span>  
 <span data-ttu-id="e2e13-110">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="e2e13-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e13-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2e13-111">Requirements</span></span>  
 <span data-ttu-id="e2e13-112">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="e2e13-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e13-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e13-113">See also</span></span>

- [<span data-ttu-id="e2e13-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2e13-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e2e13-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2e13-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e2e13-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="e2e13-116">ALink API</span></span>](index.md)
