---
title: Bu tek örnekli uygulama özgün örneğe bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198132"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="15d4f-102">Bu tek örnekli uygulama özgün örneğe bağlanamadı</span><span class="sxs-lookup"><span data-stu-id="15d4f-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="15d4f-103">Bu tek örnekli uygulama özgün örneğe bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="15d4f-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="15d4f-104">Bu sorunun olası nedenlerinden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="15d4f-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="15d4f-105">Özgün örnek yanıt vermeyi durdurdu.</span><span class="sxs-lookup"><span data-stu-id="15d4f-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="15d4f-106">Uygulamanın çekirdek nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="15d4f-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="15d4f-107">Çekirdek nesneler hakkında daha fazla bilgi için bkz. zaman [uyumu sağlayıcılar](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="15d4f-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="15d4f-108">Çekirdek nesnelerinin temel adı, derlemenin GUID, ana sürüm numarası ve alt sürüm numarasını birleştirerek alınır.</span><span class="sxs-lookup"><span data-stu-id="15d4f-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="15d4f-109">Örneğin, temel ad `3639f15d-9547-43da-8145-60da347829915.1`olabilir.</span><span class="sxs-lookup"><span data-stu-id="15d4f-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="15d4f-110">Uygulamayı geliştirirken bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="15d4f-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="15d4f-111">Uygulamanın yanıt vermeyen bir duruma gitmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="15d4f-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="15d4f-112">Uygulamanın çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="15d4f-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="15d4f-113">Uygulamanın orijinal örneğini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="15d4f-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="15d4f-114">Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanan herhangi bir işlemi temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="15d4f-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="15d4f-115">Hatanın oluştuğu koşulları ve telefon Microsoft Ürün Destek Hizmetleri ' ni aklınızda yapın.</span><span class="sxs-lookup"><span data-stu-id="15d4f-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d4f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d4f-116">See also</span></span>

- [<span data-ttu-id="15d4f-117">Hata Ayıklayıcısı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="15d4f-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
