---
title: Boş değer atanabilir başvuru türleri
description: Bu makalede, C# 8,0 ' ye eklenen null yapılabilir başvuru türlerine ilişkin bir genel bakış sunulmaktadır. Yeni ve mevcut projeler için özelliği, null başvuru özel durumlarına karşı nasıl güvenlik sağladığını öğreneceksiniz.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 5b18aceed57be256c9996a0fa7d91cf75e1f9a0b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874530"
---
# <a name="nullable-reference-types"></a><span data-ttu-id="db2b4-104">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="db2b4-104">Nullable reference types</span></span>

<span data-ttu-id="db2b4-105">C# 8,0, başvuru türü değişkenlerinin özellikleri hakkında önemli deyimler etkinleştirmenizi sağlayan **null yapılabilir başvuru türlerini** ve **null yapılamayan başvuru türlerini** tanıtır:</span><span class="sxs-lookup"><span data-stu-id="db2b4-105">C# 8.0 introduces **nullable reference types** and **non-nullable reference types** that enable you to make important statements about the properties for reference type variables:</span></span>

- <span data-ttu-id="db2b4-106">**Başvurunun null olması gerekir**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-106">**A reference isn't supposed to be null**.</span></span> <span data-ttu-id="db2b4-107">Değişkenlerin null olması beklenen durumlarda derleyici, bu değişkenlerin null olmadığını denetlemeden emin olmak için güvenli olduğunu sağlayan kuralları zorlar:</span><span class="sxs-lookup"><span data-stu-id="db2b4-107">When variables aren't supposed to be null, the compiler enforces rules that ensure it's safe to dereference these variables without first checking that it isn't null:</span></span>
  - <span data-ttu-id="db2b4-108">Değişken null olmayan bir değere başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-108">The variable must be initialized to a non-null value.</span></span>
  - <span data-ttu-id="db2b4-109">Değişkenine hiçbir şekilde değer atanamaz `null` .</span><span class="sxs-lookup"><span data-stu-id="db2b4-109">The variable can never be assigned the value `null`.</span></span>
- <span data-ttu-id="db2b4-110">**Başvuru null olabilir**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-110">**A reference may be null**.</span></span> <span data-ttu-id="db2b4-111">Değişkenler null olabilir, derleyici null bir başvuruyu doğru bir şekilde kontrol aldığınızdan emin olmak için farklı kurallar uygular:</span><span class="sxs-lookup"><span data-stu-id="db2b4-111">When variables may be null, the compiler enforces different rules to ensure that you've correctly checked for a null reference:</span></span>
  - <span data-ttu-id="db2b4-112">Değişken yalnızca derleyici değerin null olmadığını garanti edemediğinde başvuru yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-112">The variable may only be dereferenced when the compiler can guarantee that the value isn't null.</span></span>
  - <span data-ttu-id="db2b4-113">Bu değişkenler varsayılan `null` değerle başlatılabilir ve `null` diğer koddaki değeri atanabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-113">These variables may be initialized with the default `null` value and may be assigned the value `null` in other code.</span></span>

<span data-ttu-id="db2b4-114">Bu yeni özellik, tasarım amacını değişken bildiriminden belirlenemediği önceki C# sürümlerindeki başvuru değişkenlerinin işlenmesine göre önemli avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="db2b4-114">This new feature provides significant benefits over the handling of reference variables in earlier versions of C# where the design intent can't be determined from the variable declaration.</span></span> <span data-ttu-id="db2b4-115">Derleyici, başvuru türleri için null başvuru özel durumlarına karşı güvenlik sağlamadı:</span><span class="sxs-lookup"><span data-stu-id="db2b4-115">The compiler didn't provide safety against null reference exceptions for reference types:</span></span>

