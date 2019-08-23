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
ms.openlocfilehash: f2dceeb2f0b3aa9f3147157e77087dffbf2d5f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939021"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="47e36-102">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47e36-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="47e36-103">Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.</span><span class="sxs-lookup"><span data-stu-id="47e36-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47e36-104">Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir okuyucu yönteminden önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47e36-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47e36-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47e36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47e36-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="47e36-107">'ndaki Bu okuyucunun ilişkilendirileceği meta veri alma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="47e36-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="47e36-108">'ndaki Modülün dosya adı.</span><span class="sxs-lookup"><span data-stu-id="47e36-108">[in] The file name of the module.</span></span> <span data-ttu-id="47e36-109">Bunun yerine `pIStream` parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47e36-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="47e36-110">'ndaki Arama yolu.</span><span class="sxs-lookup"><span data-stu-id="47e36-110">[in] The path to search.</span></span> <span data-ttu-id="47e36-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="47e36-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="47e36-112">'ndaki Dosya akışı, filename parametresine alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47e36-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47e36-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47e36-113">Return Value</span></span>  
 <span data-ttu-id="47e36-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAıL veya diğer bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="47e36-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47e36-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47e36-115">Remarks</span></span>  
 <span data-ttu-id="47e36-116">`filename` Ya`pIStream` da parametrelerinden yalnızca birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47e36-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="47e36-117">`searchPath` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="47e36-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e36-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47e36-118">Requirements</span></span>  
 <span data-ttu-id="47e36-119">**Üst bilgi** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="47e36-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e36-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e36-120">See also</span></span>

- [<span data-ttu-id="47e36-121">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47e36-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
