---
title: SetAssemblyFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7be346f1c92c877932957787b0747515c144752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741541"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="eb941-102">SetAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb941-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="eb941-103">Oluşturulacak derlemenin adını atar.</span><span class="sxs-lookup"><span data-stu-id="eb941-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="eb941-104">İlişkisiz modülleri üretirken amaçla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb941-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb941-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb941-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb941-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb941-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="eb941-107">Bildirim dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="eb941-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="eb941-108">İşaretçi [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="eb941-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="eb941-109">Bayrakları sınıfında tanımlandığı gibi [AssemblyFlags numaralandırması](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="eb941-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="eb941-110">Oluşturulan derleme kimliği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb941-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb941-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eb941-111">Return Value</span></span>  
 <span data-ttu-id="eb941-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb941-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb941-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb941-113">Requirements</span></span>  
 <span data-ttu-id="eb941-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eb941-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb941-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb941-115">See also</span></span>

- [<span data-ttu-id="eb941-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb941-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="eb941-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb941-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="eb941-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="eb941-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
