---
description: 'Daha fazla bilgi edinin: GetWin32ResBlob yöntemi'
title: GetWin32ResBlob Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: e1140b14bfba56dfac03c443a537d6d2188575b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718271"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="20e62-103">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="20e62-103">GetWin32ResBlob Method</span></span>

<span data-ttu-id="20e62-104">Win32 kaynak blobu alır.</span><span class="sxs-lookup"><span data-stu-id="20e62-104">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="20e62-105">Derleme seçeneklerini ayarladıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="20e62-105">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e62-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20e62-106">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="20e62-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20e62-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="20e62-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="20e62-108">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="20e62-109">Win32 sürüm kaynağı oluşturulurken kullanılacak dosya adını almak için kullanılan dosya belirteci</span><span class="sxs-lookup"><span data-stu-id="20e62-109">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="20e62-110">Dosya DLL ise TRUE, bir EXE için false.</span><span class="sxs-lookup"><span data-stu-id="20e62-110">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="20e62-111">Kaynak blobuna eklenecek isteğe bağlı simge.</span><span class="sxs-lookup"><span data-stu-id="20e62-111">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="20e62-112">Kaynak blobu alır.</span><span class="sxs-lookup"><span data-stu-id="20e62-112">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="20e62-113">Blobun boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="20e62-113">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20e62-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20e62-114">Return Value</span></span>  

 <span data-ttu-id="20e62-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e62-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e62-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20e62-116">Requirements</span></span>  

 <span data-ttu-id="20e62-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="20e62-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e62-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20e62-118">See also</span></span>

- [<span data-ttu-id="20e62-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20e62-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="20e62-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20e62-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="20e62-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="20e62-121">ALink API</span></span>](index.md)
