---
title: ICorDebugFunction::GetILCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetILCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da955f6eb8e7480fb23192e1a77341166dd40f3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="2ef1e-102">ICorDebugFunction::GetILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="2ef1e-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="2ef1e-103">Bu ICorDebugFunction nesneyle ilişkili Microsoft Ara dili (MSIL) kodunu temsil eder Icordebugcode örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ef1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ef1e-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ef1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ef1e-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="2ef1e-106">[out] Bir işaretçi `ICorDebugCode` örneği veya işlev MSIL derlenmemiş yoksa null.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ef1e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ef1e-107">Remarks</span></span>  
 <span data-ttu-id="2ef1e-108">Düzenle ve devam et izin veriyorsa bu işlevi üzerinde `GetILCode` yöntemi, bu işlevin düzenlenen ortak dil çalışma zamanı (CLR) kodda sürümüne karşılık gelen MSIL kodu alırsınız.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ef1e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ef1e-109">Requirements</span></span>  
 <span data-ttu-id="2ef1e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ef1e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ef1e-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ef1e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ef1e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ef1e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ef1e-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ef1e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
