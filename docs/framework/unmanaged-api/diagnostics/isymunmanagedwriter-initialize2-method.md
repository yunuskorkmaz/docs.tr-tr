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
ms.openlocfilehash: 869d7d36ac24bfeee5b2361dd569945ad77eaf7f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610073"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="1ecc8-102">ISymUnmanagedWriter::Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ecc8-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="1ecc8-103">Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="1ecc8-104">Bu yöntem, program veritabanı (PDB) dosyasının son konumunu ayarlamanıza de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ecc8-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1ecc8-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ecc8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ecc8-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="1ecc8-107">'ndaki Meta veri verici arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="1ecc8-108">'ndaki `WCHAR`Hata ayıklama simgelerinin yazıldığı dosya adını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="1ecc8-109">Dosya adları kullanmayan bir yazıcı için dosya adı belirtilmişse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="1ecc8-110">'ndaki Belirtilmişse, sembol yazıcı sembolleri <xref:System.Runtime.InteropServices.ComTypes.IStream> parametresinde belirtilen dosya yerine, belirtilen içine yayar `filename` .</span><span class="sxs-lookup"><span data-stu-id="1ecc8-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="1ecc8-111">`pIStream`Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="1ecc8-112">[in] `true` Bu bir tam yeniden oluşturma ise `false`Bu bir artımlı derleme ise.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="1ecc8-113">'ndaki , `WCHAR` Pdb dosyasının son konumunun yol dizesi olan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ecc8-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ecc8-114">Return Value</span></span>  
 <span data-ttu-id="1ecc8-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ecc8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ecc8-116">Requirements</span></span>  
 <span data-ttu-id="1ecc8-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1ecc8-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ecc8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ecc8-118">See also</span></span>

- [<span data-ttu-id="1ecc8-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ecc8-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="1ecc8-120">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ecc8-120">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)
