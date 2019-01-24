---
title: Bu tek örnekli uygulama özgün örneğine bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 80c1ec0bf1aa4b6dbf885294c680b3bfe8897eac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565715"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="ad50a-102">Bu tek örnekli uygulama özgün örneğine bağlanamadı</span><span class="sxs-lookup"><span data-stu-id="ad50a-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="ad50a-103">Bu tek örnekli uygulama özgün örneğine bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="ad50a-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="ad50a-104">Bu sorunun olası nedeni bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ad50a-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="ad50a-105">Özgün örneğe yanıt vermeyi durdurdu.</span><span class="sxs-lookup"><span data-stu-id="ad50a-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="ad50a-106">Uygulama, çekirdek nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="ad50a-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="ad50a-107">Çekirdek nesneleri hakkında daha fazla bilgi için bkz. [mutex'ler](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="ad50a-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="ad50a-108">Derlemenin GUID, ana sürüm numarası ve küçük versiyon numarasını birleştirerek çekirdek nesneler için taban adı gelir.</span><span class="sxs-lookup"><span data-stu-id="ad50a-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="ad50a-109">Örneğin, temel adı olabilir `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="ad50a-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="ad50a-110">Uygulama geliştirirken, bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ad50a-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="ad50a-111">Uygulama bir yanıt veremez duruma geçmez denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ad50a-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="ad50a-112">Uygulama çekirdek nesneleri oluşturmak için yeterli izinlere sahip olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ad50a-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="ad50a-113">Özgün uygulama örneğini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="ad50a-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="ad50a-114">Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="ad50a-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="ad50a-115">Altında hatanın gerçekleştiği durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri telefon.</span><span class="sxs-lookup"><span data-stu-id="ad50a-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad50a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad50a-116">See also</span></span>
- [<span data-ttu-id="ad50a-117">Hata Ayıklayıcısı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="ad50a-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)

