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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 661c27b9c21f77104b8a86163d3c92d44f8a85df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181785"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="e32d0-102">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e32d0-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="e32d0-103">Bu okuyucu modülü dosya adının yanı sıra, ile ilişkili meta verileri alma arabirimiyle sembol okuyucu başlatır.</span><span class="sxs-lookup"><span data-stu-id="e32d0-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e32d0-104">Bu yöntem yalnızca bir kez çağrılabilir ve diğer okuyucu yöntemleri önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e32d0-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e32d0-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e32d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e32d0-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e32d0-107">[in] İle bu okuyucu ilişkilendirilecek olan meta verileri alma arabirim.</span><span class="sxs-lookup"><span data-stu-id="e32d0-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="e32d0-108">[in] Modül dosya adı.</span><span class="sxs-lookup"><span data-stu-id="e32d0-108">[in] The file name of the module.</span></span> <span data-ttu-id="e32d0-109">Kullanabileceğiniz `pIStream` parametresi yerine.</span><span class="sxs-lookup"><span data-stu-id="e32d0-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="e32d0-110">[in] Arama yolu.</span><span class="sxs-lookup"><span data-stu-id="e32d0-110">[in] The path to search.</span></span> <span data-ttu-id="e32d0-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e32d0-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="e32d0-112">[in] Filename parametresi bir alternatif olarak kullanılan dosya akışı.</span><span class="sxs-lookup"><span data-stu-id="e32d0-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e32d0-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e32d0-113">Return Value</span></span>  
 <span data-ttu-id="e32d0-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e32d0-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e32d0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e32d0-115">Remarks</span></span>  
 <span data-ttu-id="e32d0-116">Yalnızca birini belirtmeniz gereken `filename` veya `pIStream` parametreleri, her ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="e32d0-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="e32d0-117">`searchPath` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e32d0-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e32d0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e32d0-118">Requirements</span></span>  
 <span data-ttu-id="e32d0-119">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e32d0-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32d0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e32d0-120">See also</span></span>

- [<span data-ttu-id="e32d0-121">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e32d0-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
