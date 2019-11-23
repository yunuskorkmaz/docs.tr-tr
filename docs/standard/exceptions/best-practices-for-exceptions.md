---
title: Özel durumlar için en iyi uygulamalar-.NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 6a165c3e0f41603ef7233669d7148dd44b1d3ce6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696759"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="a7ed5-102">Özel durumlar için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="a7ed5-102">Best practices for exceptions</span></span>

<span data-ttu-id="a7ed5-103">İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="a7ed5-104">Bu bölümde, özel durumları işlemeye ve oluşturmaya yönelik en iyi uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="a7ed5-105">Hataları veya yayın kaynaklarını kurtarmak için try/catch/finally bloklarını kullanın</span><span class="sxs-lookup"><span data-stu-id="a7ed5-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="a7ed5-106">Büyük olasılıkla bir özel durum oluşturabilen ***ve*** kodunuzun bu özel durumdan kurtulabildiği kod etrafında `try`/`catch` blokları kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="a7ed5-107">`catch` blokları ' nda, her zaman en çok türetilen özel durumları en düşük türetilmiş öğesine sıralayın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="a7ed5-108">Tüm özel durumlar <xref:System.Exception>türetilir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="a7ed5-109">Daha önce türetilmiş özel durumlar, bir temel özel durum sınıfı için catch yan tümcesinin önünde bulunan bir catch yan tümcesi tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="a7ed5-110">Kodunuz bir özel durumdan kurtarılamadığında bu özel durumu yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="a7ed5-111">Mümkünse, çağrı yığınını daha sonra kurtarmak için yöntemleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="a7ed5-112">`using` deyimleriyle veya `finally` bloklarında ayrılan kaynakları temizleyin.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="a7ed5-113">Özel durumlar oluştuğunda kaynakları otomatik olarak temizlemek için `using` deyimlerini tercih edin.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="a7ed5-114"><xref:System.IDisposable>uygulamayan kaynakları temizlemek için `finally` bloklarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="a7ed5-115">Bir `finally` yan tümcesindeki kod, özel durumlar oluştuğunda bile neredeyse her zaman yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="a7ed5-116">Özel durumlar oluşturmadan ortak koşulları işleme</span><span class="sxs-lookup"><span data-stu-id="a7ed5-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="a7ed5-117">Meydana gelen ancak özel durum tetikleyebilen koşullar için, özel durumu önlemek için bunları işlemeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="a7ed5-118">Örneğin, zaten kapatılmış olan bir bağlantıyı kapatmaya çalışırsanız bir `InvalidOperationException`alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="a7ed5-119">Kapatmayı denemeden önce bağlantı durumunu denetlemek için bir `if` ifadesini kullanarak bundan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="a7ed5-120">Kapatmadan önce bağlantı durumunu denetmezseniz, `InvalidOperationException` özel durumunu yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="a7ed5-121">Seçme yöntemi, olayın ne sıklıkta gerçekleşmesini beklediğinize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="a7ed5-122">Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="a7ed5-123">Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="a7ed5-124">Olay düzenli olarak gerçekleşdiğinde ve normal yürütmenin parçası olarak kabul edildiğinde koddaki hata koşullarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="a7ed5-125">Yaygın hata koşullarını denetlediğinizde, özel durumların önüne düşeceğinden daha az kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="a7ed5-126">Özel durumların önlenebilir olması için sınıfları tasarlayın</span><span class="sxs-lookup"><span data-stu-id="a7ed5-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="a7ed5-127">Bir sınıf, özel durum tetikleyebilecek bir çağrı yapmaktan kaçınmanızı sağlayan yöntemler veya özellikler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="a7ed5-128">Örneğin, bir <xref:System.IO.FileStream> sınıfı, dosyanın sonuna ulaşılıp ulaşılmadığını belirlemenize yardımcı olan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="a7ed5-129">Bunlar, dosyanın sonundan sonra okuduğunuzda oluşturulan özel durumu önlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="a7ed5-130">Aşağıdaki örnek, bir özel durum tetiklemeden bir dosyanın sonuna nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="a7ed5-131">Özel durumların önlenmesi için başka bir yol da, özel durum oluşturmak yerine son derece yaygın hata durumları için null (veya varsayılan) döndürmaktır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="a7ed5-132">Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="a7ed5-133">Bu durumlarda null (veya varsayılan) döndürerek, bir uygulamaya yönelik performans etkisini en aza indirmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="a7ed5-134">Değer türleri için, `Nullable<T>` veya varsayılan olarak, hata göstergesi, belirli bir uygulamanız için göz önünde bulundurmanız gereken bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="a7ed5-135">`Nullable<Guid>`kullanarak, `default` `Guid.Empty`yerine `null` hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="a7ed5-136">`Nullable<T>` eklemek, bir değer varsa veya olmadığında daha net hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="a7ed5-137">Diğer zamanlarda, `Nullable<T>` eklemek, gerekli olmadığını denetlemek için ek durumlar oluşturabilir ve yalnızca olası hata kaynakları oluşturmak için bu hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span> 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="a7ed5-138">Hata kodu döndürmek yerine özel durumlar oluşturun</span><span class="sxs-lookup"><span data-stu-id="a7ed5-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="a7ed5-139">Özel durumlar, çağrı kodu bir dönüş kodunu denetlemediğinden hataların açıklanmamasının algılanmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="a7ed5-140">Önceden tanımlanmış .NET özel durum türlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="a7ed5-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="a7ed5-141">Yalnızca önceden tanımlanmış bir uygulama uygulanmazsa yeni bir özel durum sınıfı tanıtın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="a7ed5-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a7ed5-142">For example:</span></span>

