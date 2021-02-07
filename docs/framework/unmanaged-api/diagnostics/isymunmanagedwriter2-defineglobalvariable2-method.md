---
description: 'Hakkında daha fazla bilgi edinin: ISymUnmanagedWriter2::D efineGlobalVariable2 yöntemi'
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
ms.openlocfilehash: 9a33ff8d452419ff103c9f4402620bd28196ae54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761908"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="fcee6-103">ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcee6-103">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>

<span data-ttu-id="fcee6-104">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcee6-104">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcee6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcee6-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fcee6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcee6-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="fcee6-107">'ndaki Genel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="fcee6-107">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="fcee6-108">'ndaki Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="fcee6-108">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="fcee6-109">'ndaki İmzanın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="fcee6-109">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="fcee6-110">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="fcee6-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="fcee6-111">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="fcee6-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="fcee6-112">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="fcee6-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="fcee6-113">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="fcee6-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcee6-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fcee6-114">Return Value</span></span>  

 <span data-ttu-id="fcee6-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fcee6-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcee6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcee6-116">Requirements</span></span>  

 <span data-ttu-id="fcee6-117">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="fcee6-117">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcee6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcee6-118">See also</span></span>

- [<span data-ttu-id="fcee6-119">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcee6-119">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="fcee6-120">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcee6-120">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
