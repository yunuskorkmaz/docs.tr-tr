---
title: Blazor ile yeniden kullanılabilir UI bileşenleri oluşturun
description: Blazor ile yeniden kullanılabilir UI bileşenlerini nasıl oluşturup ASP.NET Web Formları denetimleriyle nasıl karşılaştıracaklarını öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228619"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="007f8-103">Blazor ile yeniden kullanılabilir UI bileşenleri oluşturun</span><span class="sxs-lookup"><span data-stu-id="007f8-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="007f8-104">ASP.NET Web Formları hakkında güzel şeylerden biri, yeniden kullanılabilir kullanıcı arabirimi (UI) kodu parçalarının yeniden kullanılabilir kullanıcı arabirimi denetimlerine kapsüllemesini nasıl sağladığıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="007f8-105">Özel kullanıcı denetimleri *.ascx* dosyaları kullanılarak biçimlendirme de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="007f8-106">Ayrıca, tam tasarımcı desteği yle ayrıntılı sunucu denetimlerini kod halinde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="007f8-107">Blazor ayrıca *bileşenler*aracılığıyla UI kapsüllemasını destekler.</span><span class="sxs-lookup"><span data-stu-id="007f8-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="007f8-108">Bir bileşen:</span><span class="sxs-lookup"><span data-stu-id="007f8-108">A component:</span></span>

- <span data-ttu-id="007f8-109">UI'nin kendi kendine yeten bir parçası.</span><span class="sxs-lookup"><span data-stu-id="007f8-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="007f8-110">Kendi durumunu ve işleme mantığını korur.</span><span class="sxs-lookup"><span data-stu-id="007f8-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="007f8-111">UI olay işleyicileri tanımlayabilir, giriş verilerine bağlanabilir ve kendi yaşam döngüsünü yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="007f8-112">Genellikle Jilet sözdizimi kullanılarak *bir .razor* dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="007f8-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="007f8-113">Razor için bir giriş</span><span class="sxs-lookup"><span data-stu-id="007f8-113">An introduction to Razor</span></span>

<span data-ttu-id="007f8-114">Razor, HTML ve C#'a dayalı hafif bir biçimlendirme dilidir.</span><span class="sxs-lookup"><span data-stu-id="007f8-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="007f8-115">Razor ile, bileşen oluşturma mantığınızı tanımlamak için biçimlendirme ve C# kodu arasında sorunsuz bir geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="007f8-116">*.razor* dosyası derlendiğinde, işleme mantığı .NET sınıfında yapılandırılmış bir şekilde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="007f8-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="007f8-117">Derlenen sınıfın adı *.razor* dosya adından alınır.</span><span class="sxs-lookup"><span data-stu-id="007f8-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="007f8-118">Ad alanı proje ve klasör yolu için varsayılan ad alanından alınır veya `@namespace` yönergeyi kullanarak ad alanını açıkça belirtebilirsiniz (aşağıdaki Razor yönergeleri hakkında daha fazla bilgi).</span><span class="sxs-lookup"><span data-stu-id="007f8-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="007f8-119">Bir bileşenin oluşturma mantığı, C# kullanılarak eklenen dinamik mantıkla normal HTML biçimlendirmesi kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="007f8-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="007f8-120">`@` Karakter C#'a geçiş için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007f8-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="007f8-121">Razor, HTML'ye ne zaman geçtiğinizi anlama konusunda genellikle akıllıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="007f8-122">Örneğin, aşağıdaki bileşen geçerli `<p>` saatle birlikte bir etiket işler:</span><span class="sxs-lookup"><span data-stu-id="007f8-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="007f8-123">C# ifadesinin başlangıcını ve sonunu açıkça belirtmek için parantez leri kullanın:</span><span class="sxs-lookup"><span data-stu-id="007f8-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="007f8-124">Razor ayrıca render mantığınızda C# kontrol akışını kullanmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="007f8-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="007f8-125">Örneğin, bazı HTML'leri koşullu olarak şu şekilde işleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="007f8-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="007f8-126">Veya bunun gibi normal bir C# `foreach` döngüsü kullanarak öğelerin bir listesini oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="007f8-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="007f8-127">ASP.NET Web Formlar'daki direktifler gibi jilet yönergeleri, Bir Razor bileşeninin nasıl derlendirilebildiğini birçok yönü denetler.</span><span class="sxs-lookup"><span data-stu-id="007f8-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="007f8-128">Örnekler bileşenin şunlardır:</span><span class="sxs-lookup"><span data-stu-id="007f8-128">Examples include the component's:</span></span>