- <span data-ttu-id="a7ed5-143">Bir özellik kümesi veya yöntem çağrısı nesnenin geçerli durumuna uygun değilse <xref:System.InvalidOperationException> bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="a7ed5-144">Geçersiz parametreler geçirilmemişse, <xref:System.ArgumentException> bir özel durum veya <xref:System.ArgumentException> türetilen önceden tanımlanmış sınıflardan birini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="a7ed5-145">Word `Exception` özel durum sınıfı adlarını Sonlandır</span><span class="sxs-lookup"><span data-stu-id="a7ed5-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="a7ed5-146">Özel bir özel durum gerekli olduğunda, bunu uygun şekilde adlandırın ve <xref:System.Exception> sınıfından türetirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="a7ed5-147">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a7ed5-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="a7ed5-148">Özel özel durum sınıflarında üç Oluşturucu Ekle</span><span class="sxs-lookup"><span data-stu-id="a7ed5-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="a7ed5-149">Kendi özel durum sınıflarınızı oluştururken en az üç ortak Oluşturucu kullanın: parametresiz Oluşturucu, bir dize iletisi alan Oluşturucu ve bir dize iletisi ve bir iç özel durum alan Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="a7ed5-150">varsayılan değerleri kullanan <xref:System.Exception.%23ctor>.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="a7ed5-151">bir dize iletisi kabul eden <xref:System.Exception.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="a7ed5-152">bir dize iletisi ve bir iç özel durum kabul eden <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="a7ed5-153">Bir örnek için bkz. [nasıl yapılır: Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a7ed5-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="a7ed5-154">Kod uzaktan yürütüldüğünde özel durum verilerinin kullanılabilir olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="a7ed5-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="a7ed5-155">Kullanıcı tanımlı özel durumlar oluştururken, özel durumlar için meta verilerin uzaktan yürütülen kod için kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="a7ed5-156">Örneğin, uygulama etki alanlarını destekleyen .NET uygulamalarında, uygulama etki alanları arasında özel durumlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="a7ed5-157">Uygulama etki alanı A 'nın bir özel durum oluşturan kodu çalıştıran bir uygulama etki alanı oluşturduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="a7ed5-158">Uygulama etki alanı A 'nın özel durumu doğru bir şekilde yakalayabilmesi ve işlemesi için, uygulama etki alanı B tarafından oluşturulan özel durumu içeren derlemeyi bulması gerekir. Uygulama etki alanı B, uygulama temeli altındaki bir derlemede bulunan ancak uygulama etki alanı A 'nın uygulama temeli altında olmayan bir özel durum oluşturursa, A uygulama etki alanı özel durumu bulamaz ve ortak dil çalışma zamanı <xref:System.IO.FileNotFoundException> bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="a7ed5-159">Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7ed5-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="a7ed5-160">Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="a7ed5-161">\- veya -</span><span class="sxs-lookup"><span data-stu-id="a7ed5-161">\- or -</span></span>

- <span data-ttu-id="a7ed5-162">Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="a7ed5-163">Dilsiz doğru hata iletilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a7ed5-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="a7ed5-164">Temiz cümleler yazın ve son noktalama işaretlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="a7ed5-165"><xref:System.Exception.Message?displayProperty=nameWithType> özelliğine atanan dizedeki her tümce bir noktayla bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="a7ed5-166">Örneğin, "günlük tablosu taşmıştır."</span><span class="sxs-lookup"><span data-stu-id="a7ed5-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="a7ed5-167">uygun bir ileti dizesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="a7ed5-168">Her özel duruma yerelleştirilmiş bir dize iletisi ekleyin</span><span class="sxs-lookup"><span data-stu-id="a7ed5-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="a7ed5-169">Kullanıcının gördüğü hata iletisi, özel durum sınıfının adından değil, oluşturulan özel durumun <xref:System.Exception.Message?displayProperty=nameWithType> özelliğinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="a7ed5-170">Genellikle, ileti dizesini bir [özel durum oluşturucusunun](xref:System.Exception.%23ctor%2A)`message` bağımsız değişkenine geçirerek <xref:System.Exception.Message?displayProperty=nameWithType> özelliğine bir değer atarsınız.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="a7ed5-171">Yerelleştirilmiş uygulamalar için, uygulamanızın oluşturabildiğini her özel durum için yerelleştirilmiş bir ileti dizesi sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="a7ed5-172">Yerelleştirilmiş hata iletileri sağlamak için kaynak dosyalarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="a7ed5-173">Uygulamaları Yerelleştirme ve yerelleştirilmiş dizeleri alma hakkında bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="a7ed5-173">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="a7ed5-174">Nasıl yapılır: yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7ed5-174">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="a7ed5-175">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a7ed5-175">Resources in Desktop Apps</span></span>](../../framework/resources/index.md) 
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="a7ed5-176">Özel özel durumlarda, gerektiğinde ek özellikler sağlayın</span><span class="sxs-lookup"><span data-stu-id="a7ed5-176">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="a7ed5-177">Özel durum için ek özellikler sağlayın (özel ileti dizesine ek olarak), yalnızca ek bilgilerin yararlı olduğu bir programlama senaryosu varsa.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-177">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="a7ed5-178">Örneğin, <xref:System.IO.FileNotFoundException> <xref:System.IO.FileNotFoundException.FileName> özelliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-178">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="a7ed5-179">Yığın izlemenin yararlı olacağı şekilde throw deyimlerini yerleştirin</span><span class="sxs-lookup"><span data-stu-id="a7ed5-179">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="a7ed5-180">Yığın izlemesi özel durumun oluşturulduğu deyimden başlar ve özel durumu yakalayan `catch` bildiriminde sona erer.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-180">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="a7ed5-181">Özel durum Oluşturucu yöntemlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="a7ed5-181">Use exception builder methods</span></span>

