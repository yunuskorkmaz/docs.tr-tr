---
title: SetManifestFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445567"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="bc522-102">SetManifestFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc522-102">SetManifestFile Method</span></span>
<span data-ttu-id="bc522-103">Bağlayıcının, derlemeyi oluşturduğunda kullandığı bildirim dosyasını belirtmenize veya sıfırlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc522-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc522-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc522-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc522-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc522-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="bc522-106">İçeriği Win32 kaynakları blobuna yerleştirilen bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="bc522-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc522-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc522-107">Return Value</span></span>  
 <span data-ttu-id="bc522-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc522-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc522-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc522-109">Remarks</span></span>  
 <span data-ttu-id="bc522-110">Win32ResBlob sorulmadan önce bunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="bc522-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="bc522-111">`pszFile` parametresinin değeri, içeriği okunan ve KIMLIĞI RT_MANIFEST olan Win32 kaynaklarına yerleştirilen bildirim dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="bc522-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="bc522-112">NULL parametresi kullanılarak çağrıldığında, daha önce okuma bildirimi temizlenir.</span><span class="sxs-lookup"><span data-stu-id="bc522-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="bc522-113">Bu, bir tane, bağlayıcının durumunu başlatma zamanına sıfırlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc522-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc522-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc522-114">Requirements</span></span>  
 <span data-ttu-id="bc522-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="bc522-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc522-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc522-116">See also</span></span>

- [<span data-ttu-id="bc522-117">IALink3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc522-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="bc522-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="bc522-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="bc522-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc522-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="bc522-120">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="bc522-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
