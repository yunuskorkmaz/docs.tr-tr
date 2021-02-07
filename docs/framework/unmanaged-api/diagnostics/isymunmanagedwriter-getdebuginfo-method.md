---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: GetDebugInfo yöntemi'
title: ISymUnmanagedWriter::GetDebugInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: 2255cc90c0bfcd36dacdf81703af67d3f47739db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762324"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="921bb-103">ISymUnmanagedWriter::GetDebugInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="921bb-103">ISymUnmanagedWriter::GetDebugInfo Method</span></span>

<span data-ttu-id="921bb-104">Bir derleyicinin taşınabilir yürütülebilir (PE) dosya üstbilgisine hata ayıklama dizini girişini yazması için gereken bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="921bb-104">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="921bb-105">Sembol yazıcı, ve hariç tüm alanları doldurur `TimeDateStamp` `PointerToRawData` .</span><span class="sxs-lookup"><span data-stu-id="921bb-105">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="921bb-106">(Derleyici, bu iki alanı uygun şekilde ayarlamaktan sorumludur.)</span><span class="sxs-lookup"><span data-stu-id="921bb-106">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="921bb-107">Bir derleyici bu yöntemi çağırmalıdır, veri blobunu PE dosyasına yayar, IMAGE_DEBUG_DIRECTORY alanı, yayan `PointerToRawData` verileri gösterecek şekilde ayarlayın ve IMAGE_DEBUG_DIRECTORY pe dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="921bb-107">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="921bb-108">Derleyici Ayrıca `TimeDateStamp` alanı oluşturulan PE dosyasının değerine eşit olacak şekilde ayarlamış olmalıdır `TimeDateStamp` .</span><span class="sxs-lookup"><span data-stu-id="921bb-108">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="921bb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="921bb-109">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="921bb-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="921bb-110">Parameters</span></span>  

 `pIDD`  
 <span data-ttu-id="921bb-111">[in, out] Sembol yazıcısının dolduracağı IMAGE_DEBUG_DIRECTORY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="921bb-111">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="921bb-112">'ndaki `DWORD` Hata ayıklama verilerinin boyutunu içeren bir.</span><span class="sxs-lookup"><span data-stu-id="921bb-112">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="921bb-113">dışı `DWORD` Hata ayıklama verilerini içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="921bb-113">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="921bb-114">dışı Simge deposu için hata ayıklama verilerini tutabilecek kadar büyük bir arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="921bb-114">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="921bb-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="921bb-115">Return Value</span></span>  

 <span data-ttu-id="921bb-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="921bb-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="921bb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="921bb-117">Requirements</span></span>  

 <span data-ttu-id="921bb-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="921bb-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921bb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="921bb-119">See also</span></span>

- [<span data-ttu-id="921bb-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="921bb-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
