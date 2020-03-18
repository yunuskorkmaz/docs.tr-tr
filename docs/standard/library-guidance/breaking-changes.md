---
title: Son dakika değişiklikleri ve .NET kitaplıkları
description: .NET kitaplıklarını oluştururken sonlandırma değişikliklerinde gezinmek için en iyi uygulama önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400423"
---
# <a name="breaking-changes"></a><span data-ttu-id="cecbd-103">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="cecbd-103">Breaking changes</span></span>

<span data-ttu-id="cecbd-104">Bir .NET kitaplığının mevcut kullanıcılar için kararlılık ve gelecek için yenilik arasında bir denge bulması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="cecbd-105">Kitaplık yazarları mükemmel olana kadar kodu yeniden düzenleme ve yeniden düşünmeye yönelir, ancak mevcut kullanıcılarınızı kırmanın özellikle düşük seviyeli kitaplıklar için olumsuz bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="cecbd-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="cecbd-106">Proje türleri ve kesme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="cecbd-106">Project types and breaking changes</span></span>

<span data-ttu-id="cecbd-107">Bir kitaplığın .NET topluluğu tarafından nasıl kullanıldığı, değişiklikleri son kullanıcı geliştiricileri üzerindeki kesme etkisini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="cecbd-108">Bir serializer, HTML ayrıştırıcı, veritabanı nesne-ilişkisel mapper veya web çerçevesi gibi **düşük ve orta düzey kitaplıklar** değişiklikleri kırma en etkilenir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="cecbd-109">Yapı bloğu paketleri, uygulamaları oluşturmak için son kullanıcı geliştiricileri ve NuGet bağımlılıkları olarak diğer kitaplıklar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cecbd-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="cecbd-110">Örneğin, bir uygulama oluşturuyorsunuz ve bir web hizmetini aramak için açık kaynak kodlu bir istemci kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="cecbd-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="cecbd-111">İstemcinin kullandığı bir bağımlılık için son dakika güncelleştirmesi düzeltebileceğiniz bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="cecbd-112">Değiştirilmesi gereken açık kaynak istemcisi ve üzerinde hiçbir kontrole sahip.</span><span class="sxs-lookup"><span data-stu-id="cecbd-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="cecbd-113">Kitaplıkların uyumlu sürümlerini bulmanız veya istemci kitaplığına bir düzeltme göndermeniz ve yeni bir sürüm beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="cecbd-114">En kötü durum, üçüncü bir kitaplığın karşılıklı uyumsuz sürümlerine bağlı iki kitaplık kullanmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="cecbd-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="cecbd-115">Bir tür ui denetimi gibi **üst düzey kitaplıklar,** değişiklikleri kırmaya karşı daha az duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="cecbd-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="cecbd-116">Üst düzey kitaplıklar doğrudan bir son kullanıcı uygulamasında başvurulur.</span><span class="sxs-lookup"><span data-stu-id="cecbd-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="cecbd-117">Son kesme değişiklikleri oluşursa, geliştirici en son sürüme güncelleştirmeyi seçebilir veya uygulamalarını kesme değişikliğiyle çalışacak şekilde değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="cecbd-118">✔️ KITAPlığınızın nasıl kullanılacağını düşünün.</span><span class="sxs-lookup"><span data-stu-id="cecbd-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="cecbd-119">Çığır açan değişikliklerin onu kullanan uygulamalar ve kitaplıklar üzerinde ne gibi bir etkisi olacak?</span><span class="sxs-lookup"><span data-stu-id="cecbd-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="cecbd-120">✔️ düşük düzeyli bir .NET kitaplığı geliştirirken çığır açan değişiklikleri en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="cecbd-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="cecbd-121">✔️ yeni bir NuGet paketi olarak bir kitaplığın büyük bir yeniden yazmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="cecbd-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="cecbd-122">Kesme değişiklik türleri</span><span class="sxs-lookup"><span data-stu-id="cecbd-122">Types of breaking changes</span></span>

<span data-ttu-id="cecbd-123">Kesme değişiklikleri farklı kategorilere ayrılır ve eşit derecede etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="cecbd-124">Kaynak kırma değişikliği</span><span class="sxs-lookup"><span data-stu-id="cecbd-124">Source breaking change</span></span>

<span data-ttu-id="cecbd-125">Kaynak kesme değişikliği program yürütülmesini etkilemez, ancak uygulama bir sonraki kez yeniden derleninde derleme hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cecbd-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="cecbd-126">Örneğin, yeni bir aşırı yükleme yöntem çağrılarında daha önce kesin olmayan bir belirsizlik oluşturabilir veya yeniden adlandırılmış parametre adlandırılmış parametreleri kullanan arayanlara son verecektir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="cecbd-127">Kaynak kırma değişikliği yalnızca geliştiriciler uygulamalarını yeniden derlediğinde zararlı olduğundan, en az kesintiye uğrayan değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="cecbd-128">Geliştiriciler kendi bozuk kaynak kodlarını kolayca düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="cecbd-129">Davranış kesme değişikliği</span><span class="sxs-lookup"><span data-stu-id="cecbd-129">Behavior breaking change</span></span>