- <span data-ttu-id="db2b4-116">**Başvuru null** olabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-116">**A reference can be null**.</span></span> <span data-ttu-id="db2b4-117">Bir başvuru türü değişkeni olarak başlatıldığında `null` veya daha sonra atandığında derleyici uyarı vermez `null` .</span><span class="sxs-lookup"><span data-stu-id="db2b4-117">The compiler doesn't issue warnings when a reference-type variable is initialized to `null`, or later assigned `null`.</span></span> <span data-ttu-id="db2b4-118">Derleyici, null denetimleri olmadan bu değişkenlere başvurulduğunu uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-118">The compiler issues warnings when these variables are dereferenced without null checks.</span></span>
- <span data-ttu-id="db2b4-119">**Başvurunun null olmadığı varsayılır**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-119">**A reference is assumed to be not null**.</span></span> <span data-ttu-id="db2b4-120">Başvuru türleri başvurulduğunu derleyici hiçbir uyarı vermez.</span><span class="sxs-lookup"><span data-stu-id="db2b4-120">The compiler doesn't issue any warnings when reference types are dereferenced.</span></span> <span data-ttu-id="db2b4-121">Bir değişken null olabilecek bir ifadeye ayarlandıysa, derleyici uyarıları yayınlar.</span><span class="sxs-lookup"><span data-stu-id="db2b4-121">The compiler issues warnings if a variable is set to an expression that may be null.</span></span>

<span data-ttu-id="db2b4-122">Bu uyarılar derleme zamanında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-122">These warnings are emitted at compile time.</span></span> <span data-ttu-id="db2b4-123">Derleyici null denetim veya başka çalışma zamanı yapılarını Nullable bir bağlamda eklemez.</span><span class="sxs-lookup"><span data-stu-id="db2b4-123">The compiler doesn't add any null checks or other runtime constructs in a nullable context.</span></span> <span data-ttu-id="db2b4-124">Çalışma zamanında, null yapılabilir bir başvuru ve null atanamaz bir başvuru eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-124">At runtime, a nullable reference and a non-nullable reference are equivalent.</span></span>

<span data-ttu-id="db2b4-125">Null yapılabilir başvuru türleri eklenmesiyle, amacınızı daha net bir şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-125">With the addition of nullable reference types, you can declare your intent more clearly.</span></span> <span data-ttu-id="db2b4-126">`null`Değer, bir değişkenin bir değere başvurmadığından emin olmanın doğru yoludur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-126">The `null` value is the correct way to represent that a variable doesn't refer to a value.</span></span> <span data-ttu-id="db2b4-127">Bu özelliği, kodunuzun tüm değerlerini kaldırmak için kullanmayın `null` .</span><span class="sxs-lookup"><span data-stu-id="db2b4-127">Don't use this feature to remove all `null` values from your code.</span></span> <span data-ttu-id="db2b4-128">Bunun yerine, amacınızı derleyiciye ve kodunuzu okuyan diğer geliştiricilere bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-128">Rather, you should declare your intent to the compiler and other developers that read your code.</span></span> <span data-ttu-id="db2b4-129">Amacınızı bildirerek, derleyici bu amaca tutarsız bir kod yazdığınızda size bildirir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-129">By declaring your intent, the compiler informs you when you write code that is inconsistent with that intent.</span></span>

<span data-ttu-id="db2b4-130">Null **yapılabilir bir başvuru türü** , [null yapılabilir değer türleriyle](language-reference/builtin-types/nullable-value-types.md)aynı söz dizimi kullanılarak belirtilmiştir: bir `?` değişkenin türüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-130">A **nullable reference type** is noted using the same syntax as [nullable value types](language-reference/builtin-types/nullable-value-types.md): a `?` is appended to the type of the variable.</span></span> <span data-ttu-id="db2b4-131">Örneğin, aşağıdaki değişken bildirimi null olabilen bir dize değişkenini temsil eder `name` :</span><span class="sxs-lookup"><span data-stu-id="db2b4-131">For example, the following variable declaration represents a nullable string variable, `name`:</span></span>

```csharp
string? name;
```

<span data-ttu-id="db2b4-132">`?`Tür adına eklenmemiş olmayan herhangi bir değişken, **null olamayan bir başvuru türüdür**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-132">Any variable where the `?` isn't appended to the type name is a **non-nullable reference type**.</span></span> <span data-ttu-id="db2b4-133">Bu özellik, bu özelliği etkinleştirdiğinizde var olan koddaki tüm başvuru türü değişkenlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-133">That includes all reference type variables in existing code when you've enabled this feature.</span></span>

