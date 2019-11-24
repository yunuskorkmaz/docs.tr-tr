---
title: ISymUnmanagedReader::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429744"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="bb5a9-102">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb5a9-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="bb5a9-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb5a9-104">This method can be called only once, and must be called before any other reader methods.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb5a9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb5a9-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb5a9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb5a9-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="bb5a9-107">[in] The metadata importer interface with which this reader will be associated.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="bb5a9-108">[in] The file name of the module.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-108">[in] The file name of the module.</span></span> <span data-ttu-id="bb5a9-109">You can use the `pIStream` parameter instead.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="bb5a9-110">[in] The path to search.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-110">[in] The path to search.</span></span> <span data-ttu-id="bb5a9-111">This parameter is optional.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="bb5a9-112">[in] The file stream, used as an alternative to the filename parameter.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb5a9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bb5a9-113">Return Value</span></span>  
 <span data-ttu-id="bb5a9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb5a9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb5a9-115">Remarks</span></span>  
 <span data-ttu-id="bb5a9-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="bb5a9-117">The `searchPath` parameter is optional.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb5a9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb5a9-118">Requirements</span></span>  
 <span data-ttu-id="bb5a9-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bb5a9-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5a9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-120">See also</span></span>

- [<span data-ttu-id="bb5a9-121">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb5a9-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
