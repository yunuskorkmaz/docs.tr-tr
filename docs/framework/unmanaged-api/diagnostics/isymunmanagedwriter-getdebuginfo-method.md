---
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
ms.openlocfilehash: dcab63b603d4a9a8e1430228043d2a5e597bbf4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678298"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="8ea3e-102">ISymUnmanagedWriter::GetDebugInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>

<span data-ttu-id="8ea3e-103">Bir derleyicinin taşınabilir yürütülebilir (PE) dosya üstbilgisine hata ayıklama dizini girişini yazması için gereken bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="8ea3e-104">Sembol yazıcı, ve hariç tüm alanları doldurur `TimeDateStamp` `PointerToRawData` .</span><span class="sxs-lookup"><span data-stu-id="8ea3e-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="8ea3e-105">(Derleyici, bu iki alanı uygun şekilde ayarlamaktan sorumludur.)</span><span class="sxs-lookup"><span data-stu-id="8ea3e-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="8ea3e-106">Bir derleyici bu yöntemi çağırmalıdır, veri blobunu PE dosyasına yayar, IMAGE_DEBUG_DIRECTORY alanı, yayan `PointerToRawData` verileri gösterecek şekilde ayarlayın ve IMAGE_DEBUG_DIRECTORY pe dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="8ea3e-107">Derleyici Ayrıca `TimeDateStamp` alanı oluşturulan PE dosyasının değerine eşit olacak şekilde ayarlamış olmalıdır `TimeDateStamp` .</span><span class="sxs-lookup"><span data-stu-id="8ea3e-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea3e-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ea3e-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ea3e-109">Parameters</span></span>  

 `pIDD`  
 <span data-ttu-id="8ea3e-110">[in, out] Sembol yazıcısının dolduracağı IMAGE_DEBUG_DIRECTORY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="8ea3e-111">'ndaki `DWORD` Hata ayıklama verilerinin boyutunu içeren bir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="8ea3e-112">dışı `DWORD` Hata ayıklama verilerini içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="8ea3e-113">dışı Simge deposu için hata ayıklama verilerini tutabilecek kadar büyük bir arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ea3e-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ea3e-114">Return Value</span></span>  

 <span data-ttu-id="8ea3e-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ea3e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ea3e-116">Requirements</span></span>  

 <span data-ttu-id="8ea3e-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8ea3e-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea3e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-118">See also</span></span>

- [<span data-ttu-id="8ea3e-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
