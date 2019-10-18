---
title: Sayfalar, yönlendirme ve düzenler
description: Blazor 'de sayfa oluşturmayı, istemci tarafı yönlendirme ile çalışmayı ve sayfa düzenlerini yönetmeyi öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 693eee270a46ccb56ed5fef8fced1d4a1cf1974f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520235"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="afe2a-103">Sayfalar, yönlendirme ve düzenler</span><span class="sxs-lookup"><span data-stu-id="afe2a-103">Pages, routing, and layouts</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="afe2a-104">ASP.NET Web Forms uygulamalar *. aspx* dosyalarında tanımlanan sayfalardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="afe2a-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="afe2a-105">Her sayfanın adresi, projedeki fiziksel dosya yolunu temel alır.</span><span class="sxs-lookup"><span data-stu-id="afe2a-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="afe2a-106">Bir tarayıcı sayfada bir istek yaptığında, sayfanın içeriği sunucu üzerinde dinamik olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="afe2a-107">Sayfanın HTML işaretlemesi ve sunucu denetimleri için işleme hesapları.</span><span class="sxs-lookup"><span data-stu-id="afe2a-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="afe2a-108">Blazor ' de, uygulamadaki her sayfa, genellikle bir veya daha fazla belirtilen rotasıyla bir *. Razor* dosyasında tanımlanan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="afe2a-109">Yönlendirme genellikle belirli bir sunucu isteğiyle birlikte istemci tarafı olur.</span><span class="sxs-lookup"><span data-stu-id="afe2a-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="afe2a-110">Tarayıcı önce uygulamanın kök adresine bir istek yapar.</span><span class="sxs-lookup"><span data-stu-id="afe2a-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="afe2a-111">Blazor uygulamasında bir kök `Router` bileşeni daha sonra gezinme isteklerini ve bunları doğru bileşene göre ele alır.</span><span class="sxs-lookup"><span data-stu-id="afe2a-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

<span data-ttu-id="afe2a-112">Blazor *derin bağlamayı*da destekler.</span><span class="sxs-lookup"><span data-stu-id="afe2a-112">Blazor also supports *deep linking*.</span></span> <span data-ttu-id="afe2a-113">Derin bağlama, tarayıcı uygulama kökü dışında belirli bir rotaya istek yaptığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="afe2a-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="afe2a-114">Sunucuya gönderilen derin bağlantı istekleri Blazor uygulamasına yönlendirilir ve ardından istek istemci tarafını doğru bileşene yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="afe2a-115">ASP.NET Web Forms basit bir sayfa aşağıdaki biçimlendirmeyi içerebilir:</span><span class="sxs-lookup"><span data-stu-id="afe2a-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="afe2a-116">*Ad. aspx*</span><span class="sxs-lookup"><span data-stu-id="afe2a-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="afe2a-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="afe2a-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="afe2a-118">Bir Blazor uygulamasındaki eşdeğer sayfa şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="afe2a-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="afe2a-119">*Name. Razor*</span><span class="sxs-lookup"><span data-stu-id="afe2a-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="afe2a-120">Sayfa oluştur</span><span class="sxs-lookup"><span data-stu-id="afe2a-120">Create pages</span></span>

<span data-ttu-id="afe2a-121">Blazor içinde bir sayfa oluşturmak için bir bileşen oluşturun ve bileşen için yolu belirtmek üzere `@page` Razor yönergesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afe2a-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="afe2a-122">@No__t_0 yönergesi, bu bileşene eklenecek yol şablonu olan tek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="afe2a-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="afe2a-123">Yol şablonu parametresi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-123">The route template parameter is required.</span></span> <span data-ttu-id="afe2a-124">ASP.NET Web Forms aksine, bir *Blazor bileşenine olan* yol dosyanın konumundan (gelecekte bir özellik eklenebilir olmasına rağmen) çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="afe2a-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="afe2a-125">Yol şablonu sözdizimi, ASP.NET Web Forms yönlendirme için kullanılan temel sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="afe2a-126">Rota parametreleri, küme ayraçları kullanılarak şablonda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-126">Route parameters are specified in the template using braces.</span></span> <span data-ttu-id="afe2a-127">Blazor, yönlendirme değerlerini aynı ada (büyük/küçük harfe duyarsız) sahip bileşen parametrelerine bağlar.</span><span class="sxs-lookup"><span data-stu-id="afe2a-127">Blazor will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="afe2a-128">Ayrıca, yol parametresinin değeri üzerinde kısıtlamalar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="afe2a-129">Örneğin, ürün KIMLIĞINI `int` olarak kısıtlamak için:</span><span class="sxs-lookup"><span data-stu-id="afe2a-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="afe2a-130">Blazor tarafından desteklenen yol kısıtlamalarının tam listesi için bkz. [route kısıtlamaları](/aspnet/core/blazor/routing#route-constraints).</span><span class="sxs-lookup"><span data-stu-id="afe2a-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="afe2a-131">Yönlendirici bileşeni</span><span class="sxs-lookup"><span data-stu-id="afe2a-131">Router component</span></span>

