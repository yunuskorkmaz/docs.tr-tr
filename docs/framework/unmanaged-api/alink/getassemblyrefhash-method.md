---
description: 'Daha fazla bilgi edinin: GetAssemblyRefHash yöntemi'
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
ms.openlocfilehash: d8222d2fdd2c05ca1a23f881989dc344ba294bc1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718479"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="0a0c3-103">GetAssemblyRefHash Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a0c3-103">GetAssemblyRefHash Method</span></span>

<span data-ttu-id="0a0c3-104">Verilen derleme için bir karma blobu alır.</span><span class="sxs-lookup"><span data-stu-id="0a0c3-104">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a0c3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a0c3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a0c3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a0c3-106">Parameters</span></span>  

 `FileToken`  
 <span data-ttu-id="0a0c3-107">Karmasının başvurabileceği derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0a0c3-107">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="0a0c3-108">Elde edilen karma blobu alır.</span><span class="sxs-lookup"><span data-stu-id="0a0c3-108">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="0a0c3-109">Karma Blobun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="0a0c3-109">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a0c3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a0c3-110">Return Value</span></span>  

 <span data-ttu-id="0a0c3-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0c3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a0c3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a0c3-112">Requirements</span></span>  

 <span data-ttu-id="0a0c3-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="0a0c3-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0c3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a0c3-114">See also</span></span>

- [<span data-ttu-id="0a0c3-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a0c3-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0a0c3-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a0c3-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0a0c3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="0a0c3-117">ALink API</span></span>](index.md)
