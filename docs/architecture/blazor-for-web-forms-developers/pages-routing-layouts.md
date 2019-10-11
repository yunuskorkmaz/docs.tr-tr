---
title: Sayfalar, yönlendirme ve düzenler
description: Blazor 'de sayfa oluşturmayı, istemci tarafı yönlendirme ile çalışmayı ve sayfa düzenlerini yönetmeyi öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: c31544156250a9e97ff8c0b17338f418817b21d2
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275824"
---
# <a name="pages-routing-and-layouts"></a>Sayfalar, yönlendirme ve düzenler

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms uygulamalar *. aspx* dosyalarında tanımlanan sayfalardan oluşur. Her sayfanın adresi, projedeki fiziksel dosya yolunu temel alır. Bir tarayıcı sayfada bir istek yaptığında, sayfanın içeriği sunucu üzerinde dinamik olarak işlenir. Sayfanın HTML işaretlemesi ve sunucu denetimleri için işleme hesapları.

Blazor ' de, uygulamadaki her sayfa, genellikle bir veya daha fazla belirtilen rotasıyla bir *. Razor* dosyasında tanımlanan bir bileşendir. Yönlendirme genellikle belirli bir sunucu isteğiyle birlikte istemci tarafı olur. Tarayıcı önce uygulamanın kök adresine bir istek yapar. Blazor uygulamasında bir kök `Router` bileşeni daha sonra gezinme isteklerini ve bunları doğru bileşene göre ele alır.

Blazor *derin bağlamayı*da destekler. Derin bağlama, tarayıcı uygulama kökü dışında belirli bir rotaya istek yaptığında oluşur. Sunucuya gönderilen derin bağlantı istekleri Blazor uygulamasına yönlendirilir ve ardından istek istemci tarafını doğru bileşene yönlendirir.

ASP.NET Web Forms basit bir sayfa aşağıdaki biçimlendirmeyi içerebilir:

*Ad. aspx*

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

*Name.aspx.cs*

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

Bir Blazor uygulamasındaki eşdeğer sayfa şöyle görünür:

*Name. Razor*

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

## <a name="create-pages"></a>Sayfa oluştur

Blazor içinde bir sayfa oluşturmak için bir bileşen oluşturun ve bileşen için yolu belirtmek üzere `@page` Razor yönergesini ekleyin. @No__t-0 yönergesi, bu bileşene eklenecek yol şablonu olan tek bir parametre alır.

```razor
@page "/counter"
```

Yol şablonu parametresi gereklidir. ASP.NET Web Forms aksine, bir *Blazor bileşenine olan* yol dosyanın konumundan (gelecekte bir özellik eklenebilir olmasına rağmen) çıkarsanamıyor.

Yol şablonu sözdizimi, ASP.NET Web Forms yönlendirme için kullanılan temel sözdizimidir. Rota parametreleri, küme ayraçları kullanılarak şablonda belirtilmiştir. Blazor, yönlendirme değerlerini aynı ada (büyük/küçük harfe duyarsız) sahip bileşen parametrelerine bağlar.

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

