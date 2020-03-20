---
title: Geri Çağırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181512"
---
# <a name="callback-functions"></a><span data-ttu-id="a0d07-102">Geri Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a0d07-102">Callback Functions</span></span>
<span data-ttu-id="a0d07-103">Geri arama işlevi, yönetilmeyen bir DLL işlevinin görevi tamamlamasına yardımcı olan yönetilen bir uygulama içindeki koddur.</span><span class="sxs-lookup"><span data-stu-id="a0d07-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="a0d07-104">Geri arama işlevine yapılan çağrılar, yönetilen bir uygulamadan, Bir DLL işlevi aracılığıyla ve yönetilen uygulamaya dolaylı olarak geçer.</span><span class="sxs-lookup"><span data-stu-id="a0d07-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="a0d07-105">Platform çağrıcağı ile çağrılan birçok DLL işlevinden bazıları, düzgün çalışması için yönetilen kodda bir geri arama işlevi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a0d07-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="a0d07-106">Yönetilen koddan çoğu DLL işlevini çağırmak için, işlevin yönetilen bir tanımını oluşturun ve sonra onu çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="a0d07-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="a0d07-107">İşlem basittir.</span><span class="sxs-lookup"><span data-stu-id="a0d07-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="a0d07-108">Geri arama işlevi gerektiren bir DLL işlevinin kullanılmasının bazı ek adımları vardır.</span><span class="sxs-lookup"><span data-stu-id="a0d07-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="a0d07-109">İlk olarak, işlev için belgelere bakarak işlevin bir geri arama gerektirip gerektirmediğini belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d07-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="a0d07-110">Ardından, yönetilen uygulamanızda geri arama işlevini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d07-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="a0d07-111">Son olarak, dll işlevini çağırın, bir işaretçiyi bağımsız değişken olarak geri arama işlevine geçersiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d07-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="a0d07-112">Aşağıdaki resimde geri arama işlevi ve uygulama adımları özetlenebilir:</span><span class="sxs-lookup"><span data-stu-id="a0d07-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Platformu gösteren diyagram geri arama işlemini çağırır.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="a0d07-114">Geri arama işlevleri, görevin tekrar tekrar gerçekleştirildiği durumlarda kullanım için idealdir.</span><span class="sxs-lookup"><span data-stu-id="a0d07-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="a0d07-115">Başka bir yaygın kullanım numaralandırma fonksiyonları ile, **EnumFontFamilies**gibi , **EnumPrinters** **,** windows API.</span><span class="sxs-lookup"><span data-stu-id="a0d07-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="a0d07-116">**EnumWindows** işlevi bilgisayarınızdaki varolan tüm pencerelerden birime direnerek, her pencerede bir görevi gerçekleştirmek için geri arama işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a0d07-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="a0d07-117">Yönergeler ve bir örnek için [bkz.](how-to-implement-callback-functions.md)</span><span class="sxs-lookup"><span data-stu-id="a0d07-117">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d07-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0d07-118">See also</span></span>

- [<span data-ttu-id="a0d07-119">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="a0d07-119">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="a0d07-120">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="a0d07-120">Calling a DLL Function</span></span>](calling-a-dll-function.md)
