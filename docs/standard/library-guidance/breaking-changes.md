---
title: Son değişiklikler ve .NET kitaplıkları
description: .NET kitaplıkları oluştururken önemli değişikliklere gidilme için en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731471"
---
# <a name="breaking-changes"></a><span data-ttu-id="e1e89-103">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e1e89-103">Breaking changes</span></span>

<span data-ttu-id="e1e89-104">Bir .NET kitaplığı, gelecekte mevcut kullanıcılar ve yeniliklere yönelik kararlılık arasında bir denge bulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="e1e89-105">Kitaplık yazarları, kusursuz olana kadar yeniden düzenleme ve yeniden düşünme kodu içerir, ancak özellikle alt düzey kitaplıklar için mevcut kullanıcılarınızın olumsuz bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="e1e89-106">Proje türleri ve son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="e1e89-106">Project types and breaking changes</span></span>

<span data-ttu-id="e1e89-107">Bir kitaplığın .NET topluluğu tarafından nasıl kullanıldığı, Son Kullanıcı geliştiricileri üzerindeki değişikliklerin etkilerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="e1e89-108">Seri hale getirici, HTML ayrıştırıcısı, veritabanı nesnesi-ilişkisel Eşleyici veya Web çerçevesi gibi **düşük ve orta düzey kitaplıklar** , en son değişikliklerden etkilenir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="e1e89-109">Yapı blok paketleri, Son Kullanıcı geliştiricileri tarafından uygulamaları ve diğer kitaplıkları NuGet bağımlılıkları olarak oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="e1e89-110">Örneğin, bir uygulama oluşturuyor ve bir Web hizmetini çağırmak için açık kaynaklı istemci kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e1e89-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="e1e89-111">İstemcinin kullandığı bir bağımlılığı ortadan kaldırma, çözebilmeniz için bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="e1e89-112">Değiştirilmesi gereken ve üzerinde denetiminiz olmadığı açık kaynaklı istemcdir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="e1e89-113">Kitaplıkların uyumlu sürümlerini bulmanız veya istemci kitaplığına bir çözüm göndermeniz ve yeni bir sürüm beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="e1e89-114">En kötü durum durumu, üçüncü bir kitaplığın karşılıklı uyumsuz sürümlerine bağlı iki kitaplık kullanmak istemeniz durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="e1e89-115">UI denetimleri paketi gibi **üst düzey kitaplıklar** , değişikliklere karşı daha az hassastır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="e1e89-116">Üst düzey kitaplıklara doğrudan bir son kullanıcı uygulamasında başvurulur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="e1e89-117">Önemli değişiklikler gerçekleşirse, geliştirici en son sürüme güncelleştirmeyi seçebilir veya uygulamasını, son değişiklikle çalışacak şekilde değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="e1e89-118">✔️, kitaplığınızın nasıl kullanılacağını düşünün.</span><span class="sxs-lookup"><span data-stu-id="e1e89-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="e1e89-119">Hangi etkilerden oluşan uygulamalar ve kitaplıklarda yapılan değişiklikler ne etkiler?</span><span class="sxs-lookup"><span data-stu-id="e1e89-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="e1e89-120">düşük düzey bir .NET kitaplığı geliştirilirken, önemli değişiklikleri en aza indirir ✔️.</span><span class="sxs-lookup"><span data-stu-id="e1e89-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="e1e89-121">✔️ Yeni bir NuGet paketi olarak bir kitaplığın büyük bir yeniden yazmayı yayımlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e1e89-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="e1e89-122">Son değişiklik türleri</span><span class="sxs-lookup"><span data-stu-id="e1e89-122">Types of breaking changes</span></span>

<span data-ttu-id="e1e89-123">Son değişiklikler farklı kategorilere ayrılır ve eşit ölçüde etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="e1e89-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="e1e89-124">Kaynak bölünmesi değişikliği</span><span class="sxs-lookup"><span data-stu-id="e1e89-124">Source breaking change</span></span>

<span data-ttu-id="e1e89-125">Kaynak bölünmesi değişikliği program yürütmeyi etkilemez, ancak uygulamanın bir sonraki yeniden derlenmesi sırasında derleme hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="e1e89-126">Örneğin, yeni bir aşırı yükleme daha önce kesin olmayan yöntem çağrılarında belirsizlik oluşturabilir ya da yeniden adlandırılmış bir parametre adlandırılmış parametreleri kullanan çağıranları keser.</span><span class="sxs-lookup"><span data-stu-id="e1e89-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="e1e89-127">Kaynak bölünmesi değişikliği yalnızca geliştiriciler uygulamalarını yeniden derleyeceğinden zararlı olduğundan, en az kesintiye uğratan değişiklik olur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="e1e89-128">Geliştiriciler kendi bozuk kaynak kodlarını kolayca çözebilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="e1e89-129">Davranış bölünmesi değişikliği</span><span class="sxs-lookup"><span data-stu-id="e1e89-129">Behavior breaking change</span></span>

<span data-ttu-id="e1e89-130">Davranış değişiklikleri en yaygın Son değişiklik türüdür: neredeyse her türlü davranış değişikliği birini bozabilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="e1e89-131">Kitaplığınızda yöntem imzaları, özel durumlar veya giriş ya da çıkış veri biçimleri gibi değişiklikler, kitaplık tüketicilerinizi olumsuz yönde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="e1e89-132">Bir hata düzeltilme bile, kullanıcılar daha önce kopuk davranışa güvendiğinde, bir son değişiklik olarak nitelendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="e1e89-133">Özellikleri eklemek ve hatalı davranışları iyileştirmek iyi bir şeydir, ancak bunu yapmadan, mevcut kullanıcıların yükseltilmesi çok zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="e1e89-134">Geliştiricilerin davranış önemli değişiklikleri ile uğraşmasına yardımcı olmak için bir yaklaşım, ayarların arkasındaki ayarları gizleyeyöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="e1e89-135">Ayarlar, geliştiricilerin kitaplığın en son sürümüne güncelleştirilmesini sağlar, ancak aynı zamanda değişiklikleri ortadan kaldırma veya devre dışı bırakmak üzere tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="e1e89-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="e1e89-136">Bu strateji, geliştiricilerin zaman içinde kendi kod uyarlanmasına izin verirken güncel kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1e89-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="e1e89-137">Örneğin, ASP.NET Core MVC, `MvcOptions`etkinleştirilmiş ve devre dışı bırakılan özellikleri değiştiren bir [Uyumluluk sürümü](/aspnet/core/mvc/compatibility-version) kavramıdır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="e1e89-138">✔️, mevcut kullanıcıları etkiliyorsa ve geliştiricilerin özelliği bir ayarla birlikte kabul etmelerine izin vermek için yeni özellikleri varsayılan olarak devre dışı bırakmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e1e89-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="e1e89-139">İkili Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="e1e89-139">Binary breaking change</span></span>

<span data-ttu-id="e1e89-140">Kitaplığınızın genel API 'sini değiştirdiğiniz zaman ikili bir değişiklik gerçekleşir, bu nedenle kitaplığınızın eski sürümlerine göre derlenen derlemeler artık API 'yi çağıramayacak.</span><span class="sxs-lookup"><span data-stu-id="e1e89-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="e1e89-141">Örneğin, yeni bir parametre ekleyerek bir yöntemin imzasını değiştirmek, kitaplığın daha eski sürümüne karşı derlenen derlemelerin bir <xref:System.MissingMethodException>oluşturması için neden olur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="e1e89-142">İkili bir son değişiklik, **tüm bir derlemeyi**de kesebilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="e1e89-143">Bir derlemeyi `AssemblyName` olarak yeniden adlandırmak derlemenin kimliğini değiştirecek, bu da derlemenin tanımlayıcı adlandırma anahtarını ekler, kaldırır veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="e1e89-144">Bir derlemenin kimliğinin değişikliği, kendisini kullanan tüm derlenmiş kodları keser.</span><span class="sxs-lookup"><span data-stu-id="e1e89-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="e1e89-145">❌ bir derleme adını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="e1e89-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="e1e89-146">❌ tanımlayıcı adlandırma anahtarını ekleme, kaldırma veya değiştirme.</span><span class="sxs-lookup"><span data-stu-id="e1e89-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="e1e89-147">✔️, arabirimler yerine soyut temel sınıflar kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e1e89-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="e1e89-148">Bir arabirime herhangi bir şey eklemek, onu uygulayan varolan türlerin başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="e1e89-149">Soyut temel sınıf, varsayılan bir sanal uygulama eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="e1e89-150">✔️ kaldırmak istediğiniz türlere ve üyelere <xref:System.ObsoleteAttribute> yerleştirmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e1e89-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="e1e89-151">Öznitelik, artık kullanılmayan API 'yi kullanmayacak şekilde kodu güncelleştirme yönergelerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1e89-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="e1e89-152"><xref:System.ObsoleteAttribute> türleri ve yöntemleri çağıran kod, özniteliğe sağlanan iletiyle birlikte bir yapı uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="e1e89-153">Uyarılar, kullanımdan kalkmış API 'nin kaldırılması için eski API yüzey süresini kullanan kişilere, çoğu zaman artık bunu kullanmayabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1e89-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

<span data-ttu-id="e1e89-154">✔️, düşük ve orta düzeyde kitaplıklarda, <xref:System.ObsoleteAttribute> ile türleri ve yöntemleri süresiz olarak tutmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e1e89-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="e1e89-155">API 'Lerin kaldırılması ikili bir son değişiklik olur.</span><span class="sxs-lookup"><span data-stu-id="e1e89-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="e1e89-156">Eski türlerin ve yöntemlerin saklanması düşük maliyetlidir ve kitaplığınıza çok sayıda teknik borç eklemez.</span><span class="sxs-lookup"><span data-stu-id="e1e89-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="e1e89-157">Türlerin ve yöntemlerin kaldırılmaması, yukarıda belirtilen en kötü durum senaryolarından kaçınmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1e89-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1e89-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1e89-158">See also</span></span>

- [<span data-ttu-id="e1e89-159">Geliştiriciler için C# sürüm ve güncelleştirme değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="e1e89-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="e1e89-160">.NET 'teki API-kırılmaya yönelik kesin bir kılavuz</span><span class="sxs-lookup"><span data-stu-id="e1e89-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="e1e89-161">.NET Son değişiklik kuralları</span><span class="sxs-lookup"><span data-stu-id="e1e89-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="e1e89-162">Öncekini</span><span class="sxs-lookup"><span data-stu-id="e1e89-162">Previous</span></span>](versioning.md)
