---
title: Sayfalar, yönlendirme ve düzenler
description: İçinde sayfa oluşturmayı Blazor , istemci tarafı yönlendirme ile çalışmayı ve sayfa düzenlerini yönetmeyi öğrenin.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/19/2019
ms.openlocfilehash: 714ba0be7c2014895a75250a47e6ce448863eb6c
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267795"
---
# <a name="pages-routing-and-layouts"></a>Sayfalar, yönlendirme ve düzenler

ASP.NET Web Forms uygulamalar *. aspx* dosyalarında tanımlanan sayfalardan oluşur. Her sayfanın adresi, projedeki fiziksel dosya yolunu temel alır. Bir tarayıcı sayfada bir istek yaptığında, sayfanın içeriği sunucu üzerinde dinamik olarak işlenir. Sayfanın HTML işaretlemesi ve sunucu denetimleri için işleme hesapları.

' De Blazor , uygulamadaki her sayfa, genellikle bir *. Razor* dosyasında tanımlanan ve belirtilen bir veya daha fazla yol içeren bir bileşendir. Yönlendirme genellikle belirli bir sunucu isteğiyle birlikte istemci tarafı olur. Tarayıcı önce uygulamanın kök adresine bir istek yapar. `Router` Blazor Daha sonra uygulamadaki bir kök bileşen, gezinme isteklerini ve bunları doğru bileşene göre kesintiye uğratan işler.

Blazor*derin bağlamayı*da destekler. Derin bağlama, tarayıcı uygulama kökü dışında belirli bir rotaya istek yaptığında oluşur. Sunucuya gönderilen derin bağlantı istekleri Blazor uygulamaya yönlendirilir ve ardından istek istemci tarafını doğru bileşene yönlendirir.

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

Bir uygulamadaki eşdeğer sayfa şöyle Blazor görünür:

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

İçinde bir sayfa oluşturmak için Blazor , bir bileşen oluşturun ve `@page` bileşenin yolunu belirtmek için Razor yönergesini ekleyin. `@page`Yönergesi, bu bileşene eklenecek yol şablonu olan tek bir parametre alır.

```razor
@page "/counter"
```

Yol şablonu parametresi gereklidir. ASP.NET Web Forms aksine, Blazor bileşen yolu dosyanın konumundan (gelecekte eklenmiş bir özellik olabilir) *değil* .

Yol şablonu sözdizimi, ASP.NET Web Forms yönlendirme için kullanılan temel sözdizimidir. Rota parametreleri, küme ayraçları kullanılarak şablonda belirtilmiştir. Blazor rota değerlerini aynı ada (büyük/küçük harfe duyarsız) sahip bileşen parametrelerine bağlayacaktır.

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

