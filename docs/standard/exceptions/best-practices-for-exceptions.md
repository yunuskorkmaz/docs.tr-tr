---
title: İstisnalar için En İyi Uygulamalar - .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 1de231b01e3fa97e78a87ae6b0595a9b5536374e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160176"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="d2382-102">Özel durumlar için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="d2382-102">Best practices for exceptions</span></span>

<span data-ttu-id="d2382-103">İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler.</span><span class="sxs-lookup"><span data-stu-id="d2382-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="d2382-104">Bu bölümde, özel durumları işlemek ve oluşturmak için en iyi uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2382-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="d2382-105">Hatalardan kurtulmak veya kaynakları serbest bırakmak için try/catch/finally bloklarını kullanma</span><span class="sxs-lookup"><span data-stu-id="d2382-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="d2382-106">Olası `try` / `catch` bir özel durum oluşturabilecek kodun etrafındaki blokları kullanın ***ve*** kodunuz bu özel durumdan kurtarabilir.</span><span class="sxs-lookup"><span data-stu-id="d2382-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="d2382-107">Bloklarda, `catch` her zaman en çok türetilenden en az türetilmiş özel durumları sıralar.</span><span class="sxs-lookup"><span data-stu-id="d2382-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="d2382-108">Tüm özel <xref:System.Exception>durumlar.</span><span class="sxs-lookup"><span data-stu-id="d2382-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="d2382-109">Daha fazla türetilmiş özel durumlar, taban özel durum sınıfı için bir catch yan tümcesi tarafından önce gelen bir catch yan tümcesi tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="d2382-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="d2382-110">Kodunuz bir özel durum kurtarılamadığınızda, bu özel durumu yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="d2382-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="d2382-111">Mümkünse kurtarmak için arama yığınının daha yukarısına yöntemleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d2382-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="d2382-112">İfadelerle veya `finally` bloklarla `using` ayrılan kaynakları temizleyin.</span><span class="sxs-lookup"><span data-stu-id="d2382-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="d2382-113">Özel `using` durumlar atıldığında kaynakları otomatik olarak temizlemek için deyimleri tercih edin.</span><span class="sxs-lookup"><span data-stu-id="d2382-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="d2382-114">Uygulanmayan `finally` <xref:System.IDisposable>kaynakları temizlemek için blokları kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2382-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="d2382-115">Bir `finally` yan tümcedeki kod, özel durumlar atıldığında bile hemen hemen her zaman yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d2382-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="d2382-116">Özel durumlar atmadan sık karşılaşılan koşulları işleme</span><span class="sxs-lookup"><span data-stu-id="d2382-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="d2382-117">Oluşması muhtemel ancak bir özel durum tetikleyebilecek koşullar için, bunları özel durumlardan kaçınacak şekilde işlemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="d2382-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="d2382-118">Örneğin, zaten kapalı olan bir bağlantıyı kapatmaya çalışırsanız, `InvalidOperationException`bir .</span><span class="sxs-lookup"><span data-stu-id="d2382-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="d2382-119">Kapatmaya çalışmadan önce `if` bağlantı durumunu denetlemek için bir deyim kullanarak bunu önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2382-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="d2382-120">Kapatmadan önce bağlantı durumunu denetlemezseniz, `InvalidOperationException` özel durumu yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2382-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="d2382-121">Seçilecek yöntem, olayın ne sıklıkta gerçekleşmesini beklediğiniz bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2382-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="d2382-122">Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2382-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="d2382-123">Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="d2382-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="d2382-124">Olay olağan bir şekilde gerçekleşirse ve normal yürütmenin bir parçası olarak kabul edilebilirse koddaki hata koşullarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d2382-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="d2382-125">Sık karşılaşılan hata koşullarını denetlediğinizde, özel durumlar dan kaçınmak için daha az kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d2382-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="d2382-126">Özel durumların önlenebileceği şekilde tasarım sınıfları</span><span class="sxs-lookup"><span data-stu-id="d2382-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="d2382-127">Bir sınıf, özel bir durum tetikleyen bir arama yapmaktan kaçınmanızı sağlayan yöntemler veya özellikler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d2382-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="d2382-128">Örneğin, bir <xref:System.IO.FileStream> sınıf, dosyanın sonuna ulaşılıp ulaşılmadığını belirlemeye yardımcı olan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2382-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="d2382-129">Bunlar, dosyanın sonundan geçmiş okursanız atılan özel durum lardan kaçınmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2382-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="d2382-130">Aşağıdaki örnek, bir özel durum tetiklemeden bir dosyanın sonuna kadar nasıl okunacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2382-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="d2382-131">Özel durumları önlemenin başka bir yolu da, özel durum atmak yerine son derece yaygın hata durumları için null (veya varsayılan) döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="d2382-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="d2382-132">Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d2382-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="d2382-133">Bu gibi durumlarda null (veya varsayılan) döndürerek, bir uygulamaya performans etkisini en aza indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2382-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="d2382-134">Değer türleri için, `Nullable<T>` hata göstergeniz olarak kullanılıp kullanılmayacağınız veya varsayılan olarak, belirli uygulamanız için göz önünde bulundurulması gereken bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="d2382-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="d2382-135">Kullanarak `Nullable<Guid>`, `default` `null` yerine `Guid.Empty`olur .</span><span class="sxs-lookup"><span data-stu-id="d2382-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="d2382-136">Bazı zamanlar, `Nullable<T>` bir değer mevcut veya yok olduğunda ekleme daha net yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2382-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="d2382-137">Diğer zamanlarda, `Nullable<T>` ekleme gerekli değildir denetlemek için ek durumlarda oluşturabilir ve yalnızca hata potansiyel kaynakları oluşturmak için hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="d2382-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="d2382-138">Hata kodu döndürmek yerine özel durumlar atma</span><span class="sxs-lookup"><span data-stu-id="d2382-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="d2382-139">Özel durumlar, arama kodu iade kodunu denetlemediğinden hataların fark edilmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2382-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="d2382-140">Önceden tanımlanmış .NET özel durum türlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="d2382-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="d2382-141">Yalnızca önceden tanımlanmış bir sınıf geçerli olmadığında yeni bir özel durum sınıfı tanıtın.</span><span class="sxs-lookup"><span data-stu-id="d2382-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="d2382-142">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d2382-142">For example:</span></span>

