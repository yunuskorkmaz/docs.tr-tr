---
title: Yeni değişiklikler ve .NET kitaplıkları
description: .NET kitaplıkları oluştururken bozucu değişiklikler gezinme için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: a5cfd2dfb544b2e47a87bd0939990ae73e5eda9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946997"
---
# <a name="breaking-changes"></a><span data-ttu-id="cd94d-103">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="cd94d-103">Breaking changes</span></span>

<span data-ttu-id="cd94d-104">Mevcut kullanıcılar için kararlılık ve gelecek yeniliğe arasında bir denge bulmak bir .NET kitaplığı için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="cd94d-105">Kitaplık yazarlar, yeniden düzenleme ve kod mükemmel değildir, ancak mevcut kullanıcılarınız yeni özellikle, alt düzey kitaplıkları için olumsuz bir etkiye sahip kadar yeniden değerlendirme Yasla.</span><span class="sxs-lookup"><span data-stu-id="cd94d-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="cd94d-106">Proje türleri ve yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="cd94d-106">Project types and breaking changes</span></span>

<span data-ttu-id="cd94d-107">Bir kitaplık .NET topluluk tarafından nasıl kullanıldığını, son kullanıcı geliştiriciler için bozucu değişiklikler etkisini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

* <span data-ttu-id="cd94d-108">**Düşük ve orta düzeyli kitaplıkları** bir seri hale getirici, HTML ayrıştırıcı, veritabanı nesne ilişkisel eşleyicidir veya web çerçevesi gibi en önemli değişiklikler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="cd94d-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="cd94d-109">Yapı Taşı paketleri, NuGet bağımlılıklarını diğer kitaplıkları ve uygulamaları oluşturmak için son kullanıcı geliştiriciler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd94d-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="cd94d-110">Örneğin, bir uygulama oluştururken ve bir web hizmeti çağırmak amacıyla kullanan bir açık kaynak istemci.</span><span class="sxs-lookup"><span data-stu-id="cd94d-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="cd94d-111">İstemcinin kullandığı bağımlılık en son güncelleştirmeye düzeltebilir miyim bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="cd94d-112">Değiştirilmesi gereken açık kaynaklı istemcisi olan ve hiçbir denetime sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd94d-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="cd94d-113">Kitaplıkları uyumlu sürümlerini bulmak veya istemci kitaplığı için bir düzeltme gönderildikten ve yeni bir sürüm için beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="cd94d-114">Üçüncü bir kitaplık karşılıklı olarak uyumsuz sürümleri üzerinde bağlı iki kitaplıkları kullanmak istiyorsanız iki katına durumdur.</span><span class="sxs-lookup"><span data-stu-id="cd94d-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

* <span data-ttu-id="cd94d-115">**Üst düzey kitaplıkları** UI paketi gibi denetimler için bozucu değişiklikler daha az duyarlı olan.</span><span class="sxs-lookup"><span data-stu-id="cd94d-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="cd94d-116">Üst düzey kitaplıkları, son kullanıcı uygulamayı doğrudan başvurulur.</span><span class="sxs-lookup"><span data-stu-id="cd94d-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="cd94d-117">Bozucu değişiklikleri ortaya çıkarsa, geliştirici en son sürüme güncelleştirmeyi seçebilirsiniz veya bozucu değişiklik ile çalışmak için uygulama değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd94d-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="cd94d-118">**✔️ YAPMAK** kitaplığınıza nasıl kullanılacağını düşünün.</span><span class="sxs-lookup"><span data-stu-id="cd94d-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="cd94d-119">Uygulamaları ve kitaplıkları kullanan etkisini önemli değişiklikler gerekiyor mu?</span><span class="sxs-lookup"><span data-stu-id="cd94d-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="cd94d-120">**✔️ YAPMAK** alt düzey bir .NET kitaplığı geliştirirken bozucu değişiklikleri en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="cd94d-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="cd94d-121">**✔️ DÜŞÜNÜN** ana yayımlama yeniden kitaplığı yeni bir NuGet paketi olarak.</span><span class="sxs-lookup"><span data-stu-id="cd94d-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="cd94d-122">Bozucu değişiklik türleri</span><span class="sxs-lookup"><span data-stu-id="cd94d-122">Types of breaking changes</span></span>

<span data-ttu-id="cd94d-123">Yeni değişiklikler, farklı kategorilere ayrılır ve eşit olarak etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="cd94d-124">Kaynak değişiklik</span><span class="sxs-lookup"><span data-stu-id="cd94d-124">Source breaking change</span></span>

<span data-ttu-id="cd94d-125">Yeni değişiklik bir kaynak, program yürütme etkilemez ancak uygulama yeniden başlatıldığında derleme hatalarına neden.</span><span class="sxs-lookup"><span data-stu-id="cd94d-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="cd94d-126">Örneğin, yeni aşırı bir belirsizlik daha önce belirsiz yöntem çağrılarında oluşturabilirsiniz veya yeniden adlandırılan bir parametresi adlandırılmış parametreleri kullanan çağıranlar çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cd94d-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="cd94d-127">Geliştiriciler uygulamalarını yeniden derleme yaptığınızda değişiklik yeni bir kaynak yalnızca zararlı, az aksatıcı değişiklik olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="cd94d-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="cd94d-128">Geliştiriciler kendi bozuk kaynak kodu kolayca giderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd94d-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="cd94d-129">Davranış değişiklik</span><span class="sxs-lookup"><span data-stu-id="cd94d-129">Behavior breaking change</span></span>

