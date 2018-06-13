---
title: İlke ile işlem sırası
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: 15e274a7a513a3208e3a54575dc354310743b731
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519424"
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="6aac9-102">İlke ile işlem sırası</span><span class="sxs-lookup"><span data-stu-id="6aac9-102">Order Processing with Policy</span></span>
<span data-ttu-id="6aac9-103">Sipariş işleme ilkesi örnek sunulan anahtar özelliklerinden bazıları gösterir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="6aac9-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="6aac9-104">Aşağıdaki işlevleri WF kurallar altyapısı için yenidir:</span><span class="sxs-lookup"><span data-stu-id="6aac9-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="6aac9-105">İşleç aşırı yüklemesi için destek.</span><span class="sxs-lookup"><span data-stu-id="6aac9-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="6aac9-106">Desteği `new` işleci, kullanıcıların yeni nesneler ve diziler WF kurallardan oluşturmasına izin verme.</span><span class="sxs-lookup"><span data-stu-id="6aac9-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="6aac9-107">Kullanıcı deneyimini WF kurallarından genişletme yöntemleri çağırma C stilleri # kodlama ile uyumlu hale getirmek genişletme yöntemleri için destek.</span><span class="sxs-lookup"><span data-stu-id="6aac9-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6aac9-108">Bu örnek gerektiren [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] derlemek ve çalıştırmak için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6aac9-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="6aac9-109"> Proje ve çözüm dosyalarını açmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6aac9-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="6aac9-110">Örnek gösteren bir `OrderProcessingPolicy` proje numaralandırılmış bir kullanılabilir öğeleri ve bir posta kodu listesinden oluşur, bir müşteri siparişi girilir.</span><span class="sxs-lookup"><span data-stu-id="6aac9-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="6aac9-111">Her iki girişleri doğruysa sırasını başarıyla işlenir; Aksi takdirde hata nesneleri, bir aşırı yüklenmiş kullanılarak ilkesi oluşturur `+` işleci ve önceden tanımlanmış genişletme yöntemi hataları kullanıcıyı bilgilendirmek üzere.</span><span class="sxs-lookup"><span data-stu-id="6aac9-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6aac9-112">Uzantı yöntemleri hakkında daha fazla bilgi için bkz: [C# sürüm 3.0 belirtimi](http://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="6aac9-112">For more information about extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="6aac9-113">Örnek aşağıdaki projeleri oluşmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6aac9-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="6aac9-114">`OrderErrorLibrary` Tanımlayan bir sınıf kitaplığı `OrderError` ve `OrderErrorCollection` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="6aac9-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="6aac9-115">Bir `OrderError` geçersiz bir giriş girildiğinde örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6aac9-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="6aac9-116">Kitaplık ayrıca bir genişletme yöntemi sağlar `OrderErrorCollection` çıkarır sınıfı `ErrorText` özelliği tüm `OrderError` nesnelerini `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="6aac9-117">`OrderProcessingPolicy` Projedir tek bir tanımlayan WF konsol uygulaması `PolicyFromFile` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6aac9-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="6aac9-118">Etkinlik aşağıdaki kurallar vardır:</span><span class="sxs-lookup"><span data-stu-id="6aac9-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="6aac9-119">Bu kural öğesi numarası 1 ile 6, (bunlar dahil) arasında olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="6aac9-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="6aac9-120">Madde numarası geçerli aralıkta ise, kural (dışında konsola yazdırma) hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6aac9-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="6aac9-121">Madde numarası 1 ile 6 arasında değilse `invalidItemNum` kural aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="6aac9-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="6aac9-122">Yeni bir `OrderError` nesne, maddeye geçirme girilen ve ayarlar `ErrorText` ve `CustomerName` nesne üzerindeki özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6aac9-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="6aac9-123">Oluşturur bir `invalidItemNumErrorCollection` nesne.</span><span class="sxs-lookup"><span data-stu-id="6aac9-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="6aac9-124">Yeni oluşturulan ekler `OrderError` için örnek `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="6aac9-125">Bu desteği gösterir `new` ile örneği nesneleri kuralları içine işleci.</span><span class="sxs-lookup"><span data-stu-id="6aac9-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="6aac9-126">Bu kural, posta kodu 5 rakamlı sahip ve için 600 99998 aralığı içinde doğrular.</span><span class="sxs-lookup"><span data-stu-id="6aac9-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="6aac9-127">Posta kodu geçerli aralıkta ise, kural (dışında konsola yazdırma) hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6aac9-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="6aac9-128">Posta kodu uzunluğu 5'ten az veya posta kodu 00600 ve 99998, arasında değil `invalidZip` kural aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="6aac9-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="6aac9-129">Oluşturur bir `OrderError` nesnesi, girilen, posta kodu geçirme ve ayarlar `ErrorText` ve `CustomerName` nesne üzerindeki özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6aac9-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="6aac9-130">Oluşturur bir `invalidZipCodeErrorCollection` nesne.</span><span class="sxs-lookup"><span data-stu-id="6aac9-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="6aac9-131">Yeni oluşturulan ekler `OrderError` yeni oluşturulan örneğine `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="6aac9-132">Bu kural için destek yeniden gösteren `new` nesneleri kuralları içine örneği olanak tanıyan işleci.</span><span class="sxs-lookup"><span data-stu-id="6aac9-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="6aac9-133">Bu kural, önceki iki kural iki tarafından eklenen herhangi bir hata olup olmadığını görmek için denetler `OrderErrorCollection` nesneleri `invalidItemNumErrorCollection` ve `invalidIZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="6aac9-134">Hatalar varsa (ya da `invalidItemNumErrorCollection` veya `invalidZipCodeErrorCollection` değil `null`), kural aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="6aac9-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="6aac9-135">Aşırı yüklenmiş çağırır `+` içeriğini kopyalamak için işleci `invalidItemNumErrorCollection` ve `invalidZipCodeErrorCollection` için bir `invalidOrdersCollection``OrderErrorCollection` örneği.</span><span class="sxs-lookup"><span data-stu-id="6aac9-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="6aac9-136">Çağrıları `PrintOrderErrors` genişletme yöntemi `invalidOrdersCollection` ve çıkaran `ErrorText` özelliği tüm `orderError` nesnelerini `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="6aac9-137">Aşırı yüklenmiş işleci `+` üzerinde `OrderErrorCollection` tanımlanan `OrderErrorCollection` sınıfı, buna `OrderErrorLibrary` projesi.</span><span class="sxs-lookup"><span data-stu-id="6aac9-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="6aac9-138">İki alan `OrderErrorCollection` nesneleri ve bunları tek istekte birleştirir `OrderErrorCollection` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6aac9-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="6aac9-139">`PrintOrderErrors` Genişletme yöntemi tanımlanan de `OrderErrorLibrary` projesi.</span><span class="sxs-lookup"><span data-stu-id="6aac9-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="6aac9-140">Genişletme yöntemleri, buradan bir sınıf türetin veya özgün türü derlenir gerek kalmadan mevcut bir CLR türü ortak sözleşmesi için yeni yöntemler eklemek için geliştiricilere sağlayan bir yeni C# özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="6aac9-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="6aac9-141">Örnek çalıştırdığınızda, bir ad, satın alınması için öğeyi öğe sayısını ve bir posta kodu girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="6aac9-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="6aac9-142">Bu bilgiler daha sonra ilke etkinliğinde tanımlanan kurallar tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6aac9-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="6aac9-143">Program dosyasından örnek çıktı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6aac9-143">The following is sample output from the program.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6aac9-144">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6aac9-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6aac9-145">OrderProcessingPolicy.sln proje dosyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6aac9-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6aac9-146">Çözümde iki farklı projelere vardır: `OrderErrorLibrary` ve `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="6aac9-147">`OrderProcessingPolicy` Proje kullanır sınıflar ve yöntemler tanımlanan `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="6aac9-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="6aac9-148">Tüm projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6aac9-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="6aac9-149">**Çalıştır**'ı tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6aac9-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6aac9-150">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="6aac9-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6aac9-151">Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:</span><span class="sxs-lookup"><span data-stu-id="6aac9-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6aac9-152">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6aac9-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6aac9-153">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="6aac9-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`