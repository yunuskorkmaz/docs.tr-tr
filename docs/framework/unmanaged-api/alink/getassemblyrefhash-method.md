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
ms.openlocfilehash: af040c4a6c9b85930d2d9261f8587ba69eb204e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721484"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="aeb41-102">GetAssemblyRefHash Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeb41-102">GetAssemblyRefHash Method</span></span>

<span data-ttu-id="aeb41-103">Verilen derleme için bir karma blobu alır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb41-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aeb41-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeb41-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aeb41-105">Parameters</span></span>  

 `FileToken`  
 <span data-ttu-id="aeb41-106">Karmasının başvurabileceği derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aeb41-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="aeb41-107">Elde edilen karma blobu alır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="aeb41-108">Karma Blobun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aeb41-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aeb41-109">Return Value</span></span>  

 <span data-ttu-id="aeb41-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb41-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb41-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeb41-111">Requirements</span></span>  

 <span data-ttu-id="aeb41-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="aeb41-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb41-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb41-113">See also</span></span>

- [<span data-ttu-id="aeb41-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb41-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="aeb41-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeb41-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="aeb41-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="aeb41-116">ALink API</span></span>](index.md)