- <span data-ttu-id="007f8-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="007f8-129">Namespace</span></span>
- <span data-ttu-id="007f8-130">Taban sınıf</span><span class="sxs-lookup"><span data-stu-id="007f8-130">Base class</span></span>
- <span data-ttu-id="007f8-131">Uygulanan arabirimler</span><span class="sxs-lookup"><span data-stu-id="007f8-131">Implemented interfaces</span></span>
- <span data-ttu-id="007f8-132">Genel parametreler</span><span class="sxs-lookup"><span data-stu-id="007f8-132">Generic parameters</span></span>
- <span data-ttu-id="007f8-133">Alınan ad alanları</span><span class="sxs-lookup"><span data-stu-id="007f8-133">Imported namespaces</span></span>
- <span data-ttu-id="007f8-134">Yollar</span><span class="sxs-lookup"><span data-stu-id="007f8-134">Routes</span></span>

<span data-ttu-id="007f8-135">Jilet yönergeleri `@` karakterle başlar ve genellikle dosyanın başında yeni bir satırın başında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007f8-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="007f8-136">Örneğin, `@namespace` yönerge bileşenin ad alanını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="007f8-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="007f8-137">Aşağıdaki tablo, Blazor'da kullanılan çeşitli Razor yönergelerini ve varsa ASP.NET Web Formları eşdeğerlerini özetleyilmiştir.</span><span class="sxs-lookup"><span data-stu-id="007f8-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="007f8-138">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="007f8-138">Directive</span></span>    |<span data-ttu-id="007f8-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="007f8-139">Description</span></span>|<span data-ttu-id="007f8-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="007f8-140">Example</span></span>|<span data-ttu-id="007f8-141">Web Formlar eşdeğeri</span><span class="sxs-lookup"><span data-stu-id="007f8-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="007f8-142">Bileşene sınıf düzeyinde bir öznitelik ekler</span><span class="sxs-lookup"><span data-stu-id="007f8-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="007f8-143">None</span><span class="sxs-lookup"><span data-stu-id="007f8-143">None</span></span>|
|`@code`      |<span data-ttu-id="007f8-144">Bileşene sınıf üyeleri ekler</span><span class="sxs-lookup"><span data-stu-id="007f8-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="007f8-145">Belirtilen arabirimi uygular</span><span class="sxs-lookup"><span data-stu-id="007f8-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="007f8-146">Kod arkası kullanma</span><span class="sxs-lookup"><span data-stu-id="007f8-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="007f8-147">Belirtilen taban sınıftan devralmalar</span><span class="sxs-lookup"><span data-stu-id="007f8-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="007f8-148">Bileşene bir hizmet enjekte eder</span><span class="sxs-lookup"><span data-stu-id="007f8-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="007f8-149">None</span><span class="sxs-lookup"><span data-stu-id="007f8-149">None</span></span>|
|`@layout`    |<span data-ttu-id="007f8-150">Bileşen için bir düzen bileşeni belirtir</span><span class="sxs-lookup"><span data-stu-id="007f8-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="007f8-151">Bileşen için ad alanını ayarlar</span><span class="sxs-lookup"><span data-stu-id="007f8-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="007f8-152">None</span><span class="sxs-lookup"><span data-stu-id="007f8-152">None</span></span>|
|`@page`      |<span data-ttu-id="007f8-153">Bileşenin rotasını belirtir</span><span class="sxs-lookup"><span data-stu-id="007f8-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="007f8-154">Bileşen için genel bir tür parametrebelirtir</span><span class="sxs-lookup"><span data-stu-id="007f8-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="007f8-155">Kod arkası kullanma</span><span class="sxs-lookup"><span data-stu-id="007f8-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="007f8-156">Kapsamına getirmek için bir ad alanı belirtir</span><span class="sxs-lookup"><span data-stu-id="007f8-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="007f8-157">*web.config'de* ad alanı ekleme</span><span class="sxs-lookup"><span data-stu-id="007f8-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="007f8-158">Jilet bileşenleri ayrıca, bileşenlerin nasıl derlendirilebildiğini (olay işleme, veri bağlama, bileşen & eleman başvuruları vb.) çeşitli yönlerini denetlemek için öğeler üzerindeki *yönerge özniteliklerini* de kapsamlı bir şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="007f8-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="007f8-159">Yönerge öznitelikleritüm parantez değerleri isteğe bağlı olduğu ortak bir genel sözdizimi izleyin:</span><span class="sxs-lookup"><span data-stu-id="007f8-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="007f8-160">Aşağıdaki tablo, Blazor'da kullanılan Razor yönergelerinin çeşitli özelliklerini özetleyilmiştir.</span><span class="sxs-lookup"><span data-stu-id="007f8-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="007f8-161">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="007f8-161">Attribute</span></span>    |<span data-ttu-id="007f8-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="007f8-162">Description</span></span>|<span data-ttu-id="007f8-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="007f8-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="007f8-164">Öznitelikler sözlüğü işler</span><span class="sxs-lookup"><span data-stu-id="007f8-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="007f8-165">İki yönlü veri bağlama oluşturur</span><span class="sxs-lookup"><span data-stu-id="007f8-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="007f8-166">Belirtilen olay için bir olay işleyicisi ekler</span><span class="sxs-lookup"><span data-stu-id="007f8-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="007f8-167">Bir koleksiyondaki öğeleri korumak için difüzör algoritması tarafından kullanılacak bir anahtar belirtir</span><span class="sxs-lookup"><span data-stu-id="007f8-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="007f8-168">Bileşene veya HTML öğesine yapılan bir başvuruyu yakalar</span><span class="sxs-lookup"><span data-stu-id="007f8-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="007f8-169">Blazor tarafından kullanılan çeşitli`@onclick`direktif `@bind` `@ref`öznitelikleri ( , , , vb) aşağıdaki bölümlerde ve daha sonraki bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="007f8-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="007f8-170">*.aspx* ve *.ascx* dosyalarında kullanılan sözdizimilerin çoğunda Razor'da paralel sözdizimi bulunur.</span><span class="sxs-lookup"><span data-stu-id="007f8-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="007f8-171">Aşağıda web formları ve jilet ASP.NET için sözdizimleri basit bir karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="007f8-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="007f8-172">Özellik</span><span class="sxs-lookup"><span data-stu-id="007f8-172">Feature</span></span>                      |<span data-ttu-id="007f8-173">Web Forms</span><span class="sxs-lookup"><span data-stu-id="007f8-173">Web Forms</span></span>           |<span data-ttu-id="007f8-174">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="007f8-174">Syntax</span></span>               |<span data-ttu-id="007f8-175">Razor</span><span class="sxs-lookup"><span data-stu-id="007f8-175">Razor</span></span>         |<span data-ttu-id="007f8-176">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="007f8-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="007f8-177">Yönergeler</span><span class="sxs-lookup"><span data-stu-id="007f8-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="007f8-178">Kod blokları</span><span class="sxs-lookup"><span data-stu-id="007f8-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="007f8-179">İfadeler</span><span class="sxs-lookup"><span data-stu-id="007f8-179">Expressions</span></span><br><span data-ttu-id="007f8-180">(HTML kodlanmış)</span><span class="sxs-lookup"><span data-stu-id="007f8-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="007f8-181">Örtülü:`@`</span><span class="sxs-lookup"><span data-stu-id="007f8-181">Implicit: `@`</span></span><br><span data-ttu-id="007f8-182">Açık:`@()`</span><span class="sxs-lookup"><span data-stu-id="007f8-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="007f8-183">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="007f8-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="007f8-184">Veri bağlama</span><span class="sxs-lookup"><span data-stu-id="007f8-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="007f8-185">Razor bileşen sınıfına üye eklemek `@code` için yönergeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="007f8-186">Bu teknik, ASP.NET `<script runat="server">...</script>` Web Forms kullanıcı denetiminde veya sayfasında bir blok kullanmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="007f8-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="007f8-187">Razor C#'a dayandığı için, c# projesi *(.csproj)* içinden derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="007f8-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="007f8-188">Bir Visual Basic projesinden *.razor* dosyaları *(.vbproj)* derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="007f8-189">Blazor projenizden Visual Basic projelerine hala başvuruyapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="007f8-190">Tam tersi de doğrudur.</span><span class="sxs-lookup"><span data-stu-id="007f8-190">The opposite is true too.</span></span>

