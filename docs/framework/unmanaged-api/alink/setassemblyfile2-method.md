---
description: 'Daha fazla bilgi edinin: SetAssemblyFile2 yöntemi'
title: SetAssemblyFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 890646b718c211b476d013daf021f8889198c1ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662409"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="5aea7-103">SetAssemblyFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5aea7-103">SetAssemblyFile2 Method</span></span>

<span data-ttu-id="5aea7-104">Yeni bir derleme için adını ve seçeneklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5aea7-104">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="5aea7-105">İlişkisiz modüller üretmeniz durumunda bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="5aea7-105">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aea7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5aea7-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aea7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5aea7-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="5aea7-108">Bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="5aea7-108">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="5aea7-109">Bu dosya için [IMetaDataEmit2 arabirimi](../metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5aea7-109">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="5aea7-110">[AssemblyFlags numaralandırması](../metadata/assemblyflags-enumeration.md)tarafından temsil edilen seçenekler.</span><span class="sxs-lookup"><span data-stu-id="5aea7-110">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="5aea7-111">Oluşturulan derlemenin benzersiz KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="5aea7-111">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aea7-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5aea7-112">Return Value</span></span>  

 <span data-ttu-id="5aea7-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5aea7-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aea7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5aea7-114">Requirements</span></span>  

 <span data-ttu-id="5aea7-115">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5aea7-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aea7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aea7-116">See also</span></span>

- [<span data-ttu-id="5aea7-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5aea7-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5aea7-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5aea7-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5aea7-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="5aea7-119">ALink API</span></span>](index.md)
