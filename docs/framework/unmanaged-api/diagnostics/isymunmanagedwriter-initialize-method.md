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
ms.openlocfilehash: 417cf623948d16147f9a1242d714f4df1311a314
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700949"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="33370-102">ISymUnmanagedWriter::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33370-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="33370-103">İle bu yazıcısı ilişkilendirilecek olan meta veri verici arabirimi ayarlar ve hata ayıklama sembolleri yazılacağı çıktı dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33370-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="33370-104">Bu yöntem yalnızca bir kez çağrılabilir ve diğer yazıcısı metotlarını önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33370-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="33370-105">Bazı yazarları, bir dosya adı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="33370-105">Some writers may require a file name.</span></span> <span data-ttu-id="33370-106">Ancak, bu yönteme dosya adını kullanmayın yazıcılar negatif herhangi bir etkisi olmadan her zaman bir dosya adı geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33370-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33370-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33370-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33370-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33370-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="33370-109">[in] Meta veri verici arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="33370-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="33370-110">[in] Hata ayıklama sembolleri yazıldığı dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="33370-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="33370-111">Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="33370-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="33370-112">[in] Belirtilmişse, simge yazıcı sembolleri yayar verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="33370-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="33370-113">`pIStream` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="33370-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="33370-114">[in] `true` bu tam yeniden derleme; ise `false` bu artımlı bir derleme ise.</span><span class="sxs-lookup"><span data-stu-id="33370-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33370-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="33370-115">Return Value</span></span>  
 <span data-ttu-id="33370-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="33370-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33370-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33370-117">Requirements</span></span>  
 <span data-ttu-id="33370-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33370-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33370-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33370-119">See also</span></span>

- [<span data-ttu-id="33370-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33370-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="33370-121">Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33370-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