<span data-ttu-id="007f8-191">Tam bir Razor sözdizimi başvurusu [için, ASP.NET Core için Razor sözdizimi başvurusuna](/aspnet/core/mvc/views/razor)bakın.</span><span class="sxs-lookup"><span data-stu-id="007f8-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="007f8-192">Bileşenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="007f8-192">Use components</span></span>

<span data-ttu-id="007f8-193">Normal HTML'nin yanı sıra, bileşenler diğer bileşenleri de görüntüleme mantığının bir parçası olarak kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="007f8-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="007f8-194">Razor'da bir bileşeni kullanma sözdizimi, ASP.NET bir Web Forms uygulamasında kullanıcı denetimi kullanmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="007f8-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="007f8-195">Bileşenler, bileşenin tür adı ile eşleşen bir öğe etiketi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="007f8-196">Örneğin, buna benzer `Counter` bir bileşen ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="007f8-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="007f8-197">Web Formlar ASP.NET aksine, Blazor bileşenleri:</span><span class="sxs-lookup"><span data-stu-id="007f8-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="007f8-198">Öğe öneki kullanmayın (örneğin, `asp:`).</span><span class="sxs-lookup"><span data-stu-id="007f8-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="007f8-199">Sayfada veya *web.config'de*kayıt gerektirmeyin.</span><span class="sxs-lookup"><span data-stu-id="007f8-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="007f8-200">.NET türleri gibi Razor bileşenleri düşünün, çünkü tam olarak ne oldukları.</span><span class="sxs-lookup"><span data-stu-id="007f8-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="007f8-201">Bileşeni içeren derleme başvurulmuşsa, bileşen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="007f8-202">Bileşenin ad alanını kapsamına getirmek için `@using` yönergeyi uygulayın:</span><span class="sxs-lookup"><span data-stu-id="007f8-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="007f8-203">Varsayılan Blazor projelerinde görüldüğü gibi, direktifleri `@using` *_Imports.jilet* dosyasına koymak yaygındır, böylece aynı dizindeki ve çocuk dizindeki tüm *.razor* dosyalarına aktarılırlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="007f8-204">Bir bileşenin ad alanı kapsamiçinde değilse, c#'da olduğu gibi, tam tür adını kullanarak bir bileşen belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="007f8-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="007f8-205">Bileşen parametreleri</span><span class="sxs-lookup"><span data-stu-id="007f8-205">Component parameters</span></span>

