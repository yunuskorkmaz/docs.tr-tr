---
title: Barındırma Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
ms.openlocfilehash: 9d0349e4801c550731b6d126197003917c4a46e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721796"
---
# <a name="hosting-structures"></a><span data-ttu-id="b05c4-102">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="b05c4-102">Hosting Structures</span></span>

<span data-ttu-id="b05c4-103">Bu bölümde, barındırma API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b05c4-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b05c4-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b05c4-104">In This Section</span></span>  

 [<span data-ttu-id="b05c4-105">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-105">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)  
 <span data-ttu-id="b05c4-106">Başvurulan derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="b05c4-107">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-107">BucketParameters Structure</span></span>](bucketparameters-structure.md)  
 <span data-ttu-id="b05c4-108">Bir olayın tür adını ve olayla ilişkili geçerli özel durumun parametrelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="b05c4-109">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-109">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)  
 <span data-ttu-id="b05c4-110">Ortak dil çalışma zamanının (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="b05c4-111">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-111">COR_GC_THREAD_STATS Structure</span></span>](cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="b05c4-112">Çöp toplamadan ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b05c4-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="b05c4-113">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-113">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)  
 <span data-ttu-id="b05c4-114">Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="b05c4-115">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-115">MDAInfo Structure</span></span>](mdainfo-structure.md)  
 <span data-ttu-id="b05c4-116">`Event_MDAFired`Yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayla ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="b05c4-117">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-117">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)  
 <span data-ttu-id="b05c4-118">Başvurulan modül ve onu içeren derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="b05c4-119">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="b05c4-119">StackOverflowInfo Structure</span></span>](stackoverflowinfo-structure.md)  
 <span data-ttu-id="b05c4-120">Oluşan taşma türünü ve taşma nedeniyle oluşan özel durum hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="b05c4-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b05c4-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b05c4-121">Related Sections</span></span>  

 [<span data-ttu-id="b05c4-122">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="b05c4-122">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="b05c4-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b05c4-123">Hosting Interfaces</span></span>](hosting-interfaces.md)  
  
 [<span data-ttu-id="b05c4-124">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b05c4-124">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="b05c4-125">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b05c4-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