<span data-ttu-id="afe2a-132">Blazor içinde yönlendirme `Router` bileşeni tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="afe2a-133">@No__t_0 bileşen genellikle uygulamanın kök bileşeninde (*app. Razor*) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afe2a-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="afe2a-134">@No__t_0 bileşeni, belirtilen `AppAssembly` ve isteğe bağlı olarak belirtilen `AdditionalAssemblies` yönlendirilebilir bileşenleri bulur.</span><span class="sxs-lookup"><span data-stu-id="afe2a-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="afe2a-135">Tarayıcı gezinirse, `Router` gezinmeyi durdurur ve `Found` parametresinin içeriğini ayıklanan `RouteData` ile işler, ancak bir yol adresle eşleşiyorsa, `Router` `NotFound` parametresini işler.</span><span class="sxs-lookup"><span data-stu-id="afe2a-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="afe2a-136">@No__t_0 bileşeni, varsa, `RouteData` tarafından belirtilen eşleşen bileşeni, varsa düzenine göre işlemeyi işler.</span><span class="sxs-lookup"><span data-stu-id="afe2a-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="afe2a-137">Eşleşen bileşen bir düzene sahip değilse, isteğe bağlı olarak belirtilen `DefaultLayout` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afe2a-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="afe2a-138">@No__t_0 bileşeni, alt içeriğini belirtilen düzen içinde işler.</span><span class="sxs-lookup"><span data-stu-id="afe2a-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="afe2a-139">Bu bölümün ilerleyen kısımlarında daha sonra mizanpajlara daha ayrıntılı bir şekilde bakacağız.</span><span class="sxs-lookup"><span data-stu-id="afe2a-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="afe2a-140">Gezinti</span><span class="sxs-lookup"><span data-stu-id="afe2a-140">Navigation</span></span>

<span data-ttu-id="afe2a-141">ASP.NET Web Forms ' de, tarayıcıya yeniden yönlendirme yanıtı döndürerek, gezintiyi farklı bir sayfaya tetiklersiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="afe2a-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="afe2a-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="afe2a-143">Blazor içinde yeniden yönlendirme yanıtı döndürülmesi genellikle mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-143">Returning a redirect response isn't typically possible in Blazor.</span></span> <span data-ttu-id="afe2a-144">Blazor, istek-yanıt modeli kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-144">Blazor doesn't use a request-reply model.</span></span> <span data-ttu-id="afe2a-145">Ancak, JavaScript ile yaptığınız gibi tarayıcı gezginlerini doğrudan tetikleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

<span data-ttu-id="afe2a-146">Blazor, şu şekilde kullanılabilecek bir `NavigationManager` hizmeti sağlar:</span><span class="sxs-lookup"><span data-stu-id="afe2a-146">Blazor provides a `NavigationManager` service that can be used to:</span></span>

- <span data-ttu-id="afe2a-147">Geçerli tarayıcı adresini al</span><span class="sxs-lookup"><span data-stu-id="afe2a-147">Get the current browser address</span></span>
- <span data-ttu-id="afe2a-148">Temel adresi al</span><span class="sxs-lookup"><span data-stu-id="afe2a-148">Get the base address</span></span>
- <span data-ttu-id="afe2a-149">Tüm gezinmeler tetiklemeleri</span><span class="sxs-lookup"><span data-stu-id="afe2a-149">Trigger navigations</span></span>
- <span data-ttu-id="afe2a-150">Adres değiştiğinde bildirim alın</span><span class="sxs-lookup"><span data-stu-id="afe2a-150">Get notified when the address changes</span></span>

<span data-ttu-id="afe2a-151">Farklı bir adrese gitmek için `NavigateTo` yöntemini kullanın:</span><span class="sxs-lookup"><span data-stu-id="afe2a-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="afe2a-152">Tüm `NavigationManager` üyelerinin açıklaması için bkz. [URI ve gezinti durumu yardımcıları](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span><span class="sxs-lookup"><span data-stu-id="afe2a-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="afe2a-153">Temel URL 'Ler</span><span class="sxs-lookup"><span data-stu-id="afe2a-153">Base URLs</span></span>

<span data-ttu-id="afe2a-154">Blazor uygulamanız bir temel yol altında dağıtılmışsa, iş özelliğine yönlendirme için `<base>` etiketini kullanarak temel URL 'YI sayfa meta verilerinde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="afe2a-155">Uygulamanın ana bilgisayar sayfası Razor kullanılarak sunucu tarafından işlendiyse, uygulamanın temel adresini belirtmek için `~/` sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="afe2a-156">Ana bilgisayar sayfası statik HTML ise, temel URL 'YI açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="afe2a-157">Sayfa düzeni</span><span class="sxs-lookup"><span data-stu-id="afe2a-157">Page layout</span></span>

