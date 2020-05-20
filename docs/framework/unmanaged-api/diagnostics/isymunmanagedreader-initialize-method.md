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
ms.openlocfilehash: 07d2de5d12fd769cb5cce243d9e721bb6fc185a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615481"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="9ac68-102">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ac68-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="9ac68-103">Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.</span><span class="sxs-lookup"><span data-stu-id="9ac68-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ac68-104">Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir okuyucu yönteminden önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ac68-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac68-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9ac68-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ac68-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="9ac68-107">'ndaki Bu okuyucunun ilişkilendirileceği meta veri alma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9ac68-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="9ac68-108">'ndaki Modülün dosya adı.</span><span class="sxs-lookup"><span data-stu-id="9ac68-108">[in] The file name of the module.</span></span> <span data-ttu-id="9ac68-109">`pIStream`Bunun yerine parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ac68-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="9ac68-110">'ndaki Arama yolu.</span><span class="sxs-lookup"><span data-stu-id="9ac68-110">[in] The path to search.</span></span> <span data-ttu-id="9ac68-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ac68-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="9ac68-112">'ndaki Dosya akışı, filename parametresine alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ac68-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ac68-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9ac68-113">Return Value</span></span>  
 <span data-ttu-id="9ac68-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9ac68-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac68-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ac68-115">Remarks</span></span>  
 <span data-ttu-id="9ac68-116">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="9ac68-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="9ac68-117">`searchPath`Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ac68-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac68-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ac68-118">Requirements</span></span>  
 <span data-ttu-id="9ac68-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9ac68-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac68-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ac68-120">See also</span></span>

- [<span data-ttu-id="9ac68-121">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ac68-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