<span data-ttu-id="007f8-206">web formlarını ASP.NET, genel özellikleri kullanarak denetimlere parametreler ve veriler aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="007f8-207">Bu özellikler öznitelikleri kullanılarak biçimlendirme olarak ayarlanabilir veya doğrudan kod olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="007f8-208">Blazor bileşenleri de benzer bir şekilde çalışır, ancak bileşen `[Parameter]` özellikleri de bileşen parametreleri olarak kabul edilecek öznitelik ile işaretlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="007f8-209">Aşağıdaki `Counter` bileşen, düğme her tıklatıldığında artış `IncrementAmount` `Counter` yapılması gereken miktarı belirtmek için kullanılabilecek bir bileşen parametresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="007f8-210">Blazor'da bir bileşen parametresi belirtmek için, web formlarında olduğu gibi bir öznitelik ASP.NET kullanın:</span><span class="sxs-lookup"><span data-stu-id="007f8-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="007f8-211">Olay işleyicileri</span><span class="sxs-lookup"><span data-stu-id="007f8-211">Event handlers</span></span>

<span data-ttu-id="007f8-212">Hem ASP.NET Web Formları hem de Blazor, Web-oi olaylarını işlemek için olay tabanlı bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="007f8-213">Bu tür olaylara örnek olarak düğme tıklamaları ve metin girişi verilebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="007f8-214">Web Formları ASP.NET, DOM tarafından açığa çıkarılan Web Telefonu etkinliklerini işlemek için HTML sunucu denetimlerini kullanırsınız veya web sunucusu denetimleri tarafından açığa çıkarılan olayları işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="007f8-215">Olaylar, form post-back istekleri aracılığıyla sunucuda su yüzüne çıkar.</span><span class="sxs-lookup"><span data-stu-id="007f8-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="007f8-216">Aşağıdaki Web Formları düğmesine tıklama örneğini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="007f8-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="007f8-217">*Counter.ascx*</span><span class="sxs-lookup"><span data-stu-id="007f8-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="007f8-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="007f8-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="007f8-219">Blazor'da, doğrudan formun `@on{event}`yönerge özniteliklerini kullanarak DOM Web Gücü olayları için işleyicileri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="007f8-220">`{event}` Yer tutucu, olayın adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="007f8-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="007f8-221">Örneğin, şu gibi düğme tıklamalarını dinleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="007f8-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="007f8-222">Olay işleyicileri, olay hakkında daha fazla bilgi sağlamak için isteğe bağlı, olaya özgü bir bağımsız değişkeni kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="007f8-223">Örneğin, fare olayları bir `MouseEventArgs` bağımsız değişken alabilir, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="007f8-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="007f8-224">Olay işleyicisi için bir yöntem grubuna atıfta bulunarak yerine lambda ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="007f8-225">Lambda ifadesi, diğer kapsam içi değerleri kapatmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="007f8-226">Olay işleyicileri eşzamanlı veya eşzamanlı olarak yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="007f8-227">Örneğin, aşağıdaki `OnClick` olay işleyicisi eşeşitleme yürütülür:</span><span class="sxs-lookup"><span data-stu-id="007f8-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="007f8-228">Bir olay işlendikten sonra, bileşen tüm bileşen durumu değişikliklerini hesaba katmak üzere işlenir.</span><span class="sxs-lookup"><span data-stu-id="007f8-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="007f8-229">Eşsenkronize olay işleyicileri ile, bileşen işleyici yürütme tamamlandıktan hemen sonra işlenir.</span><span class="sxs-lookup"><span data-stu-id="007f8-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="007f8-230">Bileşen, eşzamanlı `Task` tamamlandıktan sonra *yeniden* işlenir.</span><span class="sxs-lookup"><span data-stu-id="007f8-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="007f8-231">Bu eşzamanlı yürütme modu, asenkron `Task` hala devam ederken bazı uygun Kullanıcı Arabirimi işlemek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="007f8-232">Bileşenler, bir `EventCallback<TValue>`bileşen parametresi tanımlayarak kendi olaylarını da tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="007f8-233">Olay geri aramaları DOM Kullanıcı Arabirimi olay işleyicilerinin tüm varyasyonlarını destekler: isteğe bağlı bağımsız değişkenler, senkron veya eşzamanlı, yöntem grupları veya lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="007f8-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="007f8-234">Veri bağlama</span><span class="sxs-lookup"><span data-stu-id="007f8-234">Data binding</span></span>

<span data-ttu-id="007f8-235">Blazor, kullanıcı bir kullanıcı bir kullanıcı bir kullanıcı tarafından bileşenin durumuna verileri bağlamak için basit bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="007f8-236">Bu yaklaşım, veri kaynaklarından UI denetimlerine veri bağlamak için ASP.NET Web Formları'ndaki özelliklerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="007f8-237">[Verilerle Başa Çıkma](data.md) bölümünde farklı veri kaynaklarından gelen verileri işlemeyi ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="007f8-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="007f8-238">UI bileşeninden bileşenin durumuna iki yönlü veri bağlama oluşturmak için `@bind` yönerge özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="007f8-239">Aşağıdaki örnekte, onay kutusunun değeri `isChecked` alana bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="007f8-240">Bileşen işlendiğinde, onay kutusunun değeri `isChecked` alanın değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="007f8-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="007f8-241">Kullanıcı onay kutusunu attığında, `onchange` olay ateşlenir ve `isChecked` alan yeni değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="007f8-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="007f8-242">Bu `@bind` durumda sözdizimi aşağıdaki biçimlendirmeye eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="007f8-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="007f8-243">Bağlama için kullanılan olayı değiştirmek için `@bind:event` özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="007f8-244">Bileşenler, parametrelerine veri bağlamayı da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="007f8-245">Veri bağlama için, bağlanabilir parametreyle aynı ada sahip bir olay geri arama parametresi tanımla.</span><span class="sxs-lookup"><span data-stu-id="007f8-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="007f8-246">Ada "Değiştirildi" soneki eklenir.</span><span class="sxs-lookup"><span data-stu-id="007f8-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="007f8-247">*PasswordBox.razor*</span><span class="sxs-lookup"><span data-stu-id="007f8-247">*PasswordBox.razor*</span></span>

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="007f8-248">Bir veriyi temel deki bir UI öğesine bağlamak için, değeri ayarlayın ve olayı `@bind` özniteliği kullanmak yerine doğrudan UI öğesiüzerinde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="007f8-249">Bileşen parametresine bağlamak için, `@bind-{Parameter}` bağlamak istediğiniz parametreyi belirtmek için bir öznitelik kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="007f8-250">Durum değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="007f8-250">State changes</span></span>

<span data-ttu-id="007f8-251">Bileşenin durumu normal bir Ara-Görüntü olayı veya olay geri araması dışında değiştiyse, bileşenin yeniden işlenmesi gerektiğini el ile işaret etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="007f8-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="007f8-252">Bir bileşenin durumunun değiştiğini bildirmek için `StateHasChanged` bileşendeki yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="007f8-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="007f8-253">Aşağıdaki örnekte, bileşen, uygulamanın `AppState` diğer bölümleri tarafından güncelleştirilebilen bir hizmetten gelen bir iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="007f8-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="007f8-254">Bileşen, `StateHasChanged` ileti güncelleştirildiğinde `AppState.OnChange` bileşenin işlenmesi için yöntemini olaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="007f8-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="007f8-255">Bileşen yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="007f8-255">Component lifecycle</span></span>

<span data-ttu-id="007f8-256">ASP.NET Web Forms çerçevesi, modüller, sayfalar ve denetimler için iyi tanımlanmış yaşam döngüsü yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="007f8-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="007f8-257">Örneğin, aşağıdaki denetim `Init`, , `Load`ve `UnLoad` yaşam döngüsü olaylar için olay işleyicileri uygular:</span><span class="sxs-lookup"><span data-stu-id="007f8-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="007f8-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="007f8-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="007f8-259">Blazor bileşenleri de iyi tanımlanmış bir yaşam döngüsüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="007f8-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="007f8-260">Bileşenin yaşam döngüsü, bileşen durumunu başlatmave gelişmiş bileşen davranışlarını uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="007f8-261">Blazor'un tüm bileşen yaşam döngüsü yöntemlerinin hem senkron hem de eşzamanlı versiyonları vardır.</span><span class="sxs-lookup"><span data-stu-id="007f8-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="007f8-262">Bileşen oluşturma eşzamanlıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-262">Component rendering is synchronous.</span></span> <span data-ttu-id="007f8-263">Bileşen oluşturmanın bir parçası olarak eşzamanlı mantığı çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="007f8-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="007f8-264">Tüm eşzamanlı mantık bir yaşam döngüsü `async` yönteminin bir parçası olarak yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="007f8-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="007f8-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="007f8-265">OnInitialized</span></span>

<span data-ttu-id="007f8-266">Ve `OnInitialized` `OnInitializedAsync` yöntemler bileşeni başlatmaiçin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007f8-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="007f8-267">Bir bileşen genellikle ilk işlendikten sonra başharfe getirilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="007f8-268">Bir bileşen para başlatılan sonra, sonunda elden önce birden çok kez işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="007f8-269">Yöntem, `OnInitialized` web formları `Page_Load` sayfalarında ve denetimlerine ASP.NET olayla benzer.</span><span class="sxs-lookup"><span data-stu-id="007f8-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="007f8-270">OnparametersSet</span><span class="sxs-lookup"><span data-stu-id="007f8-270">OnParametersSet</span></span>

<span data-ttu-id="007f8-271">Ve `OnParametersSet` `OnParametersSetAsync` yöntemleri bir bileşenin üst parametre aldı ve değer özelliklerine atanır denir.</span><span class="sxs-lookup"><span data-stu-id="007f8-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="007f8-272">Bu yöntemler bileşen başlatmadan sonra yürütülür ve *bileşen her işlendi.*</span><span class="sxs-lookup"><span data-stu-id="007f8-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="007f8-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="007f8-273">OnAfterRender</span></span>

<span data-ttu-id="007f8-274">Ve `OnAfterRender` `OnAfterRenderAsync` yöntemler, bir bileşen işleme yi bitirdikten sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="007f8-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="007f8-275">Öğe ve bileşen başvuruları bu noktada doldurulur (aşağıdaki kavramlar hakkında daha fazla bilgi).</span><span class="sxs-lookup"><span data-stu-id="007f8-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="007f8-276">Bu noktada tarayıcıile etkileşim etkindir.</span><span class="sxs-lookup"><span data-stu-id="007f8-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="007f8-277">DOM ve JavaScript yürütme ile etkileşimler güvenle gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="007f8-278">`OnAfterRender`ve `OnAfterRenderAsync` *sunucuda önişleme çağrılırken çağrılmaz.*</span><span class="sxs-lookup"><span data-stu-id="007f8-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="007f8-279">`firstRender` Parametre, `true` bileşenin ilk işlenme zamanıdır; aksi takdirde, `false`değeri .</span><span class="sxs-lookup"><span data-stu-id="007f8-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="007f8-280">ıdisposable</span><span class="sxs-lookup"><span data-stu-id="007f8-280">IDisposable</span></span>

