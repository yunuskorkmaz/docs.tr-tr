---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: Initialize yöntemi'
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
ms.openlocfilehash: cf7f5df3efed7823fc36bd6c9fc56e0c49d17443
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763884"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="77f57-103">ISymUnmanagedReader::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77f57-103">ISymUnmanagedReader::Initialize Method</span></span>

<span data-ttu-id="77f57-104">Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.</span><span class="sxs-lookup"><span data-stu-id="77f57-104">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f57-105">Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir okuyucu yönteminden önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77f57-105">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f57-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77f57-106">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77f57-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77f57-107">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="77f57-108">'ndaki Bu okuyucunun ilişkilendirileceği meta veri alma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="77f57-108">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="77f57-109">'ndaki Modülün dosya adı.</span><span class="sxs-lookup"><span data-stu-id="77f57-109">[in] The file name of the module.</span></span> <span data-ttu-id="77f57-110">`pIStream`Bunun yerine parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77f57-110">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="77f57-111">'ndaki Arama yolu.</span><span class="sxs-lookup"><span data-stu-id="77f57-111">[in] The path to search.</span></span> <span data-ttu-id="77f57-112">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="77f57-112">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="77f57-113">'ndaki Dosya akışı, filename parametresine alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77f57-113">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77f57-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77f57-114">Return Value</span></span>  

 <span data-ttu-id="77f57-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="77f57-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77f57-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77f57-116">Remarks</span></span>  

 <span data-ttu-id="77f57-117">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="77f57-117">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="77f57-118">`searchPath`Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="77f57-118">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f57-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77f57-119">Requirements</span></span>  

 <span data-ttu-id="77f57-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="77f57-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f57-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77f57-121">See also</span></span>

- [<span data-ttu-id="77f57-122">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77f57-122">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
