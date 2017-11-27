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
ms.openlocfilehash: 5917fbe3cebe9b1e9ab91d113aee2461f414c14d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="ed462-102">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed462-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="ed462-103">Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.</span><span class="sxs-lookup"><span data-stu-id="ed462-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed462-104">Bu yöntem yalnızca bir kez çağrılabilir ve herhangi bir okuyucu yöntem önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed462-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed462-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed462-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed462-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed462-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="ed462-107">[in] İle bu okuyucu ilişkili olacağı meta verileri alma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ed462-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="ed462-108">[in] Modülün dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ed462-108">[in] The file name of the module.</span></span> <span data-ttu-id="ed462-109">Kullanabileceğiniz `pIStream` parametre yerine.</span><span class="sxs-lookup"><span data-stu-id="ed462-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ed462-110">[in] Arama yolu.</span><span class="sxs-lookup"><span data-stu-id="ed462-110">[in] The path to search.</span></span> <span data-ttu-id="ed462-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ed462-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ed462-112">[in] Alternatif bir filename parametresi olarak kullanılan dosya akışı.</span><span class="sxs-lookup"><span data-stu-id="ed462-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed462-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed462-113">Return Value</span></span>  
 <span data-ttu-id="ed462-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ed462-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed462-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed462-115">Remarks</span></span>  
 <span data-ttu-id="ed462-116">Yalnızca birini belirtmek zorunda `filename` veya `pIStream` parametreleri, her ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="ed462-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="ed462-117">`searchPath` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ed462-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed462-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed462-118">Requirements</span></span>  
 <span data-ttu-id="ed462-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ed462-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed462-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed462-120">See Also</span></span>  
 [<span data-ttu-id="ed462-121">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed462-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
