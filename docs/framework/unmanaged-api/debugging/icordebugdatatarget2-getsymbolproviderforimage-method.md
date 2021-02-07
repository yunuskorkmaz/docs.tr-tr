---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugDataTarget2:: GetSymbolProviderForImage yöntemi'
title: ICorDebugDataTarget2::GetSymbolProviderForImage Metodu
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7b4493b6c0959dc39d955d7691a22ac6905034b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764391"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="f2cde-103">ICorDebugDataTarget2::GetSymbolProviderForImage Metodu</span><span class="sxs-lookup"><span data-stu-id="f2cde-103">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>

<span data-ttu-id="f2cde-104">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2cde-104">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2cde-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2cde-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2cde-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2cde-106">Parameters</span></span>  

 `imageBaseAddress`  
 <span data-ttu-id="f2cde-107">'ndaki Bir modülün temel adresini temsil eden bir [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="f2cde-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="f2cde-108">dışı [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2cde-108">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2cde-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2cde-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2cde-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2cde-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2cde-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2cde-111">Requirements</span></span>  

 <span data-ttu-id="f2cde-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2cde-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2cde-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f2cde-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2cde-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2cde-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2cde-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2cde-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2cde-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2cde-116">See also</span></span>

- [<span data-ttu-id="f2cde-117">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2cde-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="f2cde-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f2cde-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
