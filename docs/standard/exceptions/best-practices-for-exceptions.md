---
title: "Özel Durumlar için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c5ea19077ff9ce8e36a33601b7e5e87c64afe60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="71fcc-102">Özel durumlar için en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="71fcc-102">Best practices for exceptions</span></span>

<span data-ttu-id="71fcc-103">İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler.</span><span class="sxs-lookup"><span data-stu-id="71fcc-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="71fcc-104">Bu bölüm işleme ve özel durumlar oluşturma en iyi uygulamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="71fcc-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks"></a><span data-ttu-id="71fcc-105">Try/catch/finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="71fcc-105">Use try/catch/finally blocks</span></span>

<span data-ttu-id="71fcc-106">Kullanım `try` / `catch` / `finally` geçici bir özel durum oluşturmak kod blokları.</span><span class="sxs-lookup"><span data-stu-id="71fcc-106">Use `try`/`catch`/`finally` blocks around code that can potentially generate an exception.</span></span> 

<span data-ttu-id="71fcc-107">İçinde `catch` engeller, her zaman sipariş özel durumlar en az belirli özel.</span><span class="sxs-lookup"><span data-stu-id="71fcc-107">In `catch` blocks, always order exceptions from the most specific to the least specific.</span></span>

<span data-ttu-id="71fcc-108">Kullanım bir `finally` veya kurtarabilirsiniz olup olmadığını, kaynakları temizlemek için blok.</span><span class="sxs-lookup"><span data-stu-id="71fcc-108">Use a `finally` block to clean up resources, whether you can recover or not.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="71fcc-109">Özel durumları atma olmadan genel koşullar işleme</span><span class="sxs-lookup"><span data-stu-id="71fcc-109">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="71fcc-110">Oluşur ancak bir özel durum harekete özel kurtulursunuz bir biçimde işleme göz önünde bulundurun büyük olasılıkla koşulları.</span><span class="sxs-lookup"><span data-stu-id="71fcc-110">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="71fcc-111">Örneğin, zaten kapatılmış bir bağlantıyı kapatın denerseniz elde edersiniz bir `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="71fcc-111">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="71fcc-112">Kullanarak, önleyebilirsiniz bir `if` deyimi kapatmak denemeden önce bağlantı durumunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="71fcc-112">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="71fcc-113">Bağlantı durumu kapatmadan önce denetlemez, yakalayabilir `InvalidOperationException` özel durum.</span><span class="sxs-lookup"><span data-stu-id="71fcc-113">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="71fcc-114">Olayın gerçekleşmesi için ne sıklıkta yapılacağı seçmek için yöntem bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="71fcc-114">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="71fcc-115">Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="71fcc-115">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="71fcc-116">Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="71fcc-116">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="71fcc-117">Olay düzenli olarak gerçekleştirilir ve normal yürütme bir parçası olarak değerlendirilebilir kodda hata koşulları için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="71fcc-117">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="71fcc-118">Sık karşılaşılan hata koşulları için işaretlediğinizde, özel durumlar önlemek için daha az kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="71fcc-118">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="71fcc-119">Özel durumlar önlenebilir böylece sınıfları tasarlama</span><span class="sxs-lookup"><span data-stu-id="71fcc-119">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="71fcc-120">Veya bir özel durum çağrı yapmaktan kaçınmak olanak tanıyan özellikler tetikleyecek bir sınıfı yöntemleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-120">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="71fcc-121">Örneğin, bir <xref:System.IO.FileStream> sınıfı dosyasının sonuna ulaşıldı olup olmadığını belirlemenize yardımcı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="71fcc-121">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="71fcc-122">Bu dosya sonunun okuyorsanız oluşan özel durum önlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-122">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="71fcc-123">Aşağıdaki örnek, bir özel durum tetiklemeden dosya sonuna kadar okumak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-123">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="71fcc-124">Özel durumlar önlemek için başka bir özel durum atma yerine son derece ortak hata durumları için null döndürmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="71fcc-124">Another way to avoid exceptions is to return null for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="71fcc-125">Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-125">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="71fcc-126">Bu durumda null değer döndürerek, uygulama performansı üzerindeki etkisini en aza indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71fcc-126">By returning null in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="71fcc-127">Bir hata kodu döndürüyor yerine özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="71fcc-127">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="71fcc-128">Özel durumlar hataları çağırmak için kodu bir dönüş koduyla kontrol kaydetmedi gözden kaçan geçmemektedir emin olun.</span><span class="sxs-lookup"><span data-stu-id="71fcc-128">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span> 

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="71fcc-129">Önceden tanımlanmış .NET özel durum türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="71fcc-129">Use the predefined .NET exception types</span></span>

<span data-ttu-id="71fcc-130">Önceden tanımlanmış bir yalnızca uygulanmaz zaman yeni bir özel durum sınıfı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="71fcc-130">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="71fcc-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="71fcc-131">For example:</span></span>

- <span data-ttu-id="71fcc-132">Throw bir <xref:System.InvalidOperationException> bir özellik kümesi veya yöntem çağrısı nesnenin geçerli durumu verilen uygun değilse, özel durum.</span><span class="sxs-lookup"><span data-stu-id="71fcc-132">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="71fcc-133">Throw bir <xref:System.ArgumentException> özel durum ya da öğesinden türetilen önceden tanımlanmış sınıflarından <xref:System.ArgumentException> geçersiz parametreler aktarılırsa.</span><span class="sxs-lookup"><span data-stu-id="71fcc-133">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="71fcc-134">Son özel durum sınıfı adları sözcüğü`Exception`</span><span class="sxs-lookup"><span data-stu-id="71fcc-134">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="71fcc-135">Bir özel durum gerekli olduğunda, uygun şekilde adlandırın ve buradan türetebilir <xref:System.Exception> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71fcc-135">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="71fcc-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="71fcc-136">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="71fcc-137">Üç oluşturucular özel durum sınıfları içerir</span><span class="sxs-lookup"><span data-stu-id="71fcc-137">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="71fcc-138">En az üç ortak oluşturucular kendi özel durum sınıfları oluştururken kullanmak: varsayılan oluşturucu, dize ileti alan bir oluşturucu ve dize ileti ve iç özel duruma alan bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="71fcc-138">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="71fcc-139"><xref:System.Exception.%23ctor>, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="71fcc-139"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="71fcc-140"><xref:System.Exception.%23ctor%28System.String%29>, bir dize ileti kabul eder.</span><span class="sxs-lookup"><span data-stu-id="71fcc-140"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="71fcc-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, bir dize ileti ve iç özel duruma kabul.</span><span class="sxs-lookup"><span data-stu-id="71fcc-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="71fcc-142">Bir örnek için bkz: [nasıl yapılır: Create User-Defined özel durumları](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="71fcc-142">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="71fcc-143">Kod uzaktan yürüttüğünde özel durum verileri kullanılabilir olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="71fcc-143">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="71fcc-144">Kullanıcı tanımlı özel durumları oluşturduğunuzda, uzaktan yürütme kod için özel durumlar için meta veriler kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="71fcc-144">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="71fcc-145">Örneğin, uygulama etki alanları destekleyen .NET uygulamalarında, uygulama etki alanları arasında özel durumlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-145">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="71fcc-146">Uygulama etki alanı A aykırı kodu yürütür uygulama etki alanı B oluşturur varsayalım.</span><span class="sxs-lookup"><span data-stu-id="71fcc-146">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="71fcc-147">Uygulama etki alanı için doğru yakalamak ve özel durumu işlemek için bir uygulama etki alanı b tarafından oluşturulan özel durum içeren derlemenin bulamıyor olmalıdır Uygulama etki alanı B bütünleştirilmiş kendi uygulama temel altında bulunan bir özel durum oluşturur, ancak uygulama etki alanı A'ın uygulama temel altında değil, uygulama etki alanı bir özel durum bulmak mümkün olmaz ve ortak dil çalışma zamanı özel durum oluşturacak bir <xref:System.IO.FileNotFoundException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="71fcc-147">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="71fcc-148">Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="71fcc-148">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="71fcc-149">Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.</span><span class="sxs-lookup"><span data-stu-id="71fcc-149">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="71fcc-150">\-veya -</span><span class="sxs-lookup"><span data-stu-id="71fcc-150">\- or -</span></span>

- <span data-ttu-id="71fcc-151">Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.</span><span class="sxs-lookup"><span data-stu-id="71fcc-151">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="include-a-localized-description-string-in-every-exception"></a><span data-ttu-id="71fcc-152">Her bir durum yerelleştirilmiş açıklama dizesi içerir</span><span class="sxs-lookup"><span data-stu-id="71fcc-152">Include a localized description string in every exception</span></span>

<span data-ttu-id="71fcc-153">Kullanıcının gördüğü hata iletisi, oluşturulan özel durumun açıklama dizesi ve olmayan özel durum sınıfı adı elde edilir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-153">The error message that the user sees is derived from the description string of the exception that was thrown, and not from the name of the exception class.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="71fcc-154">Dilbilgisi bakımından doğru hata iletilerini kullanın</span><span class="sxs-lookup"><span data-stu-id="71fcc-154">Use grammatically correct error messages</span></span>

<span data-ttu-id="71fcc-155">Clear cümle yazın ve noktalama bitiş içerir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-155">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="71fcc-156">Bir özel durumun açıklama dizesindeki her cümle nokta ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-156">Each sentence in a description string of an exception should end in a period.</span></span> <span data-ttu-id="71fcc-157">Örneğin, "günlüğü tablosu taştı."</span><span class="sxs-lookup"><span data-stu-id="71fcc-157">For example, "The log table has overflowed."</span></span> <span data-ttu-id="71fcc-158">uygun açıklama dizesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="71fcc-158">would be an appropriate description string.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="71fcc-159">Özel durumlar gerektiği gibi ek özellikler sağlar</span><span class="sxs-lookup"><span data-stu-id="71fcc-159">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="71fcc-160">Bir özel durum (ek açıklama dizesi) için ek özellikler sağlamak yalnızca ek bilgiler nerede yararlı programlı bir senaryo olduğunda.</span><span class="sxs-lookup"><span data-stu-id="71fcc-160">Provide additional properties for an exception (in addition to the description string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="71fcc-161">Örneğin, <xref:System.IO.FileNotFoundException> sağlar <xref:System.IO.FileNotFoundException.FileName> özelliği.</span><span class="sxs-lookup"><span data-stu-id="71fcc-161">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="71fcc-162">Böylece yığın izlemesi yardımcı olacaktır yer throw deyimleri</span><span class="sxs-lookup"><span data-stu-id="71fcc-162">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="71fcc-163">Burada özel durum oluşur ve bitişi bildirimi yığın izleme başlangıcı `catch` özel yakalar deyimi.</span><span class="sxs-lookup"><span data-stu-id="71fcc-163">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="71fcc-164">Özel durum Oluşturucu yöntemleri kullanın</span><span class="sxs-lookup"><span data-stu-id="71fcc-164">Use exception builder methods</span></span>

<span data-ttu-id="71fcc-165">Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="71fcc-165">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="71fcc-166">Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="71fcc-166">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="71fcc-167">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="71fcc-167">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="71fcc-168">Bazı durumlarda, özel durumun Oluşturucusu özel durum oluşturmak için kullanılacak daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="71fcc-168">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="71fcc-169">Genel özel durum sınıfı gibi örneğidir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="71fcc-169">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a><span data-ttu-id="71fcc-170">Bir özel durum atma zaman ara sonuçlarını temizle</span><span class="sxs-lookup"><span data-stu-id="71fcc-170">Clean up intermediate results when throwing an exception</span></span>

<span data-ttu-id="71fcc-171">Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="71fcc-171">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="71fcc-172">Örneğin, bir hesaptan geri alınmasının ve içinde başka bir hesap ürünü para aktarır kodu varsa ve banka yürütülürken bir özel durum, etkin kalmasını mevzuatı istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="71fcc-172">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="71fcc-173">Bu durumu yönetmek için bir banka işlem tarafından oluşturulan tüm özel durumları yakalar ve mevzuatı geri yoldur.</span><span class="sxs-lookup"><span data-stu-id="71fcc-173">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

<span data-ttu-id="71fcc-174">Bu örnek kullanımını göstermektedir `throw` arayanlar inceleyin gerek kalmadan sorunun gerçek nedenini görmek daha kolay hale getirebilir özgün özel yeniden vermesini <xref:System.Exception.InnerException> özelliği.</span><span class="sxs-lookup"><span data-stu-id="71fcc-174">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="71fcc-175">Yeni bir özel durum ve iç özel duruma olarak orijinal özel durumu eklemek için kullanılan bir alternatiftir:</span><span class="sxs-lookup"><span data-stu-id="71fcc-175">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a><span data-ttu-id="71fcc-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71fcc-176">See Also</span></span>  
[<span data-ttu-id="71fcc-177">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="71fcc-177">Exceptions</span></span>](index.md)