Ayrıca, yol parametresinin değeri üzerinde kısıtlamalar belirtebilirsiniz. Örneğin, ürün KIMLIĞINI `int` olarak kısıtlamak için:

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Blazor tarafından desteklenen yol kısıtlamalarının tam listesi için bkz. [route kısıtlamaları](/aspnet/core/blazor/routing#route-constraints).

## <a name="router-component"></a>Yönlendirici bileşeni

Blazor içinde yönlendirme `Router` bileşeni tarafından işlenir. @No__t-0 bileşeni genellikle uygulamanın kök bileşeninde (*app. Razor*) kullanılır.

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

@No__t-0 bileşeni, belirtilen `AppAssembly` ' deki ve isteğe bağlı olarak belirtilen `AdditionalAssemblies` ' de yönlendirilebilir bileşenleri bulur. Tarayıcı gezinirse, `Router` gezinmeyi durdurur ve `Found` parametresinin içeriğini ayıklanan `RouteData` ile işler, ancak bir yol adresle eşleşiyorsa, `Router` `NotFound` parametresini işler.

@No__t-0 bileşeni, varsa `RouteData` tarafından belirtilen eşleşen bileşeni, varsa düzeniyle işlemeyi işler. Eşleşen bileşen bir düzene sahip değilse, isteğe bağlı olarak belirtilen `DefaultLayout` kullanılır.

@No__t-0 bileşeni, alt içeriğini belirtilen düzen içinde işler. Bu bölümün ilerleyen kısımlarında daha sonra mizanpajlara daha ayrıntılı bir şekilde bakacağız.

## <a name="navigation"></a>Gezinti

ASP.NET Web Forms ' de, tarayıcıya yeniden yönlendirme yanıtı döndürerek, gezintiyi farklı bir sayfaya tetiklersiniz. Örneğin:

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

Blazor içinde yeniden yönlendirme yanıtı döndürülmesi genellikle mümkün değildir. Blazor, istek-yanıt modeli kullanmaz. Ancak, JavaScript ile yaptığınız gibi tarayıcı gezginlerini doğrudan tetikleyebilirsiniz.

Blazor, şu şekilde kullanılabilecek bir `NavigationManager` hizmeti sağlar:

* Geçerli tarayıcı adresini al
* Temel adresi al
* Tüm gezinmeler tetiklemeleri
* Adres değiştiğinde bildirim alın

Farklı bir adrese gitmek için `NavigateTo` yöntemini kullanın:

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

Tüm `NavigationManager` üyelerinin açıklaması için bkz. [URI ve gezinti durumu yardımcıları](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).

## <a name="base-urls"></a>Temel URL 'Ler

Blazor uygulamanız bir temel yol altında dağıtılmışsa, iş özelliğine yönlendirme için `<base>` etiketini kullanarak temel URL 'YI sayfa meta verilerinde belirtmeniz gerekir. Uygulamanın ana bilgisayar sayfası Razor kullanılarak sunucu tarafından işlendiyse, uygulamanın temel adresini belirtmek için `~/` sözdizimini kullanabilirsiniz. Ana bilgisayar sayfası statik HTML ise, temel URL 'YI açıkça belirtmeniz gerekir.

```html
<base href="~/" />
```

## <a name="page-layout"></a>Sayfa düzeni

ASP.NET Web Forms sayfa düzeni ana sayfalar tarafından işlenir. Ana sayfalar, bir veya daha fazla içerik yer tutucusu içeren bir şablonu tanımlar ve bu, tek tek sayfalarla sağlanabilir. Ana sayfalar *. Master* dosyalarında tanımlanır ve `<%@ Master %>` yönergesiyle başlar. *. Master* dosyalarının içeriği *. aspx* sayfası olarak kodlanır, ancak sayfaların içerik sağlayabileceği yerleri işaretlemek için `<asp:ContentPlaceHolder>` denetimlerin eklenmesiyle birlikte.

*Site. Master*

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

Blazor ' de, düzen bileşenlerini kullanarak sayfa düzeni işlemiş olursunuz. Düzen bileşenleri, sayfanın içeriğini işlemek için kullanılabilen `RenderFragment` türünde tek bir `Body` özelliği tanımlayan `LayoutComponentBase` ' dan devralınır.

*MainLayout. Razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

Düzen içeren sayfa işlendiğinde sayfa, düzenin `Body` özelliğini oluşturduğu konumdaki belirtilen düzenin içeriği içinde işlenir.

Bir sayfaya düzen uygulamak için `@layout` yönergesini kullanın:

```razor
@layout MainLayout
```

Bir klasör ve alt klasörlerdeki tüm bileşenlerin yerleşimini *_ımports. Razor* dosyası kullanarak belirtebilirsiniz. Ayrıca, [yönlendirici bileşenini](#router-component)kullanarak tüm sayfalarınızın varsayılan bir yerleşimini belirtebilirsiniz.

Ana sayfalar birden çok içerik yer tutucusu tanımlayabilir, ancak Blazor içindeki mizanpajlar yalnızca tek bir `Body` özelliğine sahiptir. Bu Blazor düzen bileşenleri sınırlaması, gelecek sürümlerde tamamen değinilecek.

ASP.NET Web Forms içindeki ana sayfalar iç içe olabilir. Diğer bir deyişle, ana sayfa bir ana sayfa da kullanabilir. Blazor içindeki düzen bileşenleri çok fazla iç içe olabilir. Düzen bileşenine bir düzen bileşeni uygulayabilirsiniz. İç düzenin içeriği dış düzen içinde işlenir.

*ChildLayout. Razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index. Razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

Sayfa için işlenmiş çıkış daha sonra şöyle olacaktır:

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Blazor içindeki düzenler genellikle bir sayfa için kök HTML öğelerini (`<html>`, `<body>`, `<head>` vb.) tanımlamaz. Kök HTML öğeleri, uygulamanın ilk HTML içeriğini işlemek için kullanılan bir Blazor uygulamasının konak sayfasında tanımlanır (bkz. [önyükleme Blazor](project-structure.md#bootstrap-blazor)). Konak sayfası, çevreleyen biçimlendirme ile uygulama için birden çok kök bileşeni işleyebilir.

Sayfalar da dahil olmak üzere Blazor içindeki bileşenler `<script>` etiketleri işleyebilir. Bu işleme kısıtlaması, `<script>` etiketlerinin bir kez yüklendiğinden ve değiştirilemediğinden oluşur. Razor söz dizimi kullanarak etiketleri dinamik olarak işlemeye çalışırsanız beklenmeyen bir davranış ortaya çıkabilir. Bunun yerine, tüm `<script>` etiketlerinin uygulamanın ana bilgisayar sayfasına eklenmesi gerekir.

>[!div class="step-by-step"]
>[Önceki](components.md)
>[İleri](state-management.md)
