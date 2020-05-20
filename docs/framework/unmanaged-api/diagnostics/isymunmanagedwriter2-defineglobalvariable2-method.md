---
title: ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: ed3c841c34b71b30f740117899353aa289e478d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614714"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="3f3e8-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f3e8-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="3f3e8-103">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3e8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3f3e8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f3e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f3e8-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3f3e8-106">'ndaki Genel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="3f3e8-107">'ndaki Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="3f3e8-108">'ndaki İmzanın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="3f3e8-109">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="3f3e8-110">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="3f3e8-111">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="3f3e8-112">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f3e8-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f3e8-113">Return Value</span></span>  
 <span data-ttu-id="3f3e8-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3e8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f3e8-115">Requirements</span></span>  
 <span data-ttu-id="3f3e8-116">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="3f3e8-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3e8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f3e8-117">See also</span></span>

- [<span data-ttu-id="3f3e8-118">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f3e8-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="3f3e8-119">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f3e8-119">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
