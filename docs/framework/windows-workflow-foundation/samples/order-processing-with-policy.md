---
title: İlke ile sipariş işleme
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: b927d8e7090f96b22c0510f9651070ab999c91be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398376"
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="e88f4-102">İlke ile sipariş işleme</span><span class="sxs-lookup"><span data-stu-id="e88f4-102">Order Processing with Policy</span></span>
<span data-ttu-id="e88f4-103">Sipariş işleme ilkesi örnek sunulan önemli özelliklerinden bazıları gösterilmektedir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="e88f4-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="e88f4-104">Aşağıdaki işlevleri WF kurallar altyapısı için yenidir:</span><span class="sxs-lookup"><span data-stu-id="e88f4-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="e88f4-105">İşleç aşırı yüklemesi için destek.</span><span class="sxs-lookup"><span data-stu-id="e88f4-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="e88f4-106">Destek `new` vererek yeni nesneler ve diziler WF kuralları oluşturmak işleç.</span><span class="sxs-lookup"><span data-stu-id="e88f4-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="e88f4-107">Kullanıcı deneyimini WF kurallardan genişletme yöntemlerini çağırma kodlama stilleri ile C# uyumlu hale getirmek genişletme yöntemleri için destek.</span><span class="sxs-lookup"><span data-stu-id="e88f4-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e88f4-108">Bu örnek gerektiren [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] derlemek ve çalıştırmak için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e88f4-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="e88f4-109"> Proje ve çözüm dosyaları açmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e88f4-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="e88f4-110">Örnek gösterir bir `OrderProcessingPolicy` proje numaralandırılmış bir kullanılabilir öğeleri ve bir posta kodu listesinden oluşur, bir müşteri sipariş girilir.</span><span class="sxs-lookup"><span data-stu-id="e88f4-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="e88f4-111">İki girişin doğruysa sipariş başarıyla işlendi; Aksi takdirde, ilkeyi kullanan aşırı yüklenmiş bir hata nesneleri oluşturur `+` işleci ve önceden tanımlanmış bir uzantı yöntemi hataları kullanıcıyı bilgilendirmek üzere.</span><span class="sxs-lookup"><span data-stu-id="e88f4-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e88f4-112">Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [C# sürüm 3.0 belirtimi](https://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="e88f4-112">For more information about extension methods, see [C# Version 3.0 Specification](https://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="e88f4-113">Örnek, aşağıdaki projelerin oluşur:</span><span class="sxs-lookup"><span data-stu-id="e88f4-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="e88f4-114">`OrderErrorLibrary` Tanımlayan bir sınıf kitaplığı `OrderError` ve `OrderErrorCollection` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e88f4-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="e88f4-115">Bir `OrderError` Geçersiz girdi girildiğinde örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e88f4-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="e88f4-116">Kitaplık ayrıca bir genişletme yöntemi sağlar `OrderErrorCollection` veren sınıf `ErrorText` tüm özellik `OrderError` nesneler `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="e88f4-117">`OrderProcessingPolicy` Projedir tanımlayan tek bir konsol uygulaması WF `PolicyFromFile` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e88f4-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="e88f4-118">Etkinlik aşağıdaki kurallar içerir:</span><span class="sxs-lookup"><span data-stu-id="e88f4-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="e88f4-119">Bu kural, öğe sayısı 1 ile 6, kapsamlı arasında olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="e88f4-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="e88f4-120">Öğe numarası geçerli aralıkta ise, kural (konsola yazdırma dışında) bir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e88f4-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="e88f4-121">Öğe sayısı 1 ile 6 değilse `invalidItemNum` kural şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="e88f4-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="e88f4-122">Yeni bir oluşturur `OrderError` maddeye geçirerek girilen ve ayarlar nesnesi `ErrorText` ve `CustomerName` nesnesindeki özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e88f4-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="e88f4-123">Oluşturur bir `invalidItemNumErrorCollection` nesne.</span><span class="sxs-lookup"><span data-stu-id="e88f4-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="e88f4-124">Yeni oluşturulan ekler `OrderError` için örnek `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="e88f4-125">Bu desteğini gösterir `new` ile örneği kuralları içindeki nesnelerinin işleci.</span><span class="sxs-lookup"><span data-stu-id="e88f4-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="e88f4-126">Bu kural, posta kodu 5 basamak bulunur ve bir aralıkta için 600 99998 doğrular.</span><span class="sxs-lookup"><span data-stu-id="e88f4-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="e88f4-127">Posta kodu geçerli aralığında ise, kural (konsola yazdırma dışında) bir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e88f4-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="e88f4-128">Posta kodu uzunluğu 5'ten veya posta kodu, 99998 00600 arasında değil, `invalidZip` kural şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="e88f4-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="e88f4-129">Oluşturur bir `OrderError` nesne, posta kodu girildi, geçirme ve ayarlar `ErrorText` ve `CustomerName` nesnesindeki özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e88f4-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="e88f4-130">Oluşturur bir `invalidZipCodeErrorCollection` nesne.</span><span class="sxs-lookup"><span data-stu-id="e88f4-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="e88f4-131">Yeni oluşturulan ekler `OrderError` yeni oluşturulan örneğine `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="e88f4-132">Bu kural yeniden desteği gösterir `new` kuralları içindeki nesneleri somutlaştırmak olanak tanıyan işleci.</span><span class="sxs-lookup"><span data-stu-id="e88f4-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="e88f4-133">Bu kural, iki önceki iki kural tarafından eklenen herhangi bir hata olup olmadığını görmek için denetler `OrderErrorCollection` nesneleri `invalidItemNumErrorCollection` ve `invalidIZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="e88f4-134">Hatalar varsa (ya da `invalidItemNumErrorCollection` veya `invalidZipCodeErrorCollection` değil `null`), kural şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="e88f4-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="e88f4-135">Aşırı yüklenen çağırır `+` içeriğinin kopyalanacağı işleci `invalidItemNumErrorCollection` ve `invalidZipCodeErrorCollection` için bir `invalidOrdersCollection``OrderErrorCollection` örneği.</span><span class="sxs-lookup"><span data-stu-id="e88f4-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="e88f4-136">Çağrıları `PrintOrderErrors` genişletme yöntemini `invalidOrdersCollection` ve çıkaran `ErrorText` tüm özellik `orderError` nesneler `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="e88f4-137">Aşırı yüklenmiş işleç `+` üzerinde `OrderErrorCollection` tanımlanan `OrderErrorCollection` içinde sınıf `OrderErrorLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e88f4-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="e88f4-138">İki alan `OrderErrorCollection` nesneleri ve bunları birine birleştirir `OrderErrorCollection` nesne.</span><span class="sxs-lookup"><span data-stu-id="e88f4-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="e88f4-139">`PrintOrderErrors` Uzantı yönteminin tanımlandığı ayrıca `OrderErrorLibrary` proje.</span><span class="sxs-lookup"><span data-stu-id="e88f4-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="e88f4-140">Uzantı, geliştiricilerin yeni yöntemler, bir sınıf türetmeniz ya da özgün türü yeniden derlemenize gerek kalmadan var olan bir CLR türünün ortak bir sözleşme eklemelerini sağlayan yeni bir C# özelliği yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="e88f4-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="e88f4-141">Örneği çalıştırdığında bir ad, satın alınması öğesi öğe sayısını ve posta kodu girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="e88f4-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="e88f4-142">Bu bilgiler daha sonra ilke etkinliğinde tanımlanan kuralları tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="e88f4-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="e88f4-143">Programdan alınan çıkış örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e88f4-143">The following is sample output from the program.</span></span>  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e88f4-144">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e88f4-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e88f4-145">OrderProcessingPolicy.sln proje dosyasında açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e88f4-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e88f4-146">Çözümde iki farklı proje vardır: `OrderErrorLibrary` ve `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="e88f4-147">`OrderProcessingPolicy` Kullanan proje sınıfları ve yöntemleri tanımlanan `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="e88f4-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="e88f4-148">Tüm projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e88f4-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="e88f4-149">**Çalıştır**'ı tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e88f4-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e88f4-150">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="e88f4-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e88f4-151">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="e88f4-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e88f4-152">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e88f4-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e88f4-153">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="e88f4-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`