---
title: İle yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturun Blazor
description: İle yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturmayı Blazor ve ASP.NET Web Forms denetimleriyle nasıl karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: 4fdf062fb719e62b53e47f79db1e93d0bf079350
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267691"
---
# <a name="build-reusable-ui-components-with-no-locblazor"></a>İle yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturun Blazor

ASP.NET Web Forms hakkındaki harika şeyler, yeniden kullanılabilir kullanıcı arabirimi (UI) kodunun yeniden kullanılabilir kullanıcı arabirimi denetimlerine kapsüllemesini mümkün kılar. Özel Kullanıcı denetimleri, *. ascx* dosyalarını kullanarak biçimlendirme içinde tanımlanabilir. Ayrıca, tam tasarımcı desteğiyle kodda ayrıntılı sunucu denetimleri de oluşturabilirsiniz.

Blazor Ayrıca, *Bileşenler*aracılığıyla UI kapsüllemeyi destekler. Bileşen:

- , Kendinden bağımsız bir kullanıcı arabirimi öbektir.
- Kendi durumunu ve işleme mantığını korur.
- UI olay işleyicilerini tanımlayabilir, giriş verilerine bağlanabilir ve kendi yaşam döngüsünü yönetebilir.
- Genellikle Razor söz dizimi kullanarak bir *. Razor* dosyasında tanımlanır.

## <a name="an-introduction-to-razor"></a>Razor 'e giriş

Razor, HTML ve C# tabanlı bir hafif biçimlendirme şablon dilidir. Razor sayesinde, bileşen işleme mantığınızı tanımlamak için biçimlendirme ve C# kodu arasında sorunsuzca geçiş yapabilirsiniz. *. Razor* dosyası derlendiğinde, işleme mantığı .net sınıfında yapılandırılmış bir şekilde yakalanır. Derlenen sınıfın adı *. Razor* dosya adından alınır. Ad alanı, proje ve klasör yolu için varsayılan ad alanından alınır veya yönergesini kullanarak ad alanını açıkça belirtebilirsiniz `@namespace` (aşağıdaki Razor yönergelerinden daha fazlası).

Bir bileşenin işleme mantığı, C# kullanılarak eklenen dinamik mantık ile normal HTML işaretlemesi kullanılarak yazılır. `@`Karakter, C# ' ye geçiş yapmak için kullanılır. Razor genellikle HTML 'ye geri döndüğünüzde gelime konusunda akıllı bir değer sağlar. Örneğin, aşağıdaki bileşen `<p>` geçerli saat ile bir etiket oluşturur:

```razor
<p>@DateTime.Now</p>
```

Bir C# ifadesinin başlangıcını ve bitiyi açıkça belirtmek için parantez kullanın:

```razor
<p>@(DateTime.Now)</p>
```

Razor Ayrıca, işleme mantığınızdaki C# denetim akışını kullanmayı kolaylaştırır. Örneğin, koşullu olarak bazı HTML 'yi şöyle işleyebilirsiniz:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Ya da aşağıdaki gibi normal bir C# döngüsü kullanarak öğelerin bir listesini oluşturabilirsiniz `foreach` :

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

ASP.NET Web Forms içindeki yönergeler gibi Razor yönergeleri, Razor bileşeninin nasıl derlendiğine ilişkin birçok yönü denetler. Örneğin, bileşen şunları içerir:

- Ad Alanı
- Temel sınıf
- Uygulanan arabirimler
- Genel parametreler
- İçeri aktarılan ad alanları
- Yollar

Razor yönergeleri `@` karakteriyle başlar ve genellikle dosyanın başlangıcında yeni bir satırın başlangıcında kullanılır. Örneğin, `@namespace` yönerge bileşenin ad alanını tanımlar:

```razor
@namespace MyComponentNamespace
```

Aşağıdaki tabloda, varsa, içinde kullanılan çeşitli Razor yönergeleri Blazor ve bunların ASP.NET Web Forms eşdeğerleri özetlenmektedir.