<span data-ttu-id="cd94d-130">Davranış değişiklikleri, en yaygın tür değişiklik: davranışta neredeyse herhangi bir değişiklik birisi uğratabilir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="cd94d-131">Atılan giriş veya çıkış özel durumları değişiklikleri yöntem imzaları gibi kitaplığınıza veri biçimleri, tüm olumsuz etkileyebilir kitaplığı tüketicilerinize.</span><span class="sxs-lookup"><span data-stu-id="cd94d-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="cd94d-132">Kullanıcılar daha önce bozuk çalışma biçimine dayalı değilse bile hata düzeltmesi bir değişiklik kazanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="cd94d-133">Özellikleri ekleyerek ve hatalı davranışları geliştirme iyidir ancak bakım, bu yükseltme mevcut kullanıcılar için çok zor zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="cd94d-134">Bozucu değişiklikler davranışı ile baş geliştiriciler yardımcı olmak için bir yaklaşım, bunları ayarları Gizle sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cd94d-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="cd94d-135">Ayarları kitaplığınızın kabul et veya bozucu değişiklikler kabul etmeniz aynı anda sırada en son sürüme güncelleştirme geliştiricilerin olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd94d-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="cd94d-136">Bu strateji, geliştiricilerin zamanla uyum kendi kullanan kodu izin verirken güncel kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd94d-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="cd94d-137">Örneğin, ASP.NET Core MVC kavramını sahip bir [uyumluluk sürümü](/aspnet/core/mvc/compatibility-version) etkin ve devre dışı özelliklerini değiştiren `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="cd94d-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="cd94d-138">**✔️ DÜŞÜNÜN** mevcut kullanıcıları etkileyen ve geliştiriciler özelliği olan bir ayarı kabul etmek istiyorum yeni özellikler varsayılan olarak, bırakarak.</span><span class="sxs-lookup"><span data-stu-id="cd94d-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="cd94d-139">İkili değişiklik</span><span class="sxs-lookup"><span data-stu-id="cd94d-139">Binary breaking change</span></span>

<span data-ttu-id="cd94d-140">Genel API kitaplığınızın değiştirdiğinizde bir ikili değişiklik olur, derlenmiş derlemelerde karşı şekilde kitaplığınızın eski sürümleri artık API arayabilmesi için.</span><span class="sxs-lookup"><span data-stu-id="cd94d-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="cd94d-141">Örneğin, yeni bir parametre ekleyerek bir yöntemin imzası değiştirme Kitaplığı'nın eski sürümünü karşı derlenen derlemelere throw neden olacak bir <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="cd94d-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="cd94d-142">Yeni değişiklik bir ikili da bölünebilir bir **tüm derleme**.</span><span class="sxs-lookup"><span data-stu-id="cd94d-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="cd94d-143">Bir derlemeye yeniden adlandırma `AssemblyName` derlemenin kimliğini, ekleme, kaldırma veya derlemenin tanımlayıcı adlandırma anahtarının değiştirilmesi olacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="cd94d-144">Bir derlemenin kimliğinin bir değişiklik, bunu kullanan tüm derlenmiş kod çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cd94d-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="cd94d-145">**❌ SAĞLAMADIĞI** bir derleme adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd94d-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="cd94d-146">**❌ SAĞLAMADIĞI** eklemek, kaldırmak veya tanımlayıcı adlandırma anahtarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd94d-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="cd94d-147">**✔️ DÜŞÜNÜN** soyut taban sınıfları yerine arabirimleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="cd94d-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="cd94d-148">Her şey için arabirim ekleme başarısız uygulayan varolan türleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="cd94d-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="cd94d-149">Soyut bir temel sınıf varsayılan bir sanal uygulama eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd94d-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="cd94d-150">**✔️ DÜŞÜNÜN** yerleştirme <xref:System.ObsoleteAttribute> türleri ve üyeleri kaldırmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="cd94d-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="cd94d-151">Öznitelik, artık eski API'yi kullanmak için kodu güncelleştirmek için yönergeler sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd94d-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="cd94d-152">Türler ve yöntemlerin çağıran kod <xref:System.ObsoleteAttribute> özniteliği için sağlanan iletiyi içeren bir derleme uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd94d-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="cd94d-153">Uyarıları verin kullananlar en eski API kaldırıldığında, artık, böylece geçirmek için eski API yüzey zaman bunu kullanma.</span><span class="sxs-lookup"><span data-stu-id="cd94d-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="cd94d-154">**✔️ DÜŞÜNÜN** türler ve yöntemlerin tutma <xref:System.ObsoleteAttribute> süresiz olarak kitaplıklarındaki düşük ve orta düzey.</span><span class="sxs-lookup"><span data-stu-id="cd94d-154">**✔️ CONSIDER** keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="cd94d-155">API'leri kaldırılması, bozucu değişiklik bir ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="cd94d-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="cd94d-156">Artık kullanılmayan türler ve yöntemlerin bunların bakımı, tutma dikkate düşük maliyet ve çok teknik borcu kitaplığınıza eklemez.</span><span class="sxs-lookup"><span data-stu-id="cd94d-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="cd94d-157">Türleri ve yöntemleri kaldırılmıyor, yukarıda belirtilen iki katına senaryoları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd94d-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd94d-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd94d-158">See also</span></span>

- [<span data-ttu-id="cd94d-159">C# geliştiricileri için sürüm ve güncelleştirme konuları</span><span class="sxs-lookup"><span data-stu-id="cd94d-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="cd94d-160">Eksiksiz bir kılavuz. NET'te API bozucu değişiklikler</span><span class="sxs-lookup"><span data-stu-id="cd94d-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="cd94d-161">Corefx'te bozucu değişiklik kuralları</span><span class="sxs-lookup"><span data-stu-id="cd94d-161">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="cd94d-162">Önceki</span><span class="sxs-lookup"><span data-stu-id="cd94d-162">Previous</span></span>](versioning.md)
