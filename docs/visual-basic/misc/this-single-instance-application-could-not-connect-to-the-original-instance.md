---
title: Bu tek örnekli uygulama özgün örneğe bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 8e2caa158c3874d216671979430a03b11bf60066
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095687"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="20761-102">Bu tek örnekli uygulama özgün örneğe bağlanamadı</span><span class="sxs-lookup"><span data-stu-id="20761-102">This single-instance application could not connect to the original instance</span></span>

<span data-ttu-id="20761-103">Bu tek örnekli uygulama özgün örneğe bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="20761-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="20761-104">Bu sorunun olası nedenlerinden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="20761-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="20761-105">Özgün örnek yanıt vermeyi durdurdu.</span><span class="sxs-lookup"><span data-stu-id="20761-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="20761-106">Uygulamanın çekirdek nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="20761-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="20761-107">Çekirdek nesneler hakkında daha fazla bilgi için bkz. zaman [uyumu sağlayıcılar](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="20761-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="20761-108">Çekirdek nesnelerinin temel adı, derlemenin GUID, ana sürüm numarası ve alt sürüm numarasını birleştirerek alınır.</span><span class="sxs-lookup"><span data-stu-id="20761-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="20761-109">Örneğin, taban adı olabilir `3639f15d-9547-43da-8145-60da347829915.1` .</span><span class="sxs-lookup"><span data-stu-id="20761-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="20761-110">Uygulamayı geliştirirken bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="20761-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="20761-111">Uygulamanın yanıt vermeyen bir duruma gitmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="20761-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="20761-112">Uygulamanın çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="20761-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="20761-113">Uygulamanın orijinal örneğini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="20761-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="20761-114">Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanan herhangi bir işlemi temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="20761-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="20761-115">Hatanın oluştuğu koşulları ve telefon Microsoft Ürün Destek Hizmetleri ' ni aklınızda yapın.</span><span class="sxs-lookup"><span data-stu-id="20761-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20761-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20761-116">See also</span></span>

- [<span data-ttu-id="20761-117">Hata Ayıklayıcı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="20761-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