<span data-ttu-id="cecbd-130">Davranış değişiklikleri en yaygın kesme türüdür: davranıştaki hemen hemen her değişiklik birini kırabilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="cecbd-131">Kitaplığınızda yöntem imzaları, atılan özel durumlar veya giriş veya çıktı veri biçimleri gibi değişiklikler, tüm bunlar kitaplık tüketicilerinizi olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="cecbd-132">Kullanıcılar daha önce kırılan davranışa güveniyorsa, hata düzeltmesi bile bir kesme değişikliği olarak nitelendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="cecbd-133">Özellikler ekleme ve kötü davranışları geliştirmek iyi bir şeydir, ancak bakım olmadan mevcut kullanıcıların yükseltmesini çok zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="cecbd-134">Geliştiricilerin davranış kırma değişiklikleriyle başa çıkmasına yardımcı olmak için bir yaklaşım, bunları ayarların arkasına gizlemektir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="cecbd-135">Ayarlar, geliştiricilerin kitaplığınızın en son sürümüne güncellenerken aynı zamanda değişiklikleri bölmeyi seçmeyi veya devre dışı bırakmayı seçmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cecbd-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="cecbd-136">Bu strateji, geliştiricilerin tüketen kodlarının zaman içinde uyum sağlamasına izin verirken güncel kalmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cecbd-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="cecbd-137">Örneğin, ASP.NET Core MVC, 'de etkinleştirilen ve devre dışı bırakılan `MvcOptions`özellikleri değiştiren bir uyumluluk [sürümü](/aspnet/core/mvc/compatibility-version) kavramına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="cecbd-138">✔️, varolan kullanıcıları etkiliyorsa, yeni özellikleri varsayılan olarak kapalı bırakmayı düşünün ve geliştiricilerin bir ayarı olan özelliği seçmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="cecbd-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="cecbd-139">İkili kırılma değişimi</span><span class="sxs-lookup"><span data-stu-id="cecbd-139">Binary breaking change</span></span>

<span data-ttu-id="cecbd-140">Kitaplığınızın genel API'sini değiştirdiğinizde ikili bir kesme değişikliği gerçekleşir, bu nedenle kitaplığınızın eski sürümlerine karşı derlenen derlemeler artık API'yi arayamaz.</span><span class="sxs-lookup"><span data-stu-id="cecbd-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="cecbd-141">Örneğin, yeni bir parametre ekleyerek bir yöntemin imzasını değiştirmek, kitaplığın eski sürümüne <xref:System.MissingMethodException>karşı derlenen derlemelerin bir .</span><span class="sxs-lookup"><span data-stu-id="cecbd-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="cecbd-142">İkili kesme değişikliği de **tüm derlemeyi**bozabilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="cecbd-143">Bir derlemeyi `AssemblyName` yeniden adlandırma, derlemenin güçlü adlandırma anahtarını ekleme, kaldırma veya değiştirme gibi derlemenin kimliğini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="cecbd-144">Bir derlemenin kimliğinde yapılan değişiklik, onu kullanan derlenmiş tüm kodları bozar.</span><span class="sxs-lookup"><span data-stu-id="cecbd-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="cecbd-145">❌Montaj adını DEĞIŞTIRMEYİn.</span><span class="sxs-lookup"><span data-stu-id="cecbd-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="cecbd-146">❌Güçlü adlandırma anahtarını eklemeYIN, kaldırmayın veya değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="cecbd-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="cecbd-147">✔️ arabirimler yerine soyut temel sınıfları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="cecbd-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="cecbd-148">Arabirara bir şey eklemek, onu uygulayan varolan türlerin başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cecbd-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="cecbd-149">Soyut bir taban sınıf varsayılan sanal uygulama eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cecbd-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="cecbd-150">✔️ kaldırmayı <xref:System.ObsoleteAttribute> düşündüğünüz türleri ve üyeleri yerleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="cecbd-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="cecbd-151">Öznitelik artık eski API kullanmak için kodu güncelleştirmek için yönergeler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cecbd-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="cecbd-152">Türleri ve yöntemleri <xref:System.ObsoleteAttribute> çağıran kod, özniteliğe verilen iletiyle birlikte bir yapı uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cecbd-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="cecbd-153">Uyarılar, eski API yüzey süresini kullanan kişilere, eski API kaldırıldığında çoğu kişinin artık bu alanı kullanmaması için geçiş yapmak için verir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="cecbd-154">✔️ düşük ve orta <xref:System.ObsoleteAttribute> düzey kütüphanelerde süresiz olarak türleri ve yöntemleri tutmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="cecbd-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="cecbd-155">API'leri kaldırmak ikili bir kırılma değişikliğidir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="cecbd-156">Eski türleri ve yöntemleri korumak düşük maliyetli ve kitaplığınıza çok fazla teknik borç eklemez göz önünde bulundurularak.</span><span class="sxs-lookup"><span data-stu-id="cecbd-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="cecbd-157">Türleri ve yöntemleri kaldırmamak, yukarıda belirtilen en kötü durum senaryolarını önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="cecbd-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cecbd-158">See also</span></span>

- [<span data-ttu-id="cecbd-159">C# geliştiricileri için sürüm ve güncelleştirme konuları</span><span class="sxs-lookup"><span data-stu-id="cecbd-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="cecbd-160">.NET'teki API bozan değişiklikler için kesin bir kılavuz</span><span class="sxs-lookup"><span data-stu-id="cecbd-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="cecbd-161">.NET kırma değişiklik kuralları</span><span class="sxs-lookup"><span data-stu-id="cecbd-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="cecbd-162">Önceki</span><span class="sxs-lookup"><span data-stu-id="cecbd-162">Previous</span></span>](versioning.md)
