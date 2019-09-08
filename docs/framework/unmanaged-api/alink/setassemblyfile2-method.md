---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aba11ccd61b65d2a779b39db8e0e082cf4d4015b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787222"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="eb4cf-102">SetAssemblyFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4cf-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="eb4cf-103">Yeni bir derleme için adını ve seçeneklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="eb4cf-104">İlişkisiz modüller üretmeniz durumunda bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4cf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb4cf-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb4cf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb4cf-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="eb4cf-107">Bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="eb4cf-108">Bu dosya için [IMetaDataEmit2 arabirimi](../metadata/imetadataemit2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="eb4cf-109">[AssemblyFlags numaralandırması](../metadata/assemblyflags-enumeration.md)tarafından temsil edilen seçenekler.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="eb4cf-110">Oluşturulan derlemenin benzersiz KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb4cf-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eb4cf-111">Return Value</span></span>  
 <span data-ttu-id="eb4cf-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb4cf-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb4cf-113">Requirements</span></span>  
 <span data-ttu-id="eb4cf-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4cf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4cf-115">See also</span></span>

- [<span data-ttu-id="eb4cf-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb4cf-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="eb4cf-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb4cf-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="eb4cf-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="eb4cf-118">ALink API</span></span>](index.md)