- <span data-ttu-id="d2382-143">Nesnenin <xref:System.InvalidOperationException> geçerli durumu göz önüne alındığında özellik kümesi veya yöntem çağrısı uygun değilse bir özel durum atın.</span><span class="sxs-lookup"><span data-stu-id="d2382-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="d2382-144">Geçersiz <xref:System.ArgumentException> parametreler geçirilirse türeyen bir <xref:System.ArgumentException> özel durum veya önceden tanımlanmış sınıflardan birini atın.</span><span class="sxs-lookup"><span data-stu-id="d2382-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="d2382-145">Özel durum sınıf adlarını sözcüğüyle sonlandırır`Exception`</span><span class="sxs-lookup"><span data-stu-id="d2382-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="d2382-146">Özel bir özel durum gerektiğinde, uygun bir şekilde <xref:System.Exception> adlandırın ve sınıftan türetin.</span><span class="sxs-lookup"><span data-stu-id="d2382-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="d2382-147">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d2382-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="d2382-148">Özel özel durum sınıflarına üç oluşturucu ekleme</span><span class="sxs-lookup"><span data-stu-id="d2382-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="d2382-149">Kendi özel durum sınıflarınızı oluştururken en az üç ortak oluşturucuyu kullanın: parametresiz oluşturucu, dize iletisi alan bir oluşturucu ve dize iletisi ve iç özel durum alan bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="d2382-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="d2382-150"><xref:System.Exception.%23ctor>, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d2382-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="d2382-151"><xref:System.Exception.%23ctor%28System.String%29>, bir dize iletisi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d2382-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="d2382-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, bir dize iletisi ve bir iç özel durum kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d2382-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="d2382-153">Örneğin, [bkz.](how-to-create-user-defined-exceptions.md)</span><span class="sxs-lookup"><span data-stu-id="d2382-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="d2382-154">Kod uzaktan yürütüldüğünde özel durum verilerinin kullanılabilir olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="d2382-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="d2382-155">Kullanıcı tanımlı özel durumlar oluşturduğunuzda, özel durumlar için meta verilerin uzaktan yürütülen kodiçin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d2382-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="d2382-156">Örneğin, App Etki Alanlarını destekleyen .NET uygulamalarında, Uygulama etki alanlarında özel durumlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="d2382-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="d2382-157">App Domain A'nın, özel durum oluşturan kodu yürüten App Domain B oluşturduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="d2382-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="d2382-158">App Domain A'nın özel durumu düzgün bir şekilde yakalayaması ve işlemesi için, App Domain B tarafından atılan özel durumu içeren derlemeyi bulabilmek gerekir. App Domain B, uygulama tabanı altında bir derlemede bulunan ancak App Domain A'nın uygulama tabanı altında olmayan bir özel durum oluşturursa, App <xref:System.IO.FileNotFoundException> Domain A özel durumu bulamaz ve ortak dil çalışma süresi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2382-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="d2382-159">Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d2382-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="d2382-160">Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.</span><span class="sxs-lookup"><span data-stu-id="d2382-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="d2382-161">\-veya -</span><span class="sxs-lookup"><span data-stu-id="d2382-161">\- or -</span></span>

