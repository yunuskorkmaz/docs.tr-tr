---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093622"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="8d36c-101">Null coalescer değerleri daha sonra bir adım kadar hata ayıklayıcıda görünür değildir</span><span class="sxs-lookup"><span data-stu-id="8d36c-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8d36c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8d36c-102">Details</span></span>|<span data-ttu-id="8d36c-103">.NET Framework 4.5 hatada atama işlemi Framework'ün 64 bit sürümünde çalıştırıldığı sırada yürütüldükten hemen sonra hata ayıklayıcısı'nda görünür olmaması için null bir birleştirme işlemi ayarlanan değerleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="8d36c-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="8d36c-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="8d36c-104">Suggestion</span></span>|<span data-ttu-id="8d36c-105">Hata ayıklayıcı ek bir kerelik atlama doğru şekilde güncelleştirilmesi, yerel/alanın değeri neden olur.</span><span class="sxs-lookup"><span data-stu-id="8d36c-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="8d36c-106">Ayrıca, .NET Framework 4. 6 ' Bu sorun düzeltilmiştir; Framework'ün bu sürüme yükseltme sorunu çözecektir.</span><span class="sxs-lookup"><span data-stu-id="8d36c-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="8d36c-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8d36c-107">Scope</span></span>|<span data-ttu-id="8d36c-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="8d36c-108">Edge</span></span>|
|<span data-ttu-id="8d36c-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8d36c-109">Version</span></span>|<span data-ttu-id="8d36c-110">4,5</span><span class="sxs-lookup"><span data-stu-id="8d36c-110">4.5</span></span>|
|<span data-ttu-id="8d36c-111">Tür</span><span class="sxs-lookup"><span data-stu-id="8d36c-111">Type</span></span>|<span data-ttu-id="8d36c-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8d36c-112">Runtime</span></span>|