<span data-ttu-id="007f8-281">Blazor bileşenleri, `IDisposable` bileşen UI'den kaldırıldığında kaynakları elden çıkarmak için uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="007f8-282">Bir Razor bileşeni `IDispose` yönergeyi `@implements` kullanarak uygulayabilir:</span><span class="sxs-lookup"><span data-stu-id="007f8-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="007f8-283">Bileşen başvurularını yakalama</span><span class="sxs-lookup"><span data-stu-id="007f8-283">Capture component references</span></span>

<span data-ttu-id="007f8-284">ASP.NET Web Formlarında, bir denetim örneğini kimliğine atıfta bulunarak doğrudan kod olarak işlemek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="007f8-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="007f8-285">Blazor'da, çok daha az yaygın olmasına rağmen, bir bileşene yapılan bir başvuruyup manipüle etmek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="007f8-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="007f8-286">Blazor'da bir bileşen başvurusu `@ref` yakalamak için yönerge özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="007f8-287">Öznitelik değeri, başvurulan bileşenle aynı türde bir ayaralanının adı yla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="007f8-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="007f8-288">Üst bileşen işlendiğinde, alan alt bileşen örneğiyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="007f8-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="007f8-289">Daha sonra yöntem üzerinde arama veya başka bir şekilde, bileşen örneği işlemek.</span><span class="sxs-lookup"><span data-stu-id="007f8-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="007f8-290">Bileşen başvurularını kullanarak bileşen durumunu doğrudan manipüle etmek önerilmez.</span><span class="sxs-lookup"><span data-stu-id="007f8-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="007f8-291">Bunu yapmak, bileşenin doğru zamanlarda otomatik olarak işlenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="007f8-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="007f8-292">Eleman başvurularını yakalama</span><span class="sxs-lookup"><span data-stu-id="007f8-292">Capture element references</span></span>

<span data-ttu-id="007f8-293">Blazor bileşenleri bir öğeye yapılan başvuruları yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="007f8-294">ASP.NET Web Formlar'daki HTML sunucu denetimlerinden farklı olarak, Blazor'daki bir öğe referansını kullanarak DOM'u doğrudan manipüle edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="007f8-295">Blazor, DOM difüzyon algoritmasını kullanarak sizin için en ÇOK DOM etkileşimini yönetir.</span><span class="sxs-lookup"><span data-stu-id="007f8-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="007f8-296">Blazor'da yakalanan eleman başvuruları opak.</span><span class="sxs-lookup"><span data-stu-id="007f8-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="007f8-297">Ancak, bir JavaScript interop aramasında belirli bir öğe başvurusu geçmek için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="007f8-298">JavaScript interop hakkında daha fazla bilgi için Core [Blazor JavaScript interop ASP.NET](/aspnet/core/blazor/javascript-interop)bakın.</span><span class="sxs-lookup"><span data-stu-id="007f8-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="007f8-299">Şablonlu bileşenler</span><span class="sxs-lookup"><span data-stu-id="007f8-299">Templated components</span></span>

<span data-ttu-id="007f8-300">Web Formları ASP.NET *şablonlanmış denetimler*oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="007f8-301">Şablondenetimler, geliştiricinin kapsayıcı denetimini işlemek için kullanılan HTML'nin bir bölümünü belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="007f8-302">Şablonlanmış sunucu denetimleri oluşturma mekaniği karmaşıktır, ancak verileri kullanıcıtarafından özelleştirilebilir bir şekilde işlemek için güçlü senaryolar sağlar.</span><span class="sxs-lookup"><span data-stu-id="007f8-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="007f8-303">Şablonlanmış denetimörnekleri `Repeater` şunlardır ve `DataList`.</span><span class="sxs-lookup"><span data-stu-id="007f8-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="007f8-304">Blazor bileşenleri de tip `RenderFragment` veya `RenderFragment<T>`bileşen parametreleri tanımlayarak şablonolabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="007f8-305">A, `RenderFragment` daha sonra bileşen tarafından oluşturulabilen bir jilet biçimlendirme yığınını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="007f8-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="007f8-306">A, `RenderFragment<T>` render parçası işlendiğinde belirtilebilen bir parametre alan bir Jilet biçimlendirmesi yığınıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="007f8-307">Alt içerik</span><span class="sxs-lookup"><span data-stu-id="007f8-307">Child content</span></span>