- <span data-ttu-id="d2382-162">Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.</span><span class="sxs-lookup"><span data-stu-id="d2382-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="d2382-163">Dilbilgisi açısından doğru hata iletilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="d2382-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="d2382-164">Açık cümleler yazın ve noktalama işaretlerini sona erdirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="d2382-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="d2382-165"><xref:System.Exception.Message?displayProperty=nameWithType> Özelliğe atanan dizedeki her cümle bir süre içinde sona ermelidir.</span><span class="sxs-lookup"><span data-stu-id="d2382-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="d2382-166">Örneğin, "Günlük tablosu taşmış."</span><span class="sxs-lookup"><span data-stu-id="d2382-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="d2382-167">uygun bir ileti dizesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d2382-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="d2382-168">Her özel durum için yerelleştirilmiş bir dize iletisi ekleme</span><span class="sxs-lookup"><span data-stu-id="d2382-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="d2382-169">Kullanıcının gördüğü hata iletisi, <xref:System.Exception.Message?displayProperty=nameWithType> özel durum sınıfının adından değil, atılan özel durum özelliğinden türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2382-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="d2382-170">Genellikle, ileti dizesini bir <xref:System.Exception.Message?displayProperty=nameWithType> [Özel Durum oluşturucunun](xref:System.Exception.%23ctor%2A) `message` bağımsız değişkenine geçirerek özelliğe bir değer atarsınız.</span><span class="sxs-lookup"><span data-stu-id="d2382-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="d2382-171">Yerelleştirilmiş uygulamalar için, uygulamanızın atabileceği her özel durum için yerelleştirilmiş bir ileti dizesi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2382-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="d2382-172">Yerelleştirilmiş hata iletileri sağlamak için kaynak dosyalarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d2382-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="d2382-173">Uygulamaları yerelleştirme ve yerelleştirilmiş dizeleri alma hakkında bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="d2382-173">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="d2382-174">Nasıl yapılır: yerelleştirilmiş özel durum iletileriyle kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2382-174">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="d2382-175">Masaüstü Uygulamalarında Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d2382-175">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="d2382-176">Özel özel durumlarda, gerektiğinde ek özellikler sağlayın</span><span class="sxs-lookup"><span data-stu-id="d2382-176">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="d2382-177">Yalnızca ek bilgilerin yararlı olduğu programlı bir senaryo olduğunda bir özel durum için ek özellikler sağlayın (özel ileti dizesine ek olarak).</span><span class="sxs-lookup"><span data-stu-id="d2382-177">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="d2382-178">Örneğin, <xref:System.IO.FileNotFoundException.FileName> özellik <xref:System.IO.FileNotFoundException> sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2382-178">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="d2382-179">Yığın izlemenin yararlı olması için atma deyimleri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="d2382-179">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="d2382-180">Yığın izleme, özel durum atıldığı ifadeden başlar `catch` ve özel durumu yakalayan deyimle sona erer.</span><span class="sxs-lookup"><span data-stu-id="d2382-180">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="d2382-181">Özel durum oluşturucu yöntemlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="d2382-181">Use exception builder methods</span></span>

<span data-ttu-id="d2382-182">Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="d2382-182">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="d2382-183">Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2382-183">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="d2382-184">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d2382-184">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="d2382-185">Bazı durumlarda, özel durum oluşturmak için özel durum oluşturucusu kullanmak daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="d2382-185">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="d2382-186">Örnek olarak <xref:System.ArgumentException>genel bir özel durum sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d2382-186">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="d2382-187">Özel durumlar nedeniyle yöntemler tamamlanmadığında durumu geri yükleme</span><span class="sxs-lookup"><span data-stu-id="d2382-187">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="d2382-188">Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d2382-188">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="d2382-189">Örneğin, bir hesaptan çekilip başka bir hesaba para yatırarak para aktaran kodunuz varsa ve depozitoyu yürütürlerken bir özel durum atılırsa, para çekme işleminin geçerli kalmasını istemezsinüz.</span><span class="sxs-lookup"><span data-stu-id="d2382-189">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

<span data-ttu-id="d2382-190">Yukarıdaki yöntem doğrudan herhangi bir istisna atmaz, ancak para yatırma işlemi başarısız olursa, para çekme ters böylece savunma yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2382-190">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="d2382-191">Bu durumu ele almak için bir yolu para yatırma işlemi tarafından atılan herhangi bir istisna yakalamak ve para çekme geri almaktır.</span><span class="sxs-lookup"><span data-stu-id="d2382-191">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

<span data-ttu-id="d2382-192">Bu örnek, arayanların `throw` <xref:System.Exception.InnerException> özelliği incelemek zorunda kalmadan sorunun gerçek nedenini görmesini kolaylaştıran özgün özel durumu yeniden atma nın kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d2382-192">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="d2382-193">Alternatif, yeni bir özel durum atmak ve iç özel durum olarak özgün özel durum eklemektir:</span><span class="sxs-lookup"><span data-stu-id="d2382-193">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a><span data-ttu-id="d2382-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2382-194">See also</span></span>

- [<span data-ttu-id="d2382-195">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="d2382-195">Exceptions</span></span>](index.md)
