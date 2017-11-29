---
title: "ISymUnmanagedWriter::Initialize Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="28997-102">ISymUnmanagedWriter::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28997-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="28997-103">İle bu yazıcısı ilişkili olacağı meta verileri verici arabirimi ayarlar ve hata ayıklama simgeleri yazılacak çıktı dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="28997-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="28997-104">Bu yöntemi yalnızca bir kez çağrılabilir ve herhangi bir yazıcı yöntem önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28997-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="28997-105">Bazı yazıcıları bir dosya adı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="28997-105">Some writers may require a file name.</span></span> <span data-ttu-id="28997-106">Ancak, bu yönteme dosya adını kullanmayın yazıcılarının negatif herhangi bir etkisi olmadan her zaman bir dosya adı geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28997-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28997-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28997-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28997-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28997-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="28997-109">[in] Meta veri verici arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="28997-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="28997-110">[in] Hata ayıklama simgeleri yazılmış olan dosya adı.</span><span class="sxs-lookup"><span data-stu-id="28997-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="28997-111">Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="28997-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="28997-112">[in] Belirtilmişse, simge yazan simgeleri yayma verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="28997-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="28997-113">`pIStream` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="28997-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="28997-114">[in] `true` bu tam bir yeniden oluşturma; ise `false` bu artımlı bir derleme ise.</span><span class="sxs-lookup"><span data-stu-id="28997-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28997-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28997-115">Return Value</span></span>  
 <span data-ttu-id="28997-116">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="28997-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28997-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28997-117">Requirements</span></span>  
 <span data-ttu-id="28997-118">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28997-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28997-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28997-119">See Also</span></span>  
 [<span data-ttu-id="28997-120">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="28997-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="28997-121">Initialize2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="28997-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