|Deki    |Açıklama|Örnek|Web Forms eşdeğeri|
|-------------|-----------|-------|--------------------|
|`@attribute` |Bileşene bir sınıf düzeyi özniteliği ekler|`@attribute [Authorize]`|Yok|
|`@code`      |Bileşene sınıf üyeleri ekler|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Belirtilen arabirimi uygular|`@implements IDisposable`|Arka plan kodu kullan|
|`@inherits`  |Belirtilen taban sınıftan devralır|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Bileşene bir hizmet çıkarır|`@inject IJSRuntime JS`|Yok|
|`@layout`    |Bileşen için bir düzen bileşeni belirtir|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Bileşen için ad alanını ayarlar|`@namespace MyNamespace`|Yok|
|`@page`      |Bileşen için yolu belirtir|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Bileşen için genel bir tür parametresi belirtir|`@typeparam TItem`|Arka plan kodu kullan|
|`@using`     |Kapsama getirmek için bir ad alanı belirtir|`@using MyComponentNamespace`|*web.config* ad alanı Ekle|

Razor bileşenleri Ayrıca, bileşenlerin nasıl derlendiğine (olay işleme, veri bağlama, bileşen & öğe başvuruları vb.) ilişkin çeşitli yönlerini denetlemek için öğeler üzerinde *yönerge özniteliklerinin* kapsamlı bir şekilde kullanılmasını sağlar. Yönerge öznitelikleri All, parantez içindeki değerlerin isteğe bağlı olduğu ortak bir genel söz dizimini izler:

```razor
@directive(-suffix(:name))(="value")
```

Aşağıdaki tabloda, ' de kullanılan Razor yönergelerinin çeşitli öznitelikleri özetlenmektedir Blazor .

|Öznitelik    |Açıklama|Örnek|
|-------------|-----------|-------|
|`@attributes`|Özniteliklerin sözlüğünü işler|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |İki yönlü veri bağlama oluşturur    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Belirtilen olay için bir olay işleyicisi ekler|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Bir koleksiyondaki öğeleri korumak için dağıtılmış algoritma tarafından kullanılacak bir anahtar belirtir|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Bileşene veya HTML öğesine bir başvuru yakalar|`<MyDialog @ref="myDialog" />`|

(,, Vb.) tarafından kullanılan çeşitli yönerge öznitelikleri Blazor `@onclick` `@bind` `@ref` Aşağıdaki bölümlerde ve sonraki bölümlerde ele alınmıştır.

*. Aspx* ve *. ascx* dosyalarında kullanılan sözdizimlerinin birçoğu Razor 'de paralel sözdizimleri vardır. ASP.NET Web Forms ve Razor için sözdizimlerinin basit bir karşılaştırması aşağıda verilmiştir.

|Özellik                      |Web Forms           |Sözdizimi               |Razor         |Sözdizimi |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Yönergeler                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Kod blokları                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|İfadeler<br>(HTML kodlu)|`<%: %>`            |`<%:DateTime.Now %>` |İndirgen `@`<br>Anlaşılır `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Yorumlar                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Veri bağlama                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Razor bileşen sınıfına üye eklemek için `@code` yönergesini kullanın. Bu teknik, bir `<script runat="server">...</script>` ASP.NET Web Forms Kullanıcı denetiminde veya sayfasında blok kullanmaya benzer.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Razor c# temel aldığı için C# projesi (*. csproj*) içinden derlenmesi gerekir. Visual Basic projesinden *. Razor* dosyalarını derlenemez (*. vbproj*). Visual Basic projelerine yine de Blazor projenizden başvurabilirsiniz. Tersi de geçerlidir.

Tam Razor söz dizimi başvuru için bkz. [ASP.NET Core için Razor söz dizimi başvurusu](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Bileşenleri kullanma

Normal HTML 'den başlayarak, bileşenler kendi işleme mantığının bir parçası olarak diğer bileşenleri de kullanabilir. Razor 'de bir bileşen kullanmanın sözdizimi, bir ASP.NET Web Forms uygulamasında kullanıcı denetimi kullanmaya benzerdir. Bileşenler, bileşenin tür adıyla eşleşen bir öğe etiketi kullanılarak belirtilir. Örneğin, aşağıdaki gibi bir bileşen ekleyebilirsiniz `Counter` :

```razor
<Counter />
```

ASP.NET Web Forms aksine, içindeki bileşenler Blazor :

- Öğe öneki kullanmayın (örneğin, `asp:` ).
- Sayfada veya *web.config*kayıt gerekmez.

.NET türlerine benzer Razor bileşenleri düşünün çünkü bu, tam olarak bir şeydir. Bileşeni içeren derlemeye başvuruluyorsa, bileşen kullanılabilir. Bileşenin ad alanını kapsama getirmek için `@using` yönergesini uygulayın:

```razor
@using MyComponentLib

