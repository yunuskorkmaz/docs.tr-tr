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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d19eebaa3aa0ebb6f9807f0cf277b7ed6183c148
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777198"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="8ef4c-102">GetAssemblyRefHash Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ef4c-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="8ef4c-103">Verilen derleme için bir karma blobu alır.</span><span class="sxs-lookup"><span data-stu-id="8ef4c-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ef4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ef4c-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="8ef4c-106">Karmasının başvurabileceği derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8ef4c-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="8ef4c-107">Elde edilen karma blobu alır.</span><span class="sxs-lookup"><span data-stu-id="8ef4c-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="8ef4c-108">Karma Blobun boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="8ef4c-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ef4c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ef4c-109">Return Value</span></span>  
 <span data-ttu-id="8ef4c-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ef4c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef4c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ef4c-111">Requirements</span></span>  
 <span data-ttu-id="8ef4c-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8ef4c-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef4c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ef4c-113">See also</span></span>

- [<span data-ttu-id="8ef4c-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ef4c-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8ef4c-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ef4c-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8ef4c-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="8ef4c-116">ALink API</span></span>](index.md)