<span data-ttu-id="afe2a-158">ASP.NET Web Forms sayfa düzeni ana sayfalar tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="afe2a-159">Ana sayfalar, bir veya daha fazla içerik yer tutucusu içeren bir şablonu tanımlar ve bu, tek tek sayfalarla sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="afe2a-160">Ana sayfalar *. Master* dosyalarında tanımlanır ve `<%@ Master %>` yönergesi ile başlar.</span><span class="sxs-lookup"><span data-stu-id="afe2a-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="afe2a-161">*. Master* dosyalarının içeriği *. aspx* sayfası olarak kodlanır, ancak sayfaların içerik sağlayabileceği yerleri işaretlemek için `<asp:ContentPlaceHolder>` denetimlerin eklenmesiyle birlikte.</span><span class="sxs-lookup"><span data-stu-id="afe2a-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="afe2a-162">*Site. Master*</span><span class="sxs-lookup"><span data-stu-id="afe2a-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="afe2a-163">Blazor ' de, düzen bileşenlerini kullanarak sayfa düzeni işlemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="afe2a-164">Düzen bileşenleri, sayfanın içeriğini işlemek için kullanılabilen `RenderFragment` türünde tek bir `Body` özelliği tanımlayan `LayoutComponentBase` ' dan devralınır.</span><span class="sxs-lookup"><span data-stu-id="afe2a-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="afe2a-165">*MainLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="afe2a-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="afe2a-166">Düzen içeren sayfa işlendiğinde sayfa, düzenin `Body` özelliğini oluşturduğu konumdaki belirtilen düzenin içeriği içinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="afe2a-167">Bir sayfaya düzen uygulamak için `@layout` yönergesini kullanın:</span><span class="sxs-lookup"><span data-stu-id="afe2a-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="afe2a-168">Bir klasör ve alt klasörlerdeki tüm bileşenlerin yerleşimini *_ımports. Razor* dosyası kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="afe2a-169">Ayrıca, [yönlendirici bileşenini](#router-component)kullanarak tüm sayfalarınızın varsayılan bir yerleşimini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="afe2a-170">Ana sayfalar birden çok içerik yer tutucusu tanımlayabilir, ancak Blazor içindeki mizanpajlar yalnızca tek bir `Body` özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="afe2a-171">Bu Blazor düzen bileşenleri sınırlaması, gelecek sürümlerde tamamen değinilecek.</span><span class="sxs-lookup"><span data-stu-id="afe2a-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="afe2a-172">ASP.NET Web Forms içindeki ana sayfalar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="afe2a-173">Diğer bir deyişle, ana sayfa bir ana sayfa da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="afe2a-174">Blazor içindeki düzen bileşenleri çok fazla iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="afe2a-175">Düzen bileşenine bir düzen bileşeni uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="afe2a-176">İç düzenin içeriği dış düzen içinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="afe2a-177">*ChildLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="afe2a-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="afe2a-178">*Index. Razor*</span><span class="sxs-lookup"><span data-stu-id="afe2a-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="afe2a-179">Sayfa için işlenmiş çıkış daha sonra şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="afe2a-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="afe2a-180">Blazor içindeki düzenler genellikle bir sayfa için kök HTML öğelerini (`<html>`, `<body>`, `<head>` vb.) tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="afe2a-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="afe2a-181">Kök HTML öğeleri, uygulamanın ilk HTML içeriğini işlemek için kullanılan bir Blazor uygulamasının konak sayfasında tanımlanır (bkz. [önyükleme Blazor](project-structure.md#bootstrap-blazor)).</span><span class="sxs-lookup"><span data-stu-id="afe2a-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="afe2a-182">Konak sayfası, çevreleyen biçimlendirme ile uygulama için birden çok kök bileşeni işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="afe2a-183">Sayfalar da dahil olmak üzere Blazor içindeki bileşenler `<script>` etiketleri işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="afe2a-184">Bu işleme kısıtlaması, `<script>` etiketlerinin bir kez yüklendiğinden ve değiştirilemediğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="afe2a-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="afe2a-185">Razor söz dizimi kullanarak etiketleri dinamik olarak işlemeye çalışırsanız beklenmeyen bir davranış ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="afe2a-186">Bunun yerine, tüm `<script>` etiketlerinin uygulamanın ana bilgisayar sayfasına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="afe2a-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="afe2a-187">[Önceki](components.md)
>[İleri](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="afe2a-187">[Previous](components.md)
[Next](state-management.md)</span></span>