<Counter />
```

Varsayılan projelerde görüldüğü gibi Blazor , `@using` yönergeleri bir *_Imports. Razor* dosyasına koymak, böylece aynı dizindeki ve alt dizinlerdeki tüm *. Razor* dosyalarına aktarılmaları gerekir.

Bir bileşenin ad alanı kapsamda değilse, C# ' de olduğu gibi tam tür adını kullanarak bir bileşen belirtebilirsiniz:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Bileşen parametreleri

ASP.NET Web Forms ' de, genel özellikleri kullanarak parametreleri ve verileri denetimlere akışı sağlayabilirsiniz. Bu özellikler, öznitelikler kullanılarak biçimlendirme içinde ayarlanabilir veya doğrudan kodda ayarlanabilir. Blazor bileşenler benzer bir şekilde çalışır, ancak bileşen özellikleri de `[Parameter]` bileşen parametreleri olarak kabul edilecek özniteliğiyle işaretlenmelidir.

Aşağıdaki `Counter` Bileşen, `IncrementAmount` `Counter` düğmenin tıklandığı her seferinde artırılması gereken miktarı belirtmek için kullanılan adlı bir bileşen parametresini tanımlar.

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

İçinde bir bileşen parametresi belirtmek için Blazor , ASP.NET Web Forms içinde olduğu gibi bir özniteliği kullanın:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Olay işleyicileri

Her iki ASP.NET Web Forms ve Blazor Kullanıcı arabirimi olaylarını işlemek için olay tabanlı bir programlama modeli sağlar. Bu tür olaylara örnek olarak düğme tıklamaları ve metin girişi dahildir. ASP.NET Web Forms ' de, DOM tarafından sunulan UI olaylarını işlemek için HTML sunucu denetimlerini kullanırsınız veya Web sunucusu denetimleri tarafından sunulan olayları işleyebilirsiniz. Olaylar, arka arkaya geri dönüş istekleri aracılığıyla sunucuda ortaya çıkmış. Aşağıdaki Web Forms düğmesine tıklayın.

*Counter. ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

İçinde Blazor , Dom UI olayları için işleyicileri doğrudan formun yönerge özniteliklerini kullanarak kaydedebilirsiniz `@on{event}` . `{event}`Yer tutucu, olayın adını temsil eder. Örneğin, aşağıdaki gibi düğme tıklamalarını dinleyeseçebilirsiniz:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Olay işleyicileri, olay hakkında daha fazla bilgi sağlamak için isteğe bağlı, olaya özgü bir bağımsız değişkeni kabul edebilir. Örneğin, fare olayları bir `MouseEventArgs` bağımsız değişken alabilir, ancak gerekli değildir.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Bir olay işleyicisi için bir yöntem grubuna başvurmak yerine bir lambda ifadesi kullanabilirsiniz. Lambda ifadesi, diğer kapsam içi değerleri kapatmanıza olanak sağlar.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Olay işleyicileri, zaman uyumlu veya zaman uyumsuz olarak çalıştırılabilir. Örneğin, aşağıdaki `OnClick` olay işleyicisi zaman uyumsuz olarak yürütülür:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Bir olay işlendikten sonra bileşen, bileşen durumu değişikliklerini hesaba göre işlenir. Zaman uyumsuz olay işleyicileriyle, bileşen işleyici yürütme tamamlandıktan hemen sonra işlenir. Bileşen, zaman uyumsuz tamamlandıktan sonra *yeniden* işlenir `Task` . Bu zaman uyumsuz yürütme modu, zaman uyumsuz olarak devam ederken, bazı uygun Kullanıcı arabirimini işleme fırsatı sağlar `Task` .

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

Bileşenler, türünde bir bileşen parametresi tanımlayarak kendi olaylarını da tanımlayabilir `EventCallback<TValue>` . Olay geri çağırmaları, DOM UI olay işleyicilerinin tüm çeşitlemelerini destekler: isteğe bağlı bağımsız değişkenler, zaman uyumlu veya zaman uyumsuz, yöntem grupları veya lambda ifadeleri.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Veri bağlama

Blazor bir UI bileşeninden bileşen durumuna veri bağlamak için basit bir mekanizma sağlar. Bu yaklaşım, veri kaynaklarından kullanıcı arabirimi denetimlerine veri bağlamak için ASP.NET Web Forms özelliklerinden farklıdır. [Verilerle ilgilenme](data.md) bölümünde farklı veri kaynaklarından veri işlemeyi ele alacağız.

Bir UI bileşeninden bileşen durumuna iki yönlü bir veri bağlama oluşturmak için, `@bind` Directive özniteliğini kullanın. Aşağıdaki örnekte, onay kutusunun değeri `isChecked` alana bağlanır.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Bileşen işlendiğinde onay kutusunun değeri alanın değerine ayarlanır `isChecked` . Kullanıcı onay kutusuna geçiş yaparken, `onchange` olay tetiklenir ve `isChecked` alan yeni değere ayarlanır. `@bind`Bu örnekte sözdizimi aşağıdaki biçimlendirmeye eşdeğerdir:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Bağlama için kullanılan olayı değiştirmek için `@bind:event` özniteliğini kullanın.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Bileşenler, parametrelerine veri bağlamayı da destekleyebilir. Veri bağlama için, bağlanabilir parametreyle aynı ada sahip bir olay geri çağırma parametresi tanımlayın. "Değiştirilen" sonek ada eklenir.

*PasswordBox. Razor*

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

Bir veri bağlamasını temel bir kullanıcı arabirimi öğesine zincirlemek için değeri ayarlayın ve olayı, özniteliğini kullanmak yerine doğrudan UI öğesi üzerinde işleyin `@bind` .

Bir bileşen parametresine bağlamak için, `@bind-{Parameter}` bağlamak istediğiniz parametreyi belirtmek üzere bir özniteliği kullanın.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Durum değişiklikleri

Bileşenin durumu normal bir kullanıcı arabirimi olayının veya olay geri çağrısının dışında değiştiyse, bileşen yeniden oluşturulması gerektiğini el ile işaret etmelidir. Bir bileşenin durumunun değiştiğini bildirmek için, `StateHasChanged` bileşeninde yöntemi çağırın.

Aşağıdaki örnekte, bir bileşeni, `AppState` uygulamanın diğer bölümleri tarafından güncelleştirilebilen bir hizmetten bir ileti görüntüler. Bileşen, `StateHasChanged` `AppState.OnChange` ileti her güncelleştirildiğinde bileşenin işlenmesi için yöntemini olaya kaydeder.

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
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

## <a name="component-lifecycle"></a>Bileşen yaşam döngüsü

ASP.NET Web Forms Framework, modüller, sayfalar ve denetimler için iyi tanımlanmış yaşam döngüsü yöntemlerine sahiptir. Örneğin, aşağıdaki denetim `Init` ,, `Load` ve yaşam döngüsü olayları için olay işleyicilerini uygular `UnLoad` :

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor bileşenler Ayrıca iyi tanımlanmış bir yaşam döngüsüne sahiptir. Bileşenin yaşam döngüsü, bileşen durumunu başlatmak ve Gelişmiş bileşen davranışları uygulamak için kullanılabilir.

Tüm Blazor bileşen yaşam döngüsü yöntemlerinde hem zaman uyumlu hem de zaman uyumsuz sürümler vardır. Bileşen işleme zaman uyumludur. Zaman uyumsuz mantığı bileşen işlemenin bir parçası olarak çalıştıramazsınız. Tüm zaman uyumsuz mantığın bir yaşam döngüsü yönteminin parçası olarak yürütülmesi gerekir `async` .

### <a name="oninitialized"></a>OnInitialized

`OnInitialized`Ve `OnInitializedAsync` yöntemleri, bileşeni başlatmak için kullanılır. Bir bileşen genellikle ilk işlendikten sonra başlatılır. Bir bileşen başlatıldıktan sonra, en sonunda atılmadan önce birden çok kez oluşturulabilir. `OnInitialized`Yöntemi, `Page_Load` ASP.NET Web Forms sayfalarındaki ve denetimlerindeki olaya benzerdir.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

`OnParametersSet`Ve `OnParametersSetAsync` yöntemleri bir bileşen üst öğeden parametreleri aldığında ve değer özelliklerine atandığında çağrılır. Bu yöntemler bileşen başlatıldıktan sonra ve *bileşen her işlendiğinde*yürütülür.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

`OnAfterRender`Ve `OnAfterRenderAsync` yöntemleri bir bileşen işlemeyi tamamladıktan sonra çağrılır. Öğe ve bileşen başvuruları bu noktada doldurulur (aşağıdaki kavramlarda daha fazla). Bu noktada tarayıcıyla etkileşim etkinleştirilir. DOM ve JavaScript yürütme etkileşimleri güvenle yapılabilir.

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

`OnAfterRender` ve `OnAfterRenderAsync` *sunucuda prerendering çağrıldığında çağrılmaz*.

`firstRender`Parametre, `true` bileşen ilk kez işlendiğinde, aksi durumda değeri ' dir `false` .

### <a name="idisposable"></a>IDisposable

Blazor bileşenler `IDisposable` , bileşen kullanıcı arabiriminden kaldırıldığında kaynakların atılmaya uygulanabilir. Bir Razor bileşeni `IDispose` yönergesini kullanarak uygulayabilir `@implements` :

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

## <a name="capture-component-references"></a>Bileşen başvurularını yakala

ASP.NET Web Forms ' de, bir denetim örneğini kendi KIMLIĞINE başvurarak doğrudan kodda işlemek yaygındır. ' De Blazor , çok daha az ortak olsa da bir bileşeni bir başvuruyu yakalamak ve işlemek de mümkündür.

İçindeki bir bileşen başvurusunu yakalamak için Blazor , `@ref` Directive özniteliğini kullanın. Özniteliğin değeri, başvurulan bileşenle aynı türde ayarlanabilir bir alanın adıyla eşleşmelidir.

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

Üst bileşen işlendiğinde, alanı alt bileşen örneğiyle doldurulur. Daha sonra bileşen örneği üzerinde yöntemleri çağırabilir veya başka şekilde düzenleyebilirsiniz.

Bileşen başvurularını kullanarak bileşen durumunu doğrudan işlemek önerilmez. Bunun yapılması bileşenin doğru saatlerde otomatik olarak işlenmesini önler.

## <a name="capture-element-references"></a>Öğe başvurularını yakala

Blazor bileşenler, bir öğeye başvuruları yakalayabilir. ASP.NET Web Forms içindeki HTML sunucu denetimlerinden farklı olarak, ' deki bir öğe başvurusunu kullanarak DOM 'ı doğrudan düzenleyemezsiniz Blazor . Blazor , DOM dağıtma algoritmasını kullanarak sizin için çoğu DOM etkileşimini işler. ' De yakalanan öğe başvuruları Blazor donuk. Ancak, JavaScript birlikte çalışma çağrısında belirli bir öğe başvurusunu geçirmek için kullanılırlar. JavaScript birlikte çalışması hakkında daha fazla bilgi için bkz. [ Blazor javascript Interop ASP.NET Core](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Şablonlu bileşenler

ASP.NET Web Forms içinde *şablonlu denetimler*oluşturabilirsiniz. Şablonlu denetimler, geliştiricinin bir kapsayıcı denetimini işlemek için kullanılan HTML 'nin bir bölümünü belirtmesini sağlar. Şablonlu sunucu denetimleri oluşturma mekanizması karmaşıktır, ancak kullanıcı tarafından özelleştirilebilir bir şekilde veri işlemeye yönelik güçlü senaryolar sağlar. Şablonlu denetimlerin örnekleri `Repeater` ve içerir `DataList` .

Blazor bileşenler Ayrıca, veya türündeki bileşen parametreleri tanımlayarak şablonlanır `RenderFragment` `RenderFragment<T>` . Bir `RenderFragment` , daha sonra bileşen tarafından işlenebilen bir Razor biçimlendirme öbeğini temsil eder. , `RenderFragment<T>` İşleme parçası işlendiğinde belirtilebilen bir parametre alan Razor biçimlendirme öbektir.

### <a name="child-content"></a>Alt içerik

Blazor bileşenler alt içeriğini bir olarak yakalayabilir `RenderFragment` ve bu içeriği bileşen işlemenin bir parçası olarak işleyebilir. Alt içeriği yakalamak için, türü bir bileşen parametresi tanımlayın `RenderFragment` ve bu parametreyi adlandırın `ChildContent` .

*ChildContentComponent. Razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Bir üst bileşen daha sonra normal Razor söz dizimi kullanarak alt içerik sağlayabilir.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Şablon parametreleri

Şablonlu bir Blazor Bileşen, veya türünde birden çok bileşen parametresi de tanımlayabilir `RenderFragment` `RenderFragment<T>` . İçin parametresi `RenderFragment<T>` çağrıldığında belirtilebilir. Bir bileşen için genel bir tür parametresi belirtmek için `@typeparam` Razor yönergesini kullanın.

*SimpleListView. Razor*

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

Şablonlu bir bileşen kullanırken, şablon parametreleri parametrelerin adlarıyla eşleşen alt öğeler kullanılarak belirtilebilir. Öğe olarak geçirilmiş türdeki bileşen bağımsız değişkenlerinin `RenderFragment<T>` adlı örtülü bir parametresi vardır `context` . Bu uygulama parametresinin adını `Context` alt öğe üzerindeki özniteliğini kullanarak değiştirebilirsiniz. Herhangi bir genel tür parametresi, tür parametresinin adıyla eşleşen bir öznitelik kullanılarak belirtilebilir. Mümkünse tür parametresi çıkarsanacaktır:

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

Bu bileşenin çıktısı şuna benzer:

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a>Arka plan kodu

Bir Blazor bileşen genellikle tek bir *. Razor* dosyasında yazılır. Ancak, arka plan kod dosyası kullanarak kodu ve biçimlendirmeyi ayırmak de mümkündür. Bir bileşen dosyası kullanmak için, bileşen dosyasının dosya adıyla eşleşen bir C# dosyası ekleyin *. cs* uzantısı eklenmiştir (*Counter.Razor.cs*). Bileşen için bir temel sınıf tanımlamak üzere C# dosyasını kullanın. Temel sınıfı istediğiniz şekilde adlandırın, ancak sınıfı bileşen sınıfıyla aynı ada, ancak `Base` Uzantısı eklenmiş () olarak adlandırın `CounterBase` . Bileşen tabanlı sınıf de türevi olmalıdır `ComponentBase` . Ardından, Razor bileşen dosyasında, `@inherits` bileşen () için temel sınıfı belirtmek üzere yönergesini ekleyin `@inherits CounterBase` .

*Counter. Razor*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

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

Temel sınıftaki bileşen üyelerinin görünürlüğü, `protected` `public` bileşen sınıfına görünür olmalıdır.

## <a name="additional-resources"></a>Ek kaynaklar

Yukarıdaki, bileşenlerin tüm yönlerinin ayrıntılı bir şekilde ele alınması değildir Blazor . [ASP.NET Core Razor bileşenleri oluşturma ve kullanma](/aspnet/core/blazor/components)hakkında daha fazla bilgi için Blazor belgelerine bakın.

>[!div class="step-by-step"]
>[Önceki](app-startup.md) 
> [Sonraki](pages-routing-layouts.md)
