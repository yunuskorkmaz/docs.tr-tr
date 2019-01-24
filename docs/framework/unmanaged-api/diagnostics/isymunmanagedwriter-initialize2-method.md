---
title: ISymUnmanagedWriter::Initialize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f65262a9b9850d93e934a77f154bb625a55e1e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514250"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="862a1-102">ISymUnmanagedWriter::Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="862a1-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="862a1-103">İle bu yazıcısı ilişkilendirilecek olan meta veri verici arabirimi ayarlar ve hata ayıklama sembolleri yazılacağı çıktı dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="862a1-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="862a1-104">Bu yöntem Ayrıca, program veritabanı (PDB) dosyasının son konum ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="862a1-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="862a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="862a1-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="862a1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="862a1-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="862a1-107">[in] Meta veri verici arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="862a1-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="862a1-108">[in] Bir işaretçi bir `WCHAR` hata ayıklama sembolleri yazılır dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="862a1-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="862a1-109">Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="862a1-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="862a1-110">[in] Belirtilmişse sembolleri sembol yazıcı yayan verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="862a1-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="862a1-111">`pIStream` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="862a1-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="862a1-112">[in] `true` bu tam yeniden derleme; ise `false` bu artımlı bir derleme ise.</span><span class="sxs-lookup"><span data-stu-id="862a1-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="862a1-113">[in] Bir işaretçi bir `WCHAR` diğer bir deyişle yol dizesi PDB dosyası son konumunu.</span><span class="sxs-lookup"><span data-stu-id="862a1-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="862a1-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="862a1-114">Return Value</span></span>  
 <span data-ttu-id="862a1-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="862a1-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="862a1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="862a1-116">Requirements</span></span>  
 <span data-ttu-id="862a1-117">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="862a1-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="862a1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="862a1-118">See also</span></span>
- [<span data-ttu-id="862a1-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="862a1-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="862a1-120">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="862a1-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