<span data-ttu-id="db2b4-134">Derleyici, null olabilen bir başvurunun boş olmayan olarak bilinmesinin bilinmediğini anlamak için statik analizi kullanır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-134">The compiler uses static analysis to determine if a nullable reference is known to be non-null.</span></span> <span data-ttu-id="db2b4-135">Null olduğunda, null olabilen bir başvuruya başvuru yaptığınızda derleyici sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-135">The compiler warns you if you dereference a nullable reference when it may be null.</span></span> <span data-ttu-id="db2b4-136">Değişken adının ardından [null-forverme işlecini](language-reference/operators/null-forgiving.md) kullanarak bu davranışı geçersiz kılabilirsiniz `!` .</span><span class="sxs-lookup"><span data-stu-id="db2b4-136">You can override this behavior by using the [null-forgiving operator](language-reference/operators/null-forgiving.md) `!` following a variable name.</span></span> <span data-ttu-id="db2b4-137">Örneğin, `name` değişkenin null olmadığını, ancak derleyici bir uyarı olduğunu biliyorsanız, derleyicinin analizini geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db2b4-137">For example, if you know the `name` variable isn't null but the compiler issues a warning, you can write the following code to override the compiler's analysis:</span></span>

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a><span data-ttu-id="db2b4-138">Türlerin null olabilme sayısı</span><span class="sxs-lookup"><span data-stu-id="db2b4-138">Nullability of types</span></span>

<span data-ttu-id="db2b4-139">Herhangi bir başvuru türü, uyarıların ne zaman oluşturulacağını açıklayan dört adet *null* değer içerebilir:</span><span class="sxs-lookup"><span data-stu-id="db2b4-139">Any reference type can have one of four *nullabilities*, which describes when warnings are generated:</span></span>

- <span data-ttu-id="db2b4-140">Null *atanabilir olmayan*: null bu türdeki değişkenlere atanamaz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-140">*Nonnullable*: Null can't be assigned to variables of this type.</span></span> <span data-ttu-id="db2b4-141">Bu tür değişkenlerin, başvuru yapılmadan önce null olarak işaretli olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="db2b4-141">Variables of this type don't need to be null-checked before dereferencing.</span></span>
- <span data-ttu-id="db2b4-142">*Nullable*: null, bu türdeki değişkenlere atanabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-142">*Nullable*: Null can be assigned to variables of this type.</span></span> <span data-ttu-id="db2b4-143">Bu türdeki değişkenlerin başvurusunun kaldırılması, önce `null` bir uyarıya neden olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="db2b4-143">Dereferencing variables of this type without first checking for `null` causes a warning.</span></span>
- <span data-ttu-id="db2b4-144">*Yükümlülüğü*: zorunluluvou, pre-C # 8,0 durumundadır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-144">*Oblivious*: Oblivious is the pre-C# 8.0 state.</span></span> <span data-ttu-id="db2b4-145">Bu tür değişkenlere başvuru yapılmadan başvuru yapılabilir veya atanabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-145">Variables of this type can be dereferenced or assigned without warnings.</span></span>
- <span data-ttu-id="db2b4-146">*Bilinmiyor*: bilinmiyor, genellikle kısıtlamaların tür *Nullable* veya *null değer* atanabilir olması gerektiğini bildirmeyecek tür parametreleri içindir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-146">*Unknown*: Unknown is generally for type parameters where constraints don't tell the compiler that the type must be *nullable* or *nonnullable*.</span></span>

<span data-ttu-id="db2b4-147">Değişken bildirimindeki bir türün null olabilme değeri, değişkenin bildirildiği *null yapılabilir bağlam* tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-147">The nullability of a type in a variable declaration is controlled by the *nullable context* in which the variable is declared.</span></span>

## <a name="nullable-contexts"></a><span data-ttu-id="db2b4-148">Null yapılabilir bağlamlar</span><span class="sxs-lookup"><span data-stu-id="db2b4-148">Nullable contexts</span></span>

<span data-ttu-id="db2b4-149">Null yapılabilir bağlamlar, derleyicinin başvuru türü değişkenlerini nasıl yorumlayacağını öğrenmek için ayrıntılı denetimi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-149">Nullable contexts enable fine-grained control for how the compiler interprets reference type variables.</span></span> <span data-ttu-id="db2b4-150">Belirli bir kaynak çizginin **null yapılabilir ek açıklama bağlamı** etkin veya devre dışı.</span><span class="sxs-lookup"><span data-stu-id="db2b4-150">The **nullable annotation context** of any given source line is either enabled or disabled.</span></span> <span data-ttu-id="db2b4-151">Önceden C # 8,0 derleyicisini, tüm kodunuzu devre dışı bırakılmış bir null yapılabilir bağlamda derleme olarak düşünebilirsiniz: herhangi bir başvuru türü null olabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-151">You can think of the pre-C# 8.0 compiler as compiling all your code in a disabled nullable context: any reference type may be null.</span></span> <span data-ttu-id="db2b4-152">**Null yapılabilir uyarılar bağlamı** da etkinleştirilebilir veya devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-152">The **nullable warnings context** may also be enabled or disabled.</span></span> <span data-ttu-id="db2b4-153">Null yapılabilir uyarılar bağlamı, akış analizini kullanarak derleyici tarafından oluşturulan uyarıları belirtir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-153">The nullable warnings context specifies the warnings generated by the compiler using its flow analysis.</span></span>

<span data-ttu-id="db2b4-154">`Nullable` *. Csproj* dosyanızdaki öğesi kullanılarak bir proje için Nullable ek açıklama bağlamı ve null yapılabilir uyarı bağlamı ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-154">The nullable annotation context and nullable warning context can be set for a project using the `Nullable` element in your *.csproj* file.</span></span> <span data-ttu-id="db2b4-155">Bu öğe, derleyicinin türlerin null olduğunu ve hangi uyarıların oluşturulduğunu nasıl yorumlayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-155">This element configures how the compiler interprets the nullability of types and what warnings are generated.</span></span> <span data-ttu-id="db2b4-156">Geçerli ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="db2b4-156">Valid settings are:</span></span>

- <span data-ttu-id="db2b4-157">`enable`: Null yapılabilir ek açıklama bağlamı **etkin**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-157">`enable`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="db2b4-158">Null yapılabilir uyarı bağlamı **etkin**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-158">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="db2b4-159">Bir başvuru türü değişkenleri, `string` Örneğin, null değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-159">Variables of a reference type, `string` for example, are non-nullable.</span></span>  <span data-ttu-id="db2b4-160">Tüm null değer alabilirlik uyarıları etkin.</span><span class="sxs-lookup"><span data-stu-id="db2b4-160">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="db2b4-161">`warnings`: Nullable ek açıklama bağlamı **devre dışı bırakıldı**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-161">`warnings`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="db2b4-162">Null yapılabilir uyarı bağlamı **etkin**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-162">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="db2b4-163">Bir başvuru türü değişkenleri, zorunluluvou.</span><span class="sxs-lookup"><span data-stu-id="db2b4-163">Variables of a reference type are oblivious.</span></span> <span data-ttu-id="db2b4-164">Tüm null değer alabilirlik uyarıları etkin.</span><span class="sxs-lookup"><span data-stu-id="db2b4-164">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="db2b4-165">`annotations`: Null yapılabilir ek açıklama bağlamı **etkin**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-165">`annotations`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="db2b4-166">Null yapılabilir uyarı bağlamı **devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-166">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="db2b4-167">Bir başvuru türü değişkenleri, örneğin dizesi null değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-167">Variables of a reference type, string for example, are non-nullable.</span></span> <span data-ttu-id="db2b4-168">Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="db2b4-168">All nullability warnings are disabled.</span></span>
- <span data-ttu-id="db2b4-169">`disable`: Nullable ek açıklama bağlamı **devre dışı bırakıldı**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-169">`disable`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="db2b4-170">Null yapılabilir uyarı bağlamı **devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-170">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="db2b4-171">Bir başvuru türü değişkenleri, C# ' ın önceki sürümlerinde olduğu gibi, zorunluluvou 'lardır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-171">Variables of a reference type are oblivious, just like earlier versions of C#.</span></span> <span data-ttu-id="db2b4-172">Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="db2b4-172">All nullability warnings are disabled.</span></span>

<span data-ttu-id="db2b4-173">**Örnek**:</span><span class="sxs-lookup"><span data-stu-id="db2b4-173">**Example**:</span></span>

```xml
<Nullable>enable</Nullable>
```

<span data-ttu-id="db2b4-174">Ayrıca, aynı bağlamlarını projenizde her yerde ayarlamak için yönergeleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db2b4-174">You can also use directives to set these same contexts anywhere in your project:</span></span>

- <span data-ttu-id="db2b4-175">`#nullable enable`: Null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **etkin** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="db2b4-175">`#nullable enable`: Sets the nullable annotation context and nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="db2b4-176">`#nullable disable`: Nullable ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **devre dışı** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="db2b4-176">`#nullable disable`: Sets the nullable annotation context and nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="db2b4-177">`#nullable restore`: Null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını proje ayarlarına geri yükler.</span><span class="sxs-lookup"><span data-stu-id="db2b4-177">`#nullable restore`: Restores the nullable annotation context and nullable warning context to the project settings.</span></span>
- <span data-ttu-id="db2b4-178">`#nullable disable warnings`: Nullable uyarı bağlamını **devre dışı** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="db2b4-178">`#nullable disable warnings`: Set the nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="db2b4-179">`#nullable enable warnings`: Null yapılabilir uyarı bağlamını **etkin** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="db2b4-179">`#nullable enable warnings`: Set the nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="db2b4-180">`#nullable restore warnings`: Proje ayarlarına Nullable uyarı bağlamını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="db2b4-180">`#nullable restore warnings`: Restores the nullable warning context to the project settings.</span></span>
- <span data-ttu-id="db2b4-181">`#nullable disable annotations`: Nullable ek açıklama bağlamını **devre dışı** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="db2b4-181">`#nullable disable annotations`: Set the nullable annotation context to **disabled**.</span></span>
- <span data-ttu-id="db2b4-182">`#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını **etkin** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="db2b4-182">`#nullable enable annotations`: Set the nullable annotation context to **enabled**.</span></span>
- <span data-ttu-id="db2b4-183">`#nullable restore annotations`: Ek açıklama uyarı bağlamını proje ayarlarına geri yükler.</span><span class="sxs-lookup"><span data-stu-id="db2b4-183">`#nullable restore annotations`: Restores the annotation warning context to the project settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db2b4-184">Global null yapılabilir bağlam, oluşturulan kod dosyaları için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-184">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="db2b4-185">Her iki strateji kapsamında, null yapılabilir bağlam, üretilen olarak işaretlenen tüm kaynak dosyaları için *devre dışıdır* .</span><span class="sxs-lookup"><span data-stu-id="db2b4-185">Under either strategy, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="db2b4-186">Bu, oluşturulan dosyalardaki tüm API 'Lerin açıklanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-186">This means any APIs in generated files are not annotated.</span></span> <span data-ttu-id="db2b4-187">Bir dosyanın oluşturulduğu şekilde işaretlenmiş dört yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="db2b4-187">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="db2b4-188">. Editorconfig dosyasında, `generated_code = true` Bu dosya için geçerli olan bir bölümde belirtin.</span><span class="sxs-lookup"><span data-stu-id="db2b4-188">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="db2b4-189">`<auto-generated>` `<auto-generated/>` Dosyanın üst kısmına bir açıklama koyun.</span><span class="sxs-lookup"><span data-stu-id="db2b4-189">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="db2b4-190">Bu, açıklama içindeki herhangi bir satırda olabilir, ancak açıklama bloğu dosyadaki ilk öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-190">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="db2b4-191">Dosya adını *TemporaryGeneratedFile_* başlatın</span><span class="sxs-lookup"><span data-stu-id="db2b4-191">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="db2b4-192">Dosya adını *. Designer. cs*, *. generated. cs*, *. g. cs* veya *. g. ı. cs* ile sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="db2b4-192">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="db2b4-193">Oluşturucular, Önişlemci yönergesini kullanarak kabul edebilir [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md) .</span><span class="sxs-lookup"><span data-stu-id="db2b4-193">Generators can opt-in using the [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

<span data-ttu-id="db2b4-194">Varsayılan olarak, null yapılabilir ek açıklama ve uyarı bağlamları yeni projeler dahil **devre dışıdır**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-194">By default, nullable annotation and warning contexts are **disabled**, including new projects.</span></span> <span data-ttu-id="db2b4-195">Bu, mevcut kodunuzun değişiklik yapılmadan ve yeni bir uyarı oluşturmadan derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-195">That means that your existing code compiles without changes and without generating any new warnings.</span></span>

<span data-ttu-id="db2b4-196">Bu seçenekler, [mevcut bir kod temelinin](nullable-migration-strategies.md) Nullable başvuru türlerini kullanmak için iki ayrı strateji sağlar.</span><span class="sxs-lookup"><span data-stu-id="db2b4-196">These options provide two distinct strategies to [update an existing codebase](nullable-migration-strategies.md) to use nullable reference types.</span></span>

## <a name="nullable-annotation-context"></a><span data-ttu-id="db2b4-197">Null yapılabilir ek açıklama bağlamı</span><span class="sxs-lookup"><span data-stu-id="db2b4-197">Nullable annotation context</span></span>

<span data-ttu-id="db2b4-198">Derleyici, devre dışı bırakılmış bir null yapılabilir ek açıklama bağlamında aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="db2b4-198">The compiler uses the following rules in a disabled nullable annotation context:</span></span>

- <span data-ttu-id="db2b4-199">Etkin olamayan başvuruları devre dışı bir bağlamda bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-199">You can't declare nullable references in a disabled context.</span></span>
- <span data-ttu-id="db2b4-200">Tüm başvuru değişkenlerine null değeri atanabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-200">All reference variables may be assigned a value of null.</span></span>
- <span data-ttu-id="db2b4-201">Başvuru türü değişkenine başvurulduğunu bir uyarı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-201">No warnings are generated when a variable of a reference type is dereferenced.</span></span>
- <span data-ttu-id="db2b4-202">Null-forverme işleci devre dışı bir bağlamda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-202">The null-forgiving operator may not be used in a disabled context.</span></span>

<span data-ttu-id="db2b4-203">Davranış, C# ' nin önceki sürümleriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-203">The behavior is the same as previous versions of C#.</span></span>

<span data-ttu-id="db2b4-204">Derleyici, etkinleştirilmiş bir null yapılabilir ek açıklama bağlamında aşağıdaki kuralları kullanır:</span><span class="sxs-lookup"><span data-stu-id="db2b4-204">The compiler uses the following rules in an enabled nullable annotation context:</span></span>

- <span data-ttu-id="db2b4-205">Başvuru türündeki herhangi bir değişken **null atanamaz bir başvurudur**.</span><span class="sxs-lookup"><span data-stu-id="db2b4-205">Any variable of a reference type is a **non-nullable reference**.</span></span>
- <span data-ttu-id="db2b4-206">Null olamayan herhangi bir başvuruya, güvenli bir şekilde başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-206">Any non-nullable reference may be dereferenced safely.</span></span>
- <span data-ttu-id="db2b4-207">Herhangi bir Nullable başvuru türü ( `?` değişken bildiriminde bulunan tür öğesinden sonra belirtilen) null olabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-207">Any nullable reference type (noted by `?` after the type in the variable declaration) may be null.</span></span> <span data-ttu-id="db2b4-208">Statik analiz, başvurunun başvurulduğunu bir değerin null olarak bilinmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="db2b4-208">Static analysis determines if the value is known to be non-null when it's dereferenced.</span></span> <span data-ttu-id="db2b4-209">Aksi takdirde, derleyici sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-209">If not, the compiler warns you.</span></span>
- <span data-ttu-id="db2b4-210">Null yapılabilir bir başvurunun null olmadığını bildirmek için null-forverme işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-210">You can use the null-forgiving operator to declare that a nullable reference isn't null.</span></span>

<span data-ttu-id="db2b4-211">Etkin bir null yapılabilir ek açıklama bağlamında, `?` başvuru türüne eklenen karakter **null yapılabilir bir başvuru türü** bildirir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-211">In an enabled nullable annotation context, the `?` character appended to a reference type declares a **nullable reference type**.</span></span> <span data-ttu-id="db2b4-212">İfadenin null olmadığını bildirmek için **null-forverme işleci** `!` bir ifadeye eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-212">The **null-forgiving operator** `!` may be appended to an expression to declare that the expression isn't null.</span></span>

## <a name="nullable-warning-context"></a><span data-ttu-id="db2b4-213">Null yapılabilir uyarı bağlamı</span><span class="sxs-lookup"><span data-stu-id="db2b4-213">Nullable warning context</span></span>

<span data-ttu-id="db2b4-214">Null yapılabilir uyarı bağlamı null yapılabilir ek açıklama bağlamından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-214">The nullable warning context is distinct from the nullable annotation context.</span></span> <span data-ttu-id="db2b4-215">Yeni ek açıklamalar devre dışı bırakıldığında bile uyarılar etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-215">Warnings can be enabled even when the new annotations are disabled.</span></span> <span data-ttu-id="db2b4-216">Derleyici, herhangi bir başvurunun **null durumunu** belirlemede statik akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-216">The compiler uses static flow analysis to determine the **null state** of any reference.</span></span> <span data-ttu-id="db2b4-217">Null *yapılabilir uyarı bağlamı* **devre dışı bırakılmadıysa** null durumu **null** ya da null **olabilir** .</span><span class="sxs-lookup"><span data-stu-id="db2b4-217">The null state is either **not null** or **maybe null** when the *nullable warning context* isn't **disabled**.</span></span> <span data-ttu-id="db2b4-218">Derleyici **null** olduğunu tespit ettiğinizde bir başvuruya başvuru yaparsanız, derleyici sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-218">If you dereference a reference when the compiler has determined it's **maybe null**, the compiler warns you.</span></span> <span data-ttu-id="db2b4-219">Derleyici iki koşuldan birini belirleyemediği takdirde başvurunun durumu **null olabilir** :</span><span class="sxs-lookup"><span data-stu-id="db2b4-219">The state of a reference is **maybe null** unless the compiler can determine one of two conditions:</span></span>

1. <span data-ttu-id="db2b4-220">Değişkene kesinlikle null olmayan bir değer atandı.</span><span class="sxs-lookup"><span data-stu-id="db2b4-220">The variable has been definitely assigned a non-null value.</span></span>
1. <span data-ttu-id="db2b4-221">Değişken veya ifade, kendisine başvurulmadan önce null değere karşı denetlendi.</span><span class="sxs-lookup"><span data-stu-id="db2b4-221">The variable or expression has been checked against null before de-referencing it.</span></span>

<span data-ttu-id="db2b4-222">Derleyici, null olabilen bir uyarı bağlamında **null** olabilecek bir değişkene veya ifadeye başvuru yaptığınızda uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-222">The compiler generates warnings when you dereference a variable or expression that is **maybe null** in a nullable warning context.</span></span> <span data-ttu-id="db2b4-223">Ayrıca, null olamayan bir başvuru türü değişkenine **null** olabilen bir değişken ya da ifade atandığında, bu da derleyici uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-223">Furthermore, the compiler generates warnings when a nonnullable reference-type variable is assigned a **maybe null** variable or expression in an enabled nullable annotation context.</span></span>

## <a name="attributes-describe-apis"></a><span data-ttu-id="db2b4-224">Öznitelikler API 'Leri tanımlıyor</span><span class="sxs-lookup"><span data-stu-id="db2b4-224">Attributes describe APIs</span></span>

<span data-ttu-id="db2b4-225">API 'lere, bağımsız değişkenlerin veya dönüş değerlerinin null olması veya ne zaman null olamaz hakkında daha fazla bilgi sağlayan öznitelikler eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-225">You add attributes to APIs that provide the compiler more information about when arguments or return values can or can't be null.</span></span> <span data-ttu-id="db2b4-226">Bu öznitelikler hakkında daha fazla bilgiyi [null yapılabilir öznitelikleri](language-reference/attributes/nullable-analysis.md)kapsayan dil başvurusunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-226">You can learn more about these attributes in our article in the language reference covering the [nullable attributes](language-reference/attributes/nullable-analysis.md).</span></span> <span data-ttu-id="db2b4-227">Bu öznitelikler geçerli ve gelecek sürümler üzerinden .NET kitaplıklarına ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="db2b4-227">These attributes are being added to .NET libraries over current and upcoming releases.</span></span> <span data-ttu-id="db2b4-228">En yaygın kullanılan API 'Ler ilk olarak güncelleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="db2b4-228">The most commonly used APIs are being updated first.</span></span>

## <a name="known-pitfalls"></a><span data-ttu-id="db2b4-229">Bilinen Süde</span><span class="sxs-lookup"><span data-stu-id="db2b4-229">Known pitfalls</span></span>