<span data-ttu-id="007f8-308">Blazor bileşenleri alt içeriklerini `RenderFragment` bir olarak yakalayabilir ve bu içeriği bileşen oluşturmanın bir parçası olarak işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="007f8-309">Alt içeriği yakalamak için, bir `RenderFragment` bileşen parametresi yazın ve adını belirleyin. `ChildContent`</span><span class="sxs-lookup"><span data-stu-id="007f8-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="007f8-310">*ChildContentComponent.razor*</span><span class="sxs-lookup"><span data-stu-id="007f8-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="007f8-311">Bir üst bileşen daha sonra normal Razor sözdizimini kullanarak alt içerik sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="007f8-312">Şablon parametreleri</span><span class="sxs-lookup"><span data-stu-id="007f8-312">Template parameters</span></span>

<span data-ttu-id="007f8-313">Şablonlanmış bir Blazor bileşeni de tür `RenderFragment` veya `RenderFragment<T>`birden çok bileşen parametreleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="007f8-314">Bir `RenderFragment<T>` parametre çağrıldığı zaman belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="007f8-315">Bir bileşen için genel bir tür parametresi belirtmek için Razor yönergesini `@typeparam` kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="007f8-316">*SimpleListView.razor*</span><span class="sxs-lookup"><span data-stu-id="007f8-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="007f8-317">Şablonlu bir bileşen kullanırken, şablon parametreleri parametrelerin adlarıyla eşleşen alt öğeler kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="007f8-318">Öğeler olarak `RenderFragment<T>` geçirilen tür bileşen bağımsız değişkenleri, örtülü bir parametreye sahiptir. `context`</span><span class="sxs-lookup"><span data-stu-id="007f8-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="007f8-319">Alt öğedeki özniteliği kullanarak `Context` bu uygulama parametresinin adını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007f8-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="007f8-320">Herhangi bir genel tür parametreleri, tür parametresinin adıyla eşleşen bir öznitelik kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="007f8-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="007f8-321">Tür parametresi mümkünse çıkarılacaktır:</span><span class="sxs-lookup"><span data-stu-id="007f8-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="007f8-322">Bu bileşenin çıktısı aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="007f8-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="007f8-323">Kod arkası</span><span class="sxs-lookup"><span data-stu-id="007f8-323">Code-behind</span></span>

<span data-ttu-id="007f8-324">Blazor bileşeni genellikle tek bir *.razor* dosyasında yazar.</span><span class="sxs-lookup"><span data-stu-id="007f8-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="007f8-325">Ancak, kod ve biçimlendirmeyi kod arkası dosyasını kullanarak ayırmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="007f8-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="007f8-326">Bileşen dosyasını kullanmak için, bileşen dosyasının dosya adıyla eşleşen ancak *.cs* uzantısı eklenmiştir *(Counter.razor.cs)* içeren bir C# dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="007f8-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="007f8-327">Bileşen için bir taban sınıf tanımlamak için C# dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="007f8-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="007f8-328">Taban sınıfa istediğiniz her şeyi adlandırabilirsiniz, ancak sınıfın bileşen sınıfıyla aynı ada ad `Base` vermek yaygındır, ancak bir uzantı eklenmirken (`CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="007f8-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="007f8-329">Bileşen tabanlı sınıf da. `ComponentBase`</span><span class="sxs-lookup"><span data-stu-id="007f8-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="007f8-330">Daha sonra, Razor bileşen dosyasında, bileşeniçin taban sınıf`@inherits CounterBase`( belirtmek için `@inherits` yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="007f8-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="007f8-331">*Counter.razor*</span><span class="sxs-lookup"><span data-stu-id="007f8-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="007f8-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="007f8-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="007f8-333">Bileşenin alt sınıftaki üyelerinin görünürlüğü bileşen `protected` sınıfı `public` tarafından görülebilmeli veya görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="007f8-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="007f8-334">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="007f8-334">Additional resources</span></span>

<span data-ttu-id="007f8-335">Önceki Blazor bileşenlerinin tüm yönleriyle ayrıntılı bir tedavi değildir.</span><span class="sxs-lookup"><span data-stu-id="007f8-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="007f8-336">Core Razor bileşenlerinin nasıl [oluşturulup ASP.NET kullanılacağı](/aspnet/core/blazor/components)hakkında daha fazla bilgi için Blazor belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="007f8-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="007f8-337">[Önceki](app-startup.md)
>[Sonraki](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="007f8-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
