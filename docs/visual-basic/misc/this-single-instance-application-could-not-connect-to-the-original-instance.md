---
title: "Bu tek örnekli uygulama özgün örneğe bağlanamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="e8109-102">Bu tek örnekli uygulama özgün örneğe bağlanamadı</span><span class="sxs-lookup"><span data-stu-id="e8109-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="e8109-103">Bu tek örnekli uygulama özgün örneğine bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="e8109-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="e8109-104">Bu sorunun olası nedeni bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8109-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="e8109-105">Orijinal örnek yanıt vermeyi durdurdu.</span><span class="sxs-lookup"><span data-stu-id="e8109-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="e8109-106">Uygulama çekirdek nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="e8109-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="e8109-107">Çekirdek nesneleri hakkında daha fazla bilgi için bkz: [zaman uyumu sağlayıcılar](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="e8109-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="e8109-108">Derleme GUID, ana sürüm numarası ve ikincil sürüm numarası birleştirme çekirdek nesneleri için temel adı gelir.</span><span class="sxs-lookup"><span data-stu-id="e8109-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="e8109-109">Örneğin, bir taban adına olabilir `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="e8109-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="e8109-110">Uygulama geliştirirken, bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e8109-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="e8109-111">Uygulama yanıt vermeyen bir duruma geçmez denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e8109-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="e8109-112">Uygulama çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e8109-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="e8109-113">Özgün uygulama örneğini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="e8109-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="e8109-114">Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="e8109-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="e8109-115">Hata oluştuğu durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri telefon.</span><span class="sxs-lookup"><span data-stu-id="e8109-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8109-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8109-116">See Also</span></span>  
 [<span data-ttu-id="e8109-117">NIB: Nasıl yapılır: bir uygulama (Visual Basic) davranışı depolamasına belirtin</span><span class="sxs-lookup"><span data-stu-id="e8109-117">NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)</span></span>](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [<span data-ttu-id="e8109-118">Hata ayıklayıcı temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="e8109-118">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="e8109-119">PAVEOVER ürün desteği ve erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="e8109-119">PAVEOVER Product Support and Accessibility</span></span>](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
