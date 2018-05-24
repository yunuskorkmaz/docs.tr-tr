---
title: C# 6 - C# Kılavuzu yenilikler nelerdir?
description: C# sürüm 6'deki yeni özelliklerin öğrenin
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: d9f5c5ca94c04a873e4e98863f9fea3b8f477c1c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="a0d61-103">C# 6 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="a0d61-103">What's New in C# 6</span></span>

<span data-ttu-id="a0d61-104">C# 6.0 yayın geliştiriciler için verimliliğini artıran birçok özellik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a0d61-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="a0d61-105">Bu sürümdeki özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a0d61-105">Features in this release include:</span></span>

* <span data-ttu-id="a0d61-106">[Salt okunur otomatik özellikleri](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="a0d61-106">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="a0d61-107">Salt okunur otomatik yalnızca kurucularda ayarlanabilecek özelliklerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="a0d61-108">[Otomatik özelliği başlatıcıları](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="a0d61-108">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="a0d61-109">Bir otomatik özelliğinin ilk değeri ayarlamak için başlatma ifadeler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="a0d61-110">[İşlev ifadesi bodied üyeleri](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="a0d61-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="a0d61-111">Lambda ifadeleri kullanma tek satır yöntemleri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="a0d61-112">[statik kullanarak](#using-static):</span><span class="sxs-lookup"><span data-stu-id="a0d61-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="a0d61-113">Tek bir sınıfın tüm yöntemleri geçerli ad alanı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="a0d61-114">[Null - Koşullu işleçler](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="a0d61-114">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="a0d61-115">Null ile null koşullu işleç için hala denetlenirken bir nesnenin üyelerine yönelik olarak kısaca ve güvenli bir şekilde erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="a0d61-116">[Dize ilişkilendirme](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="a0d61-116">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="a0d61-117">Satır içi ifadeler yerine konumsal bağımsız değişkenler kullanarak ifadeleri biçimlendirme dizesi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="a0d61-118">[Özel durum filtreleri](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="a0d61-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="a0d61-119">Özel durum veya diğer program durumunu bir özelliğe göre ifadeler yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="a0d61-120">[nameof ifadeleri](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="a0d61-120">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="a0d61-121">Simgeler dize temsilini oluşturmak derleyici izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="a0d61-122">[catch await ve son olarak engeller](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="a0d61-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="a0d61-123">Kullanabileceğiniz `await` daha önce bunları izin verilmeyen konumları ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="a0d61-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="a0d61-124">[Dizin başlatıcıları](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="a0d61-124">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="a0d61-125">Başlatma ifadeleri sıralı kapsayıcıları yanı sıra ilişkilendirilebilir kapsayıcıları için yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="a0d61-126">[Koleksiyon başlatıcıları için genişletme yöntemleri](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="a0d61-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="a0d61-127">Koleksiyon başlatıcıları üye yöntemleri yanı sıra erişilebilir uzantı yöntemleri güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="a0d61-128">[Geliştirilmiş aşırı yükleme çözünürlüğü](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="a0d61-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="a0d61-129">Belirsiz yöntem çağrılarını şimdi daha önce oluşturulan bazı yapıları doğru şekilde çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="a0d61-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="a0d61-130">Genel bu özelliklerin de daha okunabilir daha kısa kod yazma etkisidir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-130">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="a0d61-131">Birçok ortak uygulamalar için daha az seremoni sözdizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a0d61-131">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="a0d61-132">Daha az seremoni ile tasarım hedefi görmek daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-132">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="a0d61-133">Bu özellikler de öğrenin ve daha üretken, daha okunabilir kod yazın ve daha dil yapıları, çekirdek özellikleri yoğunlaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-133">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="a0d61-134">Bu konunun geri kalanında bu özelliklerin her biri hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-134">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="a0d61-135">Otomatik özellik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="a0d61-135">Auto-Property enhancements</span></span> 

<span data-ttu-id="a0d61-136">Otomatik uygulanan özellikler (genellikle 'otomatik-Özellikler' adlandırılır) sözdizimi yaptığı basit get vardı özellikleri oluşturmak çok kolay ve erişimciler ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="a0d61-136">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="a0d61-137">Ancak, bu basit sözdizimi otomatik özelliklerini kullanarak destekleyebilir tasarımları türlerini sınırlı.</span><span class="sxs-lookup"><span data-stu-id="a0d61-137">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="a0d61-138">Daha fazla senaryolarda kullanabilmeleri C# 6 otomatik özellikleri yeteneklerini artırır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-138">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="a0d61-139">Geri dönüş bildirme ve kadar sık yedekleme alanını el ile düzenleme hakkında daha ayrıntılı sözdizimi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a0d61-139">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="a0d61-140">Yeni sözdizimini senaryoları salt okunur özellikler ve değişken depolama otomatik özelliği arkasında başlatma yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-140">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="a0d61-141">Salt okunur otomatik özellikleri</span><span class="sxs-lookup"><span data-stu-id="a0d61-141">Read-only auto-properties</span></span>

<span data-ttu-id="a0d61-142">*Salt okunur otomatik özelliklerini* değişmez türleri oluşturmak için daha kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-142">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="a0d61-143">Özel ayarlayıcılar bildirmek için en yakın önceki sürümlerinde, C# değişmez türlerine alabilir oluştu:</span><span class="sxs-lookup"><span data-stu-id="a0d61-143">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="a0d61-144">Bu sözdizimini kullanarak, derleyici türü gerçekten değişmez garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="a0d61-144">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="a0d61-145">Onu yalnızca, zorlar `FirstName` ve `LastName` sınıfı dışında herhangi bir koddan özellikleri değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="a0d61-145">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="a0d61-146">Salt okunur otomatik özellikler doğru salt okunur davranışını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-146">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="a0d61-147">Otomatik özelliği yalnızca bir get erişimcisine bildirin:</span><span class="sxs-lookup"><span data-stu-id="a0d61-147">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="a0d61-148">`FirstName` Ve `LastName` özellikleri yalnızca bir oluşturucu gövdesinde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="a0d61-148">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="a0d61-149">Ayarlanmaya çalışılırken `LastName` içinde başka bir yöntem oluşturur bir `CS0200` derleme hatası:</span><span class="sxs-lookup"><span data-stu-id="a0d61-149">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="a0d61-150">Bu özellik sabit türleri daha kısa ve uygun otomatik özelliği sözdizimini kullanarak doğru dil için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-150">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="a0d61-151">Otomatik özelliği başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="a0d61-151">Auto-Property Initializers</span></span>

<span data-ttu-id="a0d61-152">*Otomatik özelliği başlatıcıları* özellik bildirimi bir parçası olarak bir otomatik özelliğinin ilk değeri bildirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-152">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="a0d61-153">Önceki sürümlerde, bu özellikleri ayarlayıcılar olması gerekir ve yedekleme alanı tarafından kullanılan veri depolama alanı başlatmak için bu ayarlayıcı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-153">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="a0d61-154">Bu sınıf adı ve öğrencinin dereceleri listesini içeren bir öğrenci için göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a0d61-154">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="a0d61-155">Bu sınıf büyüdükçe, diğer oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-155">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="a0d61-156">Bu alan başlatmak her Oluşturucusu gerekiyor veya hatalara neden.</span><span class="sxs-lookup"><span data-stu-id="a0d61-156">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="a0d61-157">C# 6 otomatik özelliği otomatik özellik bildirimi tarafından kullanılan depolama alanı için bir başlangıç değeri atamanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="a0d61-157">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="a0d61-158">`Grades` Üyesi olduğu bildirilmiş başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-158">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="a0d61-159">Tam olarak bir kez başlatma işlemini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-159">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="a0d61-160">Başlatma için ortak arabirimi ile depolama ayırma eşitlemek daha kolay özellik bildirimi parçası olan `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a0d61-160">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="a0d61-161">Özellik başlatıcıları gösterildiği gibi salt okunur özellikler yanı sıra okuma/yazma özellikleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-161">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="a0d61-162">İşlev ifadesi bodied üyeleri</span><span class="sxs-lookup"><span data-stu-id="a0d61-162">Expression-bodied function members</span></span>

<span data-ttu-id="a0d61-163">Biz yazma üyeleri çok gövdesi bir ifade olarak temsil edilebilir yalnızca bir deyim oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-163">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="a0d61-164">Bunun yerine bir ifade bodied üye yazarak o sözdizimi azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-164">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="a0d61-165">Bu yöntemleri ve salt okunur özellikler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-165">It works for methods and read-only properties.</span></span> <span data-ttu-id="a0d61-166">Örneğin, bir geçersiz kılma `ToString()` genellikle mükemmel bir adaydır:</span><span class="sxs-lookup"><span data-stu-id="a0d61-166">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="a0d61-167">İfade bodied üyeleri de salt okunur özellikler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0d61-167">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="a0d61-168">statik kullanma</span><span class="sxs-lookup"><span data-stu-id="a0d61-168">using static</span></span>

<span data-ttu-id="a0d61-169">*Statik kullanarak* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-169">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="a0d61-170">Daha önce `using` beyanının içeri aktarılıp bir ad alanındaki tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="a0d61-170">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="a0d61-171">Genellikle bir sınıfın statik yöntemleri kodumuza kullanırız.</span><span class="sxs-lookup"><span data-stu-id="a0d61-171">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="a0d61-172">Art arda sınıf adını yazarak kodunuzu anlamını soyutlamaması.</span><span class="sxs-lookup"><span data-stu-id="a0d61-172">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="a0d61-173">Birçok sayısal hesaplamalar sınıfları yazdığınızda, ortak bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-173">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="a0d61-174">Kodunuz ile littered <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> ve diğer çağrılar farklı yöntemlere <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0d61-174">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="a0d61-175">Yeni `using static` sözdizimi yapabilir bu sınıfların çok temizleyici okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="a0d61-175">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="a0d61-176">Kullanmakta olduğunuz sınıfı belirtin:</span><span class="sxs-lookup"><span data-stu-id="a0d61-176">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="a0d61-177">Ve şimdi, tüm statik yönteminde kullanabilirsiniz <xref:System.Math> niteleme olmadan sınıfı <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0d61-177">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="a0d61-178"><xref:System.Math> Sınıfı herhangi bir örnek yöntem içermediğinden bu özellik için harika kullanımı söz konusu değildir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-178">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="a0d61-179">Aynı zamanda `using static` statik olan bir sınıfı için bir sınıfın statik yöntemleri alıp yöntemleri örneği.</span><span class="sxs-lookup"><span data-stu-id="a0d61-179">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="a0d61-180">En yararlı örnekler biri <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="a0d61-180">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="a0d61-181">Tam sınıf adını kullanmalısınız `System.String` statik olarak using deyimi.</span><span class="sxs-lookup"><span data-stu-id="a0d61-181">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="a0d61-182">Kullanamazsınız `string` anahtar sözcüğü yerine.</span><span class="sxs-lookup"><span data-stu-id="a0d61-182">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="a0d61-183">Tanımlanan statik yöntemler çağırabilirsiniz <xref:System.String> bu yöntemleri o sınıfın bir üyesi olarak niteleme olmadan sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a0d61-183">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="a0d61-184">`static using` Özelliği ve uzantı yöntemleri ilginç şekillerde etkileşim ve özellikle bu etkileşimler adres bazı kurallar dil tasarım dahil.</span><span class="sxs-lookup"><span data-stu-id="a0d61-184">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="a0d61-185">Varolan önemli değişiklikler herhangi olasılığını en aza indirmek için sizin de dahil olmak üzere olarak kullanılabilecek kod temeli hedeftir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-185">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="a0d61-186">Bir statik yöntem olarak değil çağrıldığında uzantı yöntemi çağırma sözdizimini kullanarak çağrıldığında kapsamında uzantı yöntemleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-186">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="a0d61-187">Bu LINQ sorguları genellikle görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-187">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="a0d61-188">İçeri aktararak LINQ düzeni aktarabilirsiniz <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="a0d61-188">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="a0d61-189">Bu tüm yöntemleri alır <xref:System.Linq.Enumerable> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0d61-189">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="a0d61-190">Ancak, genişletme yöntemleri genişletme yöntemleri olarak çağrıldığında kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-190">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="a0d61-191">Statik yöntem sözdizimi kullanılarak çağrılır varsa bunlar kapsamında değildir:</span><span class="sxs-lookup"><span data-stu-id="a0d61-191">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="a0d61-192">Genişletme yöntemleri, genellikle uzantı yöntemi çağırma ifadeler kullanarak denir çünkü bu bir karardır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-192">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="a0d61-193">Bunlar statik yöntemini kullanarak burada adlandırılır nadir durumda karışıklığı çözmek için olan sözdizimi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a0d61-193">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="a0d61-194">Sınıf adı çağırma bir parçası olarak gerektiren akıllıca gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="a0d61-194">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="a0d61-195">Bir son özelliğini yok `static using`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-195">There's one last feature of `static using`.</span></span> <span data-ttu-id="a0d61-196">`static using` Yönergesi de tüm iç içe geçmiş türler alır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-196">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="a0d61-197">Bu tüm iç içe geçmiş türler niteliğe olmadan başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-197">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="a0d61-198">Null-conditional işleçleri</span><span class="sxs-lookup"><span data-stu-id="a0d61-198">Null-conditional operators</span></span>

<span data-ttu-id="a0d61-199">Null değerler kod zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-199">Null values complicate code.</span></span> <span data-ttu-id="a0d61-200">Her erişim değişkenlerinin değil başvurusunun kaldırılmasının emin olmak için kontrol etmeniz `null`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-200">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="a0d61-201">*Null koşullu işleç* bu denetimlerini çok daha kolay ve akıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-201">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="a0d61-202">Üye erişimi yalnızca Değiştir `.` ile `?.`:</span><span class="sxs-lookup"><span data-stu-id="a0d61-202">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="a0d61-203">Önceki örnekte, değişken `first` atanan `null` kişi nesne ise `null`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-203">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="a0d61-204">Değeri, aksi takdirde, atanan `FirstName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a0d61-204">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="a0d61-205">En önemlisi, `?.` Bu kod satırı oluşturmayacak anlamına gelir bir `NullReferenceException` zaman `person` değişken `null`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-205">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="a0d61-206">Bunun yerine, short-circuits ve üreten `null`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-206">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="a0d61-207">Ayrıca, bu deyim döndürür Not bir `string`değerinin ne olursa olsun `person`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-207">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="a0d61-208">Kestirmeler, söz konusu olduğunda `null` tam ifadeyle eşleşecek döndürülen değeri belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="a0d61-208">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="a0d61-209">Bu yapı ile genellikle kullanabilirsiniz *null birleştirmesi* özelliklerinden biri olduğunda, varsayılan değerleri atamak için işleci `null`:</span><span class="sxs-lookup"><span data-stu-id="a0d61-209">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="a0d61-210">Sağ taraftaki yan işleneni `?.` işleci özellikler veya alanlar için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-210">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="a0d61-211">Koşullu yöntemleri çağırmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-211">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="a0d61-212">Üye işlevleri null koşullu işleç ile en yaygın kullanımı güvenle temsilciler (veya olay işleyicileri) çağırmaktır olabilecek `null`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-212">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="a0d61-213">Siz temsilcinin çağırarak gerçekleştirirsiniz `Invoke` yöntemini kullanarak `?.` üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="a0d61-213">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="a0d61-214">Bir örneğe bakın</span><span class="sxs-lookup"><span data-stu-id="a0d61-214">You can see an example in the</span></span>  
<span data-ttu-id="a0d61-215">[desenler temsilci](../delegates-patterns.md#handling-null-delegates) konu.</span><span class="sxs-lookup"><span data-stu-id="a0d61-215">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="a0d61-216">Kurallarına `?.` işleci olun işlecinin sol taraftaki yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-216">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="a0d61-217">Bu önemlidir ve olay işleyicilerini kullanarak örnek dahil olmak üzere birçok deyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-217">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="a0d61-218">Olay işleyici kullanımıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="a0d61-218">Let's start with the event handler usage.</span></span> <span data-ttu-id="a0d61-219">Önceki sürümlerinde C#, aşağıdakine benzer bir kod yazmak için önerilir:</span><span class="sxs-lookup"><span data-stu-id="a0d61-219">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="a0d61-220">Bu, daha basit bir söz dizimi tercih edilen:</span><span class="sxs-lookup"><span data-stu-id="a0d61-220">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="a0d61-221">Önceki örnekte bir yarış durumu sunar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-221">The preceding example introduces a race condition.</span></span> <span data-ttu-id="a0d61-222">`SomethingHappened` Olay karşı işaretlendiğinde aboneleri olabilir `null`, ve olay tetiklenir önce bu aboneleri kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-222">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="a0d61-223">Neden bir <xref:System.NullReferenceException> oluşturulmasına.</span><span class="sxs-lookup"><span data-stu-id="a0d61-223">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="a0d61-224">Bu ikinci sürümünde `SomethingHappened` olay işleyicisi sınandığında null olmayan olabilir, ancak başka bir kod bir işleyici kaldırırsa, olay işleyicisi çağrıldığında hala null olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-224">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="a0d61-225">Derleyici için kod oluşturur `?.` sol tarafındaki sağlar işleci (`this.SomethingHappened`), `?.` ifade kez değerlendirilir ve sonucu önbelleğe alınır:</span><span class="sxs-lookup"><span data-stu-id="a0d61-225">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="a0d61-226">Sol tarafta yalnızca bir kez değerlendirilir sağlama da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanabilmenizi sağlar `?.` bu yan etkileri sahip olsa bile yan etkileri yalnızca bir kez gerçekleşebilir, yani bir kez değerlendirilme.</span><span class="sxs-lookup"><span data-stu-id="a0d61-226">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="a0d61-227">Bizim içerik örnek görebilirsiniz [olayları](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="a0d61-227">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="a0d61-228">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="a0d61-228">String Interpolation</span></span>

<span data-ttu-id="a0d61-229">C# 6 bir biçim dizesi ve diğer dize değerlerini üretmek için değerlendirilen bir ifade dizelerden oluşturmak için yeni sözdizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a0d61-229">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="a0d61-230">Konumsal parametreler gibi bir yöntem kullanmak için gereken geleneksel olarak, `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="a0d61-230">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="a0d61-231">C# 6, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği Biçim dizesinde ifade katıştırma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-231">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="a0d61-232">Yalnızca dizesiyle yazdığınızdan `$`:</span><span class="sxs-lookup"><span data-stu-id="a0d61-232">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="a0d61-233">Bu ilk örnek özellik ifadeleri değiştirilen ifadeleri için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-233">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="a0d61-234">Herhangi bir ifade kullanmak için bu sözdizimini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-234">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="a0d61-235">Örneğin, öğrencinin Not noktası ortalaması ilişkilendirme bir parçası olarak işlem:</span><span class="sxs-lookup"><span data-stu-id="a0d61-235">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="a0d61-236">Önceki örnekte çalışan, size, çıktı için bulur `Grades.Average()` istediğiniz olandan daha fazla ondalık hane olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-236">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="a0d61-237">Dize ilişkilendirme sözdizimi tüm biçim dizeleri kullanılabilir önceki biçimlendirme yöntemlerine kullanılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="a0d61-237">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="a0d61-238">Biçim dizeleri kaşlı ayraçlar içinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0d61-238">You add the format strings inside the braces.</span></span> <span data-ttu-id="a0d61-239">Ekleme bir `:` ifade biçimlendirmek için aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="a0d61-239">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="a0d61-240">Önceki kod satırı ile değeri biçimlendirir `Grades.Average()` iki ondalık basamak içeren bir kayan noktalı sayı olarak.</span><span class="sxs-lookup"><span data-stu-id="a0d61-240">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="a0d61-241">`:` Her zaman biçimlendirilen ifadesi ve biçim dizesi arasındaki ayırıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-241">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="a0d61-242">İfadeniz kullandığında, bu sorunları ortaya çıkarabilir bir `:` koşullu bir işleç gibi başka bir şekilde:</span><span class="sxs-lookup"><span data-stu-id="a0d61-242">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="a0d61-243">Önceki örnekte `:` koşullu işleç parçası olmayan biçim dizesi başlayan olarak ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-243">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="a0d61-244">Burada bu gerçekleşir tüm durumlarda ifade düşündüğünüz olarak ifade yorumlamaya derleyici zorlamak için parantez ile çevreleyen:</span><span class="sxs-lookup"><span data-stu-id="a0d61-244">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="a0d61-245">Kaşlı ayraç yerleştirebilirsiniz ifadeleri sınırlamalar değil.</span><span class="sxs-lookup"><span data-stu-id="a0d61-245">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="a0d61-246">Karmaşık bir LINQ Sorgu sonucu görüntülemek ve hesaplamalar gerçekleştirmek için Ara değerli bir dize içinde çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0d61-246">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="a0d61-247">Bir dize ilişkilendirme ifadesi başka bir dize ilişkilendirme deyimi içinde bile geçirebilmenize bu örnekten görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-247">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="a0d61-248">Bu örnek daha daha karmaşık üretim kodunda istersiniz olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-248">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="a0d61-249">Bunun yerine, yalnızca tanım özellik derecesini.</span><span class="sxs-lookup"><span data-stu-id="a0d61-249">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="a0d61-250">Ara değerli bir dize süslü ayraçlar arasında herhangi bir C# ifade yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-250">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="a0d61-251">Dize ilişkilendirme ve belirli kültürler</span><span class="sxs-lookup"><span data-stu-id="a0d61-251">String interpolation and specific cultures</span></span>

<span data-ttu-id="a0d61-252">Önceki bölümde gösterilen tüm örnekler burada kodu yürütür makinede dil ve geçerli kültürü kullanarak dizeleri biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="a0d61-252">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="a0d61-253">Genellikle bir kültürü kullanarak üretilen dize biçiminde gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-253">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="a0d61-254">Bunu yapmak için dize ilişkilendirme tarafından üretilen nesnesi örtük olarak dönüştürülebilir olgu kullanın <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="a0d61-254">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="a0d61-255"><xref:System.FormattableString> Örnek biçim dizesi ve dizeleri dönüştürme önce ifadeleri değerlendirme sonuçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-255">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="a0d61-256">Ortak yöntemlerini kullanabilirsiniz <xref:System.FormattableString> bir dize biçimlendirme sırasında kültür belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a0d61-256">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="a0d61-257">Örneğin, aşağıdaki örnekte, Almanca kültürü kullanarak bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-257">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="a0d61-258">(İçin ondalık ayırıcı, ',' karakterini kullanır ve '.' karakteri olarak binlik ayırıcı.)</span><span class="sxs-lookup"><span data-stu-id="a0d61-258">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="a0d61-259">Daha fazla bilgi için bkz: [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu.</span><span class="sxs-lookup"><span data-stu-id="a0d61-259">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="a0d61-260">Özel durum filtreleri</span><span class="sxs-lookup"><span data-stu-id="a0d61-260">Exception Filters</span></span>

<span data-ttu-id="a0d61-261">C# 6 başka bir yeni özelliği *özel durum filtreleri*.</span><span class="sxs-lookup"><span data-stu-id="a0d61-261">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="a0d61-262">Özel durum filtreleri verilen catch yan tümcesinin ne zaman uygulanacağını belirleme tümceler var.</span><span class="sxs-lookup"><span data-stu-id="a0d61-262">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="a0d61-263">Bir özel durum filtresi için kullanılan ifade değerlendiren varsa `true`, catch yan tümcesi, özel durum normal işleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-263">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="a0d61-264">İfade değerlendirilirse `false`, sonra `catch` yan tümcesi atlandı.</span><span class="sxs-lookup"><span data-stu-id="a0d61-264">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="a0d61-265">Bir kullanım olduğunu belirlemek için bir özel durum bilgilerini incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="a0d61-265">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="a0d61-266">Özel durum filtreleri tarafından oluşturulan kodu oluşturulur ve işlenmemiş bir özel durum hakkında daha iyi bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-266">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="a0d61-267">Özel durum filtreleri diline eklenmeden önce aşağıdaki gibi bir kod oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a0d61-267">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="a0d61-268">Özel değişiklikler bu iki örnek arasında olduğu durum noktası.</span><span class="sxs-lookup"><span data-stu-id="a0d61-268">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="a0d61-269">Önceki kodda, burada bir `throw` yan tümcesi kullanıldığında, özel durumu, herhangi bir yığın izleme çözümlemesi veya kilitlenme bilgi dökümleri incelenmesi gösterecektir `throw` catch yan tümcesi deyiminde.</span><span class="sxs-lookup"><span data-stu-id="a0d61-269">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="a0d61-270">Gerçek özel durum nesnesi özgün çağrı yığını içerir, ancak bu throw noktası ve özgün throw noktasının konumunu arasında çağrı yığınında tüm değişkenleri hakkında diğer tüm bilgiler kaybolmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-270">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="a0d61-271">Bir özel durum filtresi kullanarak kodu nasıl işleneceğini ile karşılaştırın: özel durum filtre ifadesi değerlendiren `false`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-271">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="a0d61-272">Bu nedenle, yürütme hiçbir zaman girer `catch` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a0d61-272">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="a0d61-273">Çünkü `catch` yan tümcesi yürütülmez, hiçbir yığın geriye doğru izleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-273">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="a0d61-274">Anlamına gelir özgün konum throw daha sonra gerçekleşmesi hata ayıklama etkinlikler için korunur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-274">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="a0d61-275">Alanları veya yalnızca özel durum türü üzerinde kalmak yerine bir özel durum özelliklerini değerlendirmek gerektiğinde daha fazla hata ayıklama bilgilerini korumak için bir özel durum filtresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0d61-275">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="a0d61-276">Özel durum filtreleri önerilen başka bir desenle günlük yordamları için bunları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-276">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="a0d61-277">Bu kullanım da, özel durum throw noktası korunur bir özel durum filtresi olarak değerlendirildiğinde şekilde yararlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-277">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="a0d61-278">Günlüğe kayıt yöntemi, bağımsız değişkeni olan koşulsuz olarak döndüren özel bir yöntem olacaktır `false`:</span><span class="sxs-lookup"><span data-stu-id="a0d61-278">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="a0d61-279">Bir özel durum günlüğe kaydetmek istediğiniz her bir catch yan tümcesi ekleyin ve bu yöntemi özel durum filtre olarak kullanın:</span><span class="sxs-lookup"><span data-stu-id="a0d61-279">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="a0d61-280">Özel durumlar hiçbir zaman, çünkü yakalanan `LogException` yöntem her zaman döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-280">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="a0d61-281">Bu her zaman yanlış özel durum filtresi anlamına gelir, bu günlüğü işleyicisi herhangi bir özel durum işleyicileri önce yerleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0d61-281">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="a0d61-282">Önceki örnekte bir özel durum filtreleri güvenliğin çok önemli vurgular.</span><span class="sxs-lookup"><span data-stu-id="a0d61-282">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="a0d61-283">Özel durum filtreleri daha genel bir özel durum catch yan tümcesi önce daha belirli bir yere görünebilir senaryoları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a0d61-283">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="a0d61-284">Birden çok catch tümcelerinde yer aynı özel durum türü olması mümkündür:</span><span class="sxs-lookup"><span data-stu-id="a0d61-284">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="a0d61-285">Başka bir önerilen deseni, bir hata ayıklayıcısı ekli özel durumları işleme catch yan tümceleri önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-285">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="a0d61-286">Bu teknik hata ayıklayıcısı ile bir uygulamayı çalıştırın ve bir özel durum yakalandığında yürütme durdurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-286">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="a0d61-287">Böylece yalnızca bir hata ayıklayıcısı değil iliştirildiğinde herhangi bir kurtarma kodu yürütür, kodunuzda bir özel durum filtresi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a0d61-287">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="a0d61-288">Bu kodda ekledikten sonra tüm işlenmeyen özel durumlarını ayırmak için hata ayıklayıcı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a0d61-288">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="a0d61-289">Hata ayıklayıcı altında programını çalıştırın ve hata ayıklayıcısı sonları her `PerformFailingOperation()` oluşturur bir `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-289">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="a0d61-290">Catch yan tümcesi nedeniyle false döndüren özel durum filtresi yürütülen olmaz çünkü hata ayıklayıcı programınızın keser.</span><span class="sxs-lookup"><span data-stu-id="a0d61-290">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="a0d61-291">`nameof` İfadeler</span><span class="sxs-lookup"><span data-stu-id="a0d61-291">`nameof` Expressions</span></span>

<span data-ttu-id="a0d61-292">`nameof` Bir simge adı için ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-292">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="a0d61-293">Bir değişken, bir özellik veya bir üye alanı adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-293">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="a0d61-294">En yaygın birini kullanan için `nameof` bir özel duruma neden bir sembol adını sağlar:</span><span class="sxs-lookup"><span data-stu-id="a0d61-294">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="a0d61-295">Başka bir uygulama temel XAML uygulamaları ile kullanılır `INotifyPropertyChanged` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="a0d61-295">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="a0d61-296">Kullanmanın avantajı `nameof` bir sabit dize üzerinden işlecidir araçları simgenin anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d61-296">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="a0d61-297">Simgenin yeniden adlandırmak için yeniden düzenleme araçları kullanırsanız, içindeki adlandıracak `nameof` ifade.</span><span class="sxs-lookup"><span data-stu-id="a0d61-297">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="a0d61-298">Sabit Dizeler Bu avantajı yok.</span><span class="sxs-lookup"><span data-stu-id="a0d61-298">Constant strings don't have that advantage.</span></span> <span data-ttu-id="a0d61-299">Sık kullanılan düzenleyicinizde kendiniz deneyin: bir değişken ve herhangi bir yeniden adlandırma `nameof` ifadeler de güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-299">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="a0d61-300">`nameof` İfade bağımsız değişkeni nitelenmemiş adı üretir (`LastName` önceki örneklerde) dahi bağımsız değişkeni için tam ad kullanın:</span><span class="sxs-lookup"><span data-stu-id="a0d61-300">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="a0d61-301">Bu `nameof` ifade üretir `FirstName`değil `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-301">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="a0d61-302">Catch await ve son olarak engeller</span><span class="sxs-lookup"><span data-stu-id="a0d61-302">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="a0d61-303">C# 5 vardı nereye geçici bazı sınırlamaları `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="a0d61-303">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="a0d61-304">Bunlardan birini C# 6'kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a0d61-304">One of those has been removed in C# 6.</span></span> <span data-ttu-id="a0d61-305">Artık kullanabilirsiniz `await` içinde `catch` veya `finally` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="a0d61-305">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="a0d61-306">Eklenmesi await catch ifadelerinde ve finally blokları olanlar nasıl işlendiği karmaşık hale gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-306">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="a0d61-307">Bu görünme tartışmak için örnek ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="a0d61-307">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="a0d61-308">Herhangi bir zaman uyumsuz yöntem bekleme deyimde kullanabileceğiniz bir finally yan tümcesinin.</span><span class="sxs-lookup"><span data-stu-id="a0d61-308">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="a0d61-309">C# 6 catch ifadelerinde beklemek.</span><span class="sxs-lookup"><span data-stu-id="a0d61-309">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="a0d61-310">Bu günlük kaydı senaryoları ile en sık kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a0d61-310">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="a0d61-311">Eklemek için uygulama ayrıntılarını `await` içinde destek `catch` ve `finally` yan tümceleri davranışı zaman uyumlu bir kod davranışını ile tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d61-311">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="a0d61-312">Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturur, yürütme için uygun bir arar `catch` yan tümcesinde sonraki çevresindeki bloğu.</span><span class="sxs-lookup"><span data-stu-id="a0d61-312">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="a0d61-313">Geçerli bir özel durum varsa, bu özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-313">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="a0d61-314">Beklemenin ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.</span><span class="sxs-lookup"><span data-stu-id="a0d61-314">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="a0d61-315">Bu davranış önerilen yazmak için nedeni `catch` ve `finally` yan tümceleri dikkatle, yeni özel durumları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="a0d61-315">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="a0d61-316">Dizin başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="a0d61-316">Index Initializers</span></span>

<span data-ttu-id="a0d61-317">*Dizin başlatıcıları* koleksiyon başlatıcıları daha tutarlı hale iki özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-317">*Index Initializers* is one of two features that make collection initializers more consistent.</span></span> <span data-ttu-id="a0d61-318">Önceki sürümlerinde, C#, kullanabileceğinizi *koleksiyon başlatıcıları* dizisi stili koleksiyonlarıyla yalnızca:</span><span class="sxs-lookup"><span data-stu-id="a0d61-318">In earlier releases of C#, you could use *collection initializers* only with sequence style collections:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="a0d61-319">Şimdi, ayrıca bunları ile kullanabileceğiniz <xref:System.Collections.Generic.Dictionary%602> koleksiyonları ve benzer türleri:</span><span class="sxs-lookup"><span data-stu-id="a0d61-319">Now, you can also use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="a0d61-320">Bu özellik ilişkilendirilebilir kapsayıcıları ne birkaç sürümleri için dizisi kapsayıcıları için yerinde bırakıldı için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-320">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="a0d61-321">Uzantı `Add` koleksiyon başlatıcıları yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a0d61-321">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="a0d61-322">Kullanma yeteneğini koleksiyonu başlatma kolaylaştırır başka bir özellik olan bir *genişletme yöntemi* için `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a0d61-322">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="a0d61-323">Bu özellik, Visual Basic ile eşlik için eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-323">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="a0d61-324">Bir yöntem anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip olan bir özel koleksiyon sınıfı olduğunda en kullanışlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-324">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="a0d61-325">Örneğin, şöyle Öğrenciler koleksiyonu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a0d61-325">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="a0d61-326">`Enroll` Yöntemi öğrencinin ekler.</span><span class="sxs-lookup"><span data-stu-id="a0d61-326">The `Enroll` method adds a student.</span></span> <span data-ttu-id="a0d61-327">Ancak bunu IU `Add` düzeni.</span><span class="sxs-lookup"><span data-stu-id="a0d61-327">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="a0d61-328">Önceki sürümlerde, C# ile koleksiyon başlatıcıları kullanılamadı bir `Enrollment` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="a0d61-328">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="a0d61-329">Artık, ancak yalnızca eşleyen bir genişletme yöntemi oluşturursanız `Add` için `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="a0d61-329">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="a0d61-330">Bu özellik ile yapmakta olduğunuz hangi yöntemi adlı bir yöntem bir koleksiyona öğe ekler eşlemektir `Add` bir genişletme yöntemi oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="a0d61-330">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="a0d61-331">Geliştirilmiş aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="a0d61-331">Improved overload resolution</span></span>

<span data-ttu-id="a0d61-332">Son bu özellik, büyük olasılıkla farkına biridir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-332">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="a0d61-333">C# Derleyici'nın önceki sürümünü lambda ifadeleri belirsiz içeren bazı yöntem çağrılarını bulunduğu yapıları vardı.</span><span class="sxs-lookup"><span data-stu-id="a0d61-333">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="a0d61-334">Bu yöntem göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a0d61-334">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="a0d61-335">Önceki sürümlerde, C#, yöntemi Grup sözdizimini kullanarak bu yöntem çağırma başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="a0d61-335">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="a0d61-336">Önceki derleyici doğru arasında ayrım yapmamak `Task.Run(Action)` ve `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="a0d61-336">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="a0d61-337">Önceki sürümlerde, bağımsız değişken olarak bir lambda ifadesi kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a0d61-337">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="a0d61-338">C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="a0d61-338">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>
