---
title: ISymUnmanagedWriter::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428041"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="df1c8-102">ISymUnmanagedWriter::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df1c8-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="df1c8-103">İle bu yazıcısı ilişkili olacağı meta verileri verici arabirimi ayarlar ve hata ayıklama simgeleri yazılacak çıktı dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="df1c8-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="df1c8-104">Bu yöntemi yalnızca bir kez çağrılabilir ve herhangi bir yazıcı yöntem önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df1c8-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="df1c8-105">Bazı yazıcıları bir dosya adı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="df1c8-105">Some writers may require a file name.</span></span> <span data-ttu-id="df1c8-106">Ancak, bu yönteme dosya adını kullanmayın yazıcılarının negatif herhangi bir etkisi olmadan her zaman bir dosya adı geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df1c8-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1c8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df1c8-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df1c8-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df1c8-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="df1c8-109">[in] Meta veri verici arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="df1c8-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="df1c8-110">[in] Hata ayıklama simgeleri yazılmış olan dosya adı.</span><span class="sxs-lookup"><span data-stu-id="df1c8-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="df1c8-111">Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="df1c8-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="df1c8-112">[in] Belirtilmişse, simge yazan simgeleri yayma verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="df1c8-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="df1c8-113">`pIStream` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="df1c8-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="df1c8-114">[in] `true` bu tam bir yeniden oluşturma; ise `false` bu artımlı bir derleme ise.</span><span class="sxs-lookup"><span data-stu-id="df1c8-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df1c8-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="df1c8-115">Return Value</span></span>  
 <span data-ttu-id="df1c8-116">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="df1c8-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df1c8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df1c8-117">Requirements</span></span>  
 <span data-ttu-id="df1c8-118">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df1c8-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1c8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df1c8-119">See Also</span></span>  
 [<span data-ttu-id="df1c8-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df1c8-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="df1c8-121">Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df1c8-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