Ayrıca, yol parametresinin değeri üzerinde kısıtlamalar belirtebilirsiniz. Örneğin, ürün KIMLIĞINI bir olarak kısıtlamak için `int` :

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Tarafından desteklenen yol kısıtlamalarının tam listesi için Blazor bkz. [route kısıtlamaları](/aspnet/core/blazor/routing#route-constraints).

## <a name="router-component"></a>Yönlendirici bileşeni

İçindeki yönlendirme Blazor bileşen tarafından işlenir `Router` . `Router`Bileşen genellikle uygulamanın kök bileşeni (*app. Razor*) içinde kullanılır.

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

`Router`Bileşeni, belirtilen `AppAssembly` ve isteğe bağlı olarak belirtilen içindeki yönlendirilebilir bileşenleri bulur `AdditionalAssemblies` . Tarayıcı gezinirse, bir yol adresle eşleşiyorsa, bu,, ' ın, parametresini `Router` durdurur ve `Found` parametre içeriğini ayıklanmış ile işler `RouteData` , aksi takdirde `Router` `NotFound` parametresini işler.

`RouteView`Bileşen, varsa onunla belirtilen eşleşen bileşeni, `RouteData` varsa düzeniyle işlemeyi işler. Eşleşen bileşenin düzeni yoksa, isteğe bağlı olarak belirtilen `DefaultLayout` kullanılır.

`LayoutView`Bileşen, alt içeriğini belirtilen düzen içinde işler. Bu bölümün ilerleyen kısımlarında daha sonra mizanpajlara daha ayrıntılı bir şekilde bakacağız.

## <a name="navigation"></a>Gezinti

ASP.NET Web Forms ' de, tarayıcıya yeniden yönlendirme yanıtı döndürerek, gezintiyi farklı bir sayfaya tetiklersiniz. Örneğin:

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

' De yeniden yönlendirme yanıtı döndürülmesi genellikle mümkün değildir Blazor . Blazor istek-yanıt modeli kullanmaz. Ancak, JavaScript ile yaptığınız gibi tarayıcı gezginlerini doğrudan tetikleyebilirsiniz.

Blazor Şu `NavigationManager` şekilde kullanılabilecek bir hizmet sağlar:

- Geçerli tarayıcı adresini al
- Temel adresi al
- Tüm gezinmeler tetiklemeleri
- Adres değiştiğinde bildirim alın

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

Tüm üyelerin açıklaması için `NavigationManager` bkz. [URI ve gezinti durumu yardımcıları](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).

## <a name="base-urls"></a>Temel URL 'Ler

BlazorUygulamanız bir temel yol altında dağıtılmışsa, `<base>` iş için yönlendirme özelliği etiketini kullanarak sayfa meta verilerinde temel URL 'yi belirtmeniz gerekir. Uygulamanın ana bilgisayar sayfası Razor kullanılarak sunucu tarafından işlendiyse, `~/` uygulamanın temel adresini belirtmek için söz dizimini kullanabilirsiniz. Ana bilgisayar sayfası statik HTML ise, temel URL 'YI açıkça belirtmeniz gerekir.

```html
<base href="~/" />
```

## <a name="page-layout"></a>Sayfa düzeni

ASP.NET Web Forms sayfa düzeni ana sayfalar tarafından işlenir. Ana sayfalar, bir veya daha fazla içerik yer tutucusu içeren bir şablonu tanımlar ve bu, tek tek sayfalarla sağlanabilir. Ana sayfalar *. Master* dosyalarında tanımlanır ve `<%@ Master %>` yönergeyle başlar. *. Master* dosyalarının içeriği bir *. aspx* sayfası gibi kodlanır, ancak `<asp:ContentPlaceHolder>` sayfaların içerik sağlayabildiği yerleri işaretlemek için denetimler eklenir.

*Site.master*

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

' De Blazor , düzen bileşenlerini kullanarak sayfa düzeni işlemiş olursunuz. Düzen bileşenleri, `LayoutComponentBase` `Body` `RenderFragment` sayfanın içeriğini işlemek için kullanılabilen, türünde tek bir özelliği tanımlayan öğesinden devralınır.

*MainLayout. Razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

Düzen içeren sayfa işlendiğinde, sayfa, düzenin özelliğin oluşturulduğu konumdaki belirtilen düzenin içeriği içinde işlenir `Body` .

Bir sayfaya düzen uygulamak için `@layout` yönergesini kullanın:

```razor
@layout MainLayout
```

Bir klasör ve alt klasörlerdeki tüm bileşenlerin yerleşimini *_Imports. Razor* dosyası kullanarak belirtebilirsiniz. Ayrıca, [yönlendirici bileşenini](#router-component)kullanarak tüm sayfalarınızın varsayılan bir yerleşimini belirtebilirsiniz.

Ana sayfalar birden çok içerik yer tutucusu tanımlayabilir, ancak içindeki mizanpajlar Blazor yalnızca tek bir `Body` özelliğe sahiptir. Bu Blazor düzen bileşenleri sınırlaması, gelecek sürümlerde tamamen değinilmesi gerekecektir.

ASP.NET Web Forms içindeki ana sayfalar iç içe olabilir. Diğer bir deyişle, ana sayfa bir ana sayfa da kullanabilir. İçindeki düzen bileşenleri Blazor çok iç içe olabilir. Düzen bileşenine bir düzen bileşeni uygulayabilirsiniz. İç düzenin içeriği dış düzen içinde işlenir.

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

İçindeki düzenler, Blazor genellikle bir sayfa için kök HTML öğelerini tanımlamaz (,, vb `<html>` `<body>` `<head>` .). Kök HTML öğeleri, uygulamanın Blazor Ilk HTML içeriğini işlemek için kullanılan bir uygulamanın konak sayfasında tanımlanır (bkz. [ Blazor önyükleme ](project-structure.md#bootstrap-blazor)). Konak sayfası, çevreleyen biçimlendirme ile uygulama için birden çok kök bileşeni işleyebilir.

İçindeki Blazor , sayfalar dahil olmak üzere bileşenler, `<script>` etiketleri işleyebilir. Bu işleme kısıtlaması `<script>` , Etiketler bir kez yüklendiğinden ve değiştirilemediğinden oluşur. Razor söz dizimi kullanarak etiketleri dinamik olarak işlemeye çalışırsanız beklenmeyen bir davranış ortaya çıkabilir. Bunun yerine, tüm `<script>` Etiketler uygulamanın ana bilgisayar sayfasına eklenmelidir.

>[!div class="step-by-step"]
>[Önceki](components.md) 
> [Sonraki](state-management.md)