<span data-ttu-id="a7ed5-182">Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-182">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="a7ed5-183">Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-183">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="a7ed5-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a7ed5-184">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="a7ed5-185">Bazı durumlarda, özel durumu oluşturmak için özel durumun oluşturucusunu kullanmak daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-185">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="a7ed5-186">Örnek, <xref:System.ArgumentException>gibi genel bir özel durum sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-186">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="a7ed5-187">Yöntemler özel durumlar nedeniyle tamamlanmadığınızda durumu geri yükle</span><span class="sxs-lookup"><span data-stu-id="a7ed5-187">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="a7ed5-188">Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-188">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="a7ed5-189">Örneğin, bir hesaptan withdrawing ve başka bir hesapta bir özel durum oluşturan bir kod varsa ve depozito yürütülürken bir özel durum oluşturulursa, çekme al 'nın etkin kalmasını istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-189">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

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

<span data-ttu-id="a7ed5-190">Yukarıdaki yöntem, doğrudan özel durum oluşturmaz, ancak depozito işlemi başarısız olursa, çekme işleminin ters çevrilmesiyle yeniden savunma yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-190">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="a7ed5-191">Bu durumu işlemenin bir yolu, depozito işlemi tarafından oluşturulan tüm özel durumları yakalamak ve geri alma işlemini geri almak olur.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-191">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="a7ed5-192">Bu örnek, özgün özel durumu yeniden oluşturmak için `throw` kullanımını gösterir, bu da çağıranların <xref:System.Exception.InnerException> özelliğini incelemek zorunda kalmadan sorunun gerçek nedenini görmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-192">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="a7ed5-193">Diğer bir seçenek de yeni bir özel durum oluşturmak ve asıl özel durumu iç özel durum olarak içerkullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="a7ed5-193">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a7ed5-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7ed5-194">See also</span></span>

- [<span data-ttu-id="a7ed5-195">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a7ed5-195">Exceptions</span></span>](index.md)
