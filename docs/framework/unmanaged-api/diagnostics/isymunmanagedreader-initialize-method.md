---
title: "ISymUnmanagedReader::Initialize Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="7a72d-102">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a72d-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="7a72d-103">Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.</span><span class="sxs-lookup"><span data-stu-id="7a72d-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a72d-104">Bu yöntem yalnızca bir kez çağrılabilir ve herhangi bir okuyucu yöntem önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a72d-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a72d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a72d-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a72d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a72d-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="7a72d-107">[in] İle bu okuyucu ilişkili olacağı meta verileri alma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7a72d-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="7a72d-108">[in] Modülün dosya adı.</span><span class="sxs-lookup"><span data-stu-id="7a72d-108">[in] The file name of the module.</span></span> <span data-ttu-id="7a72d-109">Kullanabileceğiniz `pIStream` parametre yerine.</span><span class="sxs-lookup"><span data-stu-id="7a72d-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="7a72d-110">[in] Arama yolu.</span><span class="sxs-lookup"><span data-stu-id="7a72d-110">[in] The path to search.</span></span> <span data-ttu-id="7a72d-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a72d-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="7a72d-112">[in] Alternatif bir filename parametresi olarak kullanılan dosya akışı.</span><span class="sxs-lookup"><span data-stu-id="7a72d-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a72d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a72d-113">Return Value</span></span>  
 <span data-ttu-id="7a72d-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7a72d-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a72d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a72d-115">Remarks</span></span>  
 <span data-ttu-id="7a72d-116">Yalnızca birini belirtmek zorunda `filename` veya `pIStream` parametreleri, her ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="7a72d-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="7a72d-117">`searchPath` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a72d-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a72d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a72d-118">Requirements</span></span>  
 <span data-ttu-id="7a72d-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a72d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a72d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a72d-120">See Also</span></span>  
 [<span data-ttu-id="7a72d-121">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a72d-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
