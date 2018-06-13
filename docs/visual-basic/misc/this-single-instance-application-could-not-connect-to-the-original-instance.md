---
title: Bu tek örnekli uygulama özgün örneğe bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 9bc1f33231cc4f29fabd100a695843beb334aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640260"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="34efb-102">Bu tek örnekli uygulama özgün örneğe bağlanamadı</span><span class="sxs-lookup"><span data-stu-id="34efb-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="34efb-103">Bu tek örnekli uygulama özgün örneğine bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="34efb-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="34efb-104">Bu sorunun olası nedeni bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="34efb-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="34efb-105">Orijinal örnek yanıt vermeyi durdurdu.</span><span class="sxs-lookup"><span data-stu-id="34efb-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="34efb-106">Uygulama çekirdek nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="34efb-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="34efb-107">Çekirdek nesneleri hakkında daha fazla bilgi için bkz: [zaman uyumu sağlayıcılar](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="34efb-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="34efb-108">Derleme GUID, ana sürüm numarası ve ikincil sürüm numarası birleştirme çekirdek nesneleri için temel adı gelir.</span><span class="sxs-lookup"><span data-stu-id="34efb-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="34efb-109">Örneğin, bir taban adına olabilir `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="34efb-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="34efb-110">Uygulama geliştirirken, bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="34efb-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="34efb-111">Uygulama yanıt vermeyen bir duruma geçmez denetleyin.</span><span class="sxs-lookup"><span data-stu-id="34efb-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="34efb-112">Uygulama çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="34efb-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="34efb-113">Özgün uygulama örneğini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="34efb-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="34efb-114">Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="34efb-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="34efb-115">Hata oluştuğu durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri telefon.</span><span class="sxs-lookup"><span data-stu-id="34efb-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34efb-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34efb-116">See Also</span></span>  
 [<span data-ttu-id="34efb-117">Hata ayıklayıcı temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="34efb-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  