<span data-ttu-id="db2b4-230">Başvuru türleri içeren diziler ve yapılar, null yapılabilir başvuru türleri özelliği olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-230">Arrays and structs that contain reference types are known pitfalls in nullable reference types feature.</span></span>

### <a name="structs"></a><span data-ttu-id="db2b4-231">Yapılar</span><span class="sxs-lookup"><span data-stu-id="db2b4-231">Structs</span></span>

<span data-ttu-id="db2b4-232">Null yapılamayan başvuru türleri içeren bir struct, `default` herhangi bir uyarı olmadan bu için atamaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="db2b4-232">A struct that contains non-nullable reference types allows assigning `default` for it without any warnings.</span></span> <span data-ttu-id="db2b4-233">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="db2b4-233">Consider the following example:</span></span>

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

<span data-ttu-id="db2b4-234">Yukarıdaki örnekte, null `PrintStudent(default)` olamayan başvuru türleri sırasında hiçbir uyarı yoktur `FirstName` ve `LastName` null olur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-234">In the preceding example, there is no warning in `PrintStudent(default)` while the non-nullable reference types `FirstName` and `LastName` are null.</span></span>

<span data-ttu-id="db2b4-235">Diğer bir daha yaygın durum, genel yapılar ile ilgilenirken olur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-235">Another more common case is when you deal with generic structs.</span></span> <span data-ttu-id="db2b4-236">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="db2b4-236">Consider the following example:</span></span>

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

<span data-ttu-id="db2b4-237">Önceki örnekte, özelliği `Bar` `null` çalışma zamanında olacak ve herhangi bir uyarı olmadan null yapılamayan dizeye atanır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-237">In the preceding example, the property `Bar` is going to be `null` at runtime, and it's assigned to non-nullable string without any warnings.</span></span>

### <a name="arrays"></a><span data-ttu-id="db2b4-238">Diziler</span><span class="sxs-lookup"><span data-stu-id="db2b4-238">Arrays</span></span>

<span data-ttu-id="db2b4-239">Diziler aynı zamanda null yapılabilir başvuru türlerinde bilinen bir Süde bulunur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-239">Arrays are also a known pitfall in nullable reference types.</span></span> <span data-ttu-id="db2b4-240">Uyarı üretmeyen aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="db2b4-240">Consider the following example which doesn't produce any warnings:</span></span>

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

<span data-ttu-id="db2b4-241">Önceki örnekte, dizinin bildirimi null yapılamayan dizeler olduğunu gösterirken, öğeleri tamamen null olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="db2b4-241">In the preceding example, the declaration of the array shows it holds non-nullable strings, while its elements are all initialized to null.</span></span> <span data-ttu-id="db2b4-242">Sonra, değişkenine `s` null değer atanır (dizinin ilk öğesi).</span><span class="sxs-lookup"><span data-stu-id="db2b4-242">Then, the variable `s` is assigned a null value (the first element of the array).</span></span> <span data-ttu-id="db2b4-243">Son olarak, değişken başvurusu `s` bir çalışma zamanı özel durumuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="db2b4-243">Finally, the variable `s` is dereferenced causing a runtime exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="db2b4-244">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db2b4-244">See also</span></span>

- [<span data-ttu-id="db2b4-245">Taslak Nullable başvuru türleri belirtimi</span><span class="sxs-lookup"><span data-stu-id="db2b4-245">Draft nullable reference types specification</span></span>](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)
- [<span data-ttu-id="db2b4-246">Null yapılabilir başvurular öğreticisine giriş</span><span class="sxs-lookup"><span data-stu-id="db2b4-246">Intro to nullable references tutorial</span></span>](whats-new/tutorials/nullable-reference-types.md)
- [<span data-ttu-id="db2b4-247">Var olan bir kod temelinin Nullable başvurulara geçirilmesi</span><span class="sxs-lookup"><span data-stu-id="db2b4-247">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="db2b4-248">**Nullable** (C# derleyici seçeneği)</span><span class="sxs-lookup"><span data-stu-id="db2b4-248">**Nullable** (C# Compiler option)</span></span>](language-reference/compiler-options/language.md#nullable)
