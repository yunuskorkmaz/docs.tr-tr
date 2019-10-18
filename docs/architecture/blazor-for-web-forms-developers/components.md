---
title: Blazor ile yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturun
description: Blazor ile yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturmayı ve bunların ASP.NET Web Forms denetimleriyle nasıl karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: ab9697bcb12ec17528415b3ad4d850803f472b36
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520334"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Blazor ile yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturun

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms hakkındaki harika şeyler, yeniden kullanılabilir kullanıcı arabirimi (UI) kodunun yeniden kullanılabilir kullanıcı arabirimi denetimlerine kapsüllemesini mümkün kılar. Özel Kullanıcı denetimleri, *. ascx* dosyalarını kullanarak biçimlendirme içinde tanımlanabilir. Ayrıca, tam tasarımcı desteğiyle kodda ayrıntılı sunucu denetimleri de oluşturabilirsiniz.

Blazor, *Bileşenler*aracılığıyla UI kapsüllemeyi de destekler. Bileşen:

- , Kendinden bağımsız bir kullanıcı arabirimi öbektir.
- Kendi durumunu ve işleme mantığını korur.
- UI olay işleyicilerini tanımlayabilir, giriş verilerine bağlanabilir ve kendi yaşam döngüsünü yönetebilir.
- Genellikle Razor söz dizimi kullanarak bir *. Razor* dosyasında tanımlanır.

## <a name="an-introduction-to-razor"></a>Razor 'e giriş

Razor, HTML ve C#temel alan hafif bir işaretleme şablon dilidir. Razor sayesinde, bileşen işleme mantığınızı tanımlamak için biçimlendirme C# ve kod arasında sorunsuzca geçiş yapabilirsiniz. *. Razor* dosyası derlendiğinde, işleme mantığı .net sınıfında yapılandırılmış bir şekilde yakalanır. Derlenen sınıfın adı *. Razor* dosya adından alınır. Ad alanı, proje ve klasör yolu için varsayılan ad alanından alınır veya `@namespace` yönergesini kullanarak ad alanını açıkça belirtebilirsiniz (aşağıdaki Razor yönergelerinden daha fazlası).

Bir bileşenin işleme mantığı, kullanılarak C#dinamik mantık eklenen normal HTML işaretlemesi kullanılarak yazılır. @No__t_0 karakteri öğesine C#geçiş yapmak için kullanılır. Razor genellikle HTML 'ye geri döndüğünüzde gelime konusunda akıllı bir değer sağlar. Örneğin, aşağıdaki bileşen geçerli saat ile bir `<p>` etiketi işler:

```razor
<p>@DateTime.Now</p>
```

Bir C# ifadenin başlangıcını ve bitiyi açıkça belirtmek için parantez kullanın:

```razor
<p>@(DateTime.Now)</p>
```

Razor Ayrıca, işleme mantığınızdaki denetim C# akışını kullanmayı da kolaylaştırır. Örneğin, koşullu olarak bazı HTML 'yi şöyle işleyebilirsiniz:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Ya da aşağıdaki gibi normal C# `foreach` döngüsünü kullanarak öğelerin bir listesini oluşturabilirsiniz:

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

ASP.NET Web Forms içindeki yönergeler gibi Razor yönergeleri, Razor bileşeninin nasıl derlendiğine ilişkin birçok yönü denetler. Örneğin, bileşen şunları içerir:

- Ad Alanı
- Temel sınıf
- Uygulanan arabirimler
- Genel parametreler
- İçeri aktarılan ad alanları
- Yolların

Razor yönergeleri `@` karakteriyle başlar ve genellikle dosyanın başlangıcında yeni bir satırın başlangıcında kullanılır. Örneğin, `@namespace` yönergesi bileşenin ad alanını tanımlar:

```razor
@namespace MyComponentNamespace
```

Aşağıdaki tabloda, Blazor içinde kullanılan çeşitli Razor yönergeleri ve varsa ASP.NET Web Forms eşdeğerleri özetlenmektedir.

|Deki    |Açıklama|Örnek|Web Forms eşdeğeri|
|-------------|-----------|-------|--------------------|
|`@attribute` |Bileşene bir sınıf düzeyi özniteliği ekler|`@attribute [Authorize]`|Yok.|
|`@code`      |Bileşene sınıf üyeleri ekler|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Belirtilen arabirimi uygular|`@implements IDisposable`|Arka plan kodu kullan|
|`@inherits`  |Belirtilen taban sınıftan devralır|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Bileşene bir hizmet çıkarır|`@inject IJSRuntime JS`|Yok.|
|`@layout`    |Bileşen için bir düzen bileşeni belirtir|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Bileşen için ad alanını ayarlar|`@namespace MyNamespace`|Yok.|
|`@page`      |Bileşen için yolu belirtir|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Bileşen için genel bir tür parametresi belirtir|`@typeparam TItem`|Arka plan kodu kullan|
|`@using`     |Kapsama getirmek için bir ad alanı belirtir|`@using MyComponentNamespace`|*Web. config* 'de ad alanı Ekle|

Razor bileşenleri Ayrıca, bileşenlerin nasıl derlendiğine (olay işleme, veri bağlama, bileşen & öğe başvuruları vb.) ilişkin çeşitli yönlerini denetlemek için öğeler üzerinde *yönerge özniteliklerinin* kapsamlı bir şekilde kullanılmasını sağlar. Yönerge öznitelikleri All, parantez içindeki değerlerin isteğe bağlı olduğu ortak bir genel söz dizimini izler:

```razor
@directive(-suffix(:name))(="value")
```

Aşağıdaki tabloda, Blazor ' de kullanılan Razor yönergelerinin çeşitli öznitelikleri özetlenmektedir.

|Öznitelik    |Açıklama|Örnek|
|-------------|-----------|-------|
|`@attributes`|Özniteliklerin sözlüğünü işler|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |İki yönlü veri bağlama oluşturur    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Belirtilen olay için bir olay işleyicisi ekler|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Bir koleksiyondaki öğeleri korumak için dağıtılmış algoritma tarafından kullanılacak bir anahtar belirtir|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Bileşene veya HTML öğesine bir başvuru yakalar|`<MyDialog @ref="myDialog" />`|

Blazor (`@onclick`, `@bind`, `@ref` vb.) tarafından kullanılan çeşitli yönerge öznitelikleri aşağıdaki bölümlerde ve sonraki bölümlerde ele alınmıştır.

*. Aspx* ve *. ascx* dosyalarında kullanılan sözdizimlerinin birçoğu Razor 'de paralel sözdizimleri vardır. ASP.NET Web Forms ve Razor için sözdizimlerinin basit bir karşılaştırması aşağıda verilmiştir.

|Özellik                      |Web Forms           |Sözdizimi               |Razor         |Sözdizimi |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Yönergeler                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Kod blokları                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|İfadeler<br>(HTML kodlu)|`<%: %>`            |`<%:DateTime.Now %>` |Örtük: `@`<br>Açık: `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Açıklamalar                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Veri bağlama                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Razor bileşen sınıfına üye eklemek için `@code` yönergesini kullanın. Bu teknik, bir ASP.NET Web Forms Kullanıcı denetiminde veya sayfasında `<script runat="server">...</script>` bloğu kullanmaya benzer.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Razor temel aldığı için C#, bir C# proje ( *. csproj*) içinden derlenmesi gerekir. VB projesinden *. Razor* dosyalarını derlenemez ( *. vbproj*). Blazor projenizden VB projelerine yine de başvurabilirsiniz. Tersi de geçerlidir.

Tam Razor söz dizimi başvuru için bkz. [ASP.NET Core için Razor söz dizimi başvurusu](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Bileşenleri kullanma

Normal HTML 'den başlayarak, bileşenler kendi işleme mantığının bir parçası olarak diğer bileşenleri de kullanabilir. Razor 'de bir bileşen kullanmanın sözdizimi, bir ASP.NET Web Forms uygulamasında kullanıcı denetimi kullanmaya benzerdir. Bileşenler, bileşenin tür adıyla eşleşen bir öğe etiketi kullanılarak belirtilir. Örneğin, aşağıdakine benzer bir `Counter` bileşeni ekleyebilirsiniz:

```razor
<Counter />
```

ASP.NET Web Forms aksine, Blazor içindeki bileşenler:

- Öğe öneki kullanmayın (örneğin, `asp:`).
- Sayfada veya *Web. config*dosyasında kayıt gerekmez.

.NET türlerine benzer Razor bileşenleri düşünün çünkü bu, tam olarak bir şeydir. Bileşeni içeren derlemeye başvuruluyorsa, bileşen kullanılabilir. Bileşenin ad alanını kapsama getirmek için `@using` yönergesini uygulayın:

```razor
@using MyComponentLib

<Counter />
```

Varsayılan Blazor projelerinde görüldüğü gibi, aynı dizinde ve alt dizinlerde bulunan tüm *. Razor* dosyalarına aktarılmaları için `@using` yönergelerinin bir *_ımports. Razor* dosyasına yerleştirmesi yaygındır.

Bir bileşenin ad alanı kapsamda değilse, içinde C#olduğu gibi tam tür adını kullanarak bir bileşen belirtebilirsiniz:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Bileşen parametreleri

ASP.NET Web Forms ' de, genel özellikleri kullanarak parametreleri ve verileri denetimlere akışı sağlayabilirsiniz. Bu özellikler, öznitelikler kullanılarak biçimlendirme içinde ayarlanabilir veya doğrudan kodda ayarlanabilir. Blazor bileşenleri benzer bir biçimde çalışır, ancak bileşen özellikleri de bileşen parametreleri olarak kabul edilecek `[Parameter]` özniteliğiyle işaretlenmelidir.

Aşağıdaki `Counter` bileşeni, düğme tıklandığında `Counter` ' nin arttırılabileceğini belirtmek için kullanılabilecek `IncrementAmount` adlı bir bileşen parametresini tanımlar.

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

Blazor içinde bir bileşen parametresi belirtmek için, ASP.NET Web Forms içinde olduğu gibi bir özniteliği kullanın:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Olay işleyicileri

Hem ASP.NET Web Forms hem de Blazor Kullanıcı arabirimi olaylarını işlemek için bir olay tabanlı programlama modeli sağlar. Bu tür olaylara örnek olarak düğme tıklamaları ve metin girişi dahildir. ASP.NET Web Forms ' de, DOM tarafından sunulan UI olaylarını işlemek için HTML sunucu denetimlerini kullanırsınız veya Web sunucusu denetimleri tarafından sunulan olayları işleyebilirsiniz. Olaylar, arka arkaya geri dönüş istekleri aracılığıyla sunucuda ortaya çıkmış. Aşağıdaki Web Forms düğmesine tıklayın.

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

Blazor ' de, DOM UI olayları için işleyicileri doğrudan `@on{event}` ' ın yönerge özniteliklerini kullanarak kaydedebilirsiniz. @No__t_0 yer tutucusu, olayın adını temsil eder. Örneğin, aşağıdaki gibi düğme tıklamalarını dinleyeseçebilirsiniz:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Olay işleyicileri, olay hakkında daha fazla bilgi sağlamak için isteğe bağlı, olaya özgü bir bağımsız değişkeni kabul edebilir. Örneğin, fare olayları `MouseEventArgs` bağımsız değişkeni alabilir, ancak bu gerekli değildir.

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

Bir olay işlendikten sonra bileşen, bileşen durumu değişikliklerini hesaba göre işlenir. Zaman uyumsuz olay işleyicileriyle, bileşen işleyici yürütme tamamlandıktan hemen sonra işlenir. Bileşen, zaman uyumsuz `Task` tamamlandıktan sonra *yeniden* işlenir. Bu zaman uyumsuz yürütme modu, zaman uyumsuz `Task` devam ederken, bazı uygun Kullanıcı arabirimini işleme fırsatı sağlar.

```razor
<button @onclick="Get message">Get message</button>

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

Bileşenler, `EventCallback<TValue>` türünde bir bileşen parametresi tanımlayarak kendi olaylarını da tanımlayabilir. Olay geri çağırmaları, DOM UI olay işleyicilerinin tüm çeşitlemelerini destekler: isteğe bağlı bağımsız değişkenler, zaman uyumlu veya zaman uyumsuz, yöntem grupları veya lambda ifadeleri.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Veri bağlama

Blazor, bir UI bileşeninden bileşen durumuna veri bağlamak için basit bir mekanizma sağlar. Bu yaklaşım, veri kaynaklarından kullanıcı arabirimi denetimlerine veri bağlamak için ASP.NET Web Forms özelliklerinden farklıdır. [Verilerle ilgilenme](data.md) bölümünde farklı veri kaynaklarından veri işlemeyi ele alacağız.

Bir UI bileşeninden bileşen durumuna iki yönlü bir veri bağlama oluşturmak için `@bind` yönerge özniteliğini kullanın. Aşağıdaki örnekte, onay kutusunun değeri `isChecked` alanına bağlanır.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Bileşen işlendiğinde onay kutusunun değeri `isChecked` alanının değerine ayarlanır. Kullanıcı onay kutusuna geçiş yaparken `onchange` olayı tetiklenir ve `isChecked` alanı yeni değere ayarlanır. Bu örnekte `@bind` sözdizimi aşağıdaki biçimlendirmeye eşdeğerdir:

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

Bir veri bağlamasını temel bir kullanıcı arabirimi öğesine zincirlemek için değeri ayarlayın ve olayı `@bind` özniteliğini kullanmak yerine doğrudan UI öğesi üzerinde işleyin.

Bir bileşen parametresine bağlamak için, bağlamak istediğiniz parametreyi belirtmek üzere bir `@bind-{Parameter}` özniteliği kullanın.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Durum değişiklikleri

Bileşenin durumu normal bir kullanıcı arabirimi olayının veya olay geri çağrısının dışında değiştiyse, bileşen yeniden oluşturulması gerektiğini el ile işaret etmelidir. Bir bileşenin durumunun değiştiğini bildirmek için, bileşende `StateHasChanged` yöntemini çağırın.

Aşağıdaki örnekte, bir bileşeni, uygulamanın diğer bölümleri tarafından güncelleştirilebilen `AppState` hizmetinden bir ileti görüntüler. Bileşen, ileti her güncelleştirildiğinde bileşenin işlenmesi için `StateHasChanged` yöntemini `AppState.OnChange` olayına kaydeder.

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

## <a name="component-lifecycle"></a>Bileşen yaşam döngüsü

ASP.NET Web Forms Framework, modüller, sayfalar ve denetimler için iyi tanımlanmış yaşam döngüsü yöntemlerine sahiptir. Örneğin, aşağıdaki denetim `Init`, `Load` ve `UnLoad` yaşam döngüsü olayları için olay işleyicilerini uygular:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor bileşenlerinde de iyi tanımlanmış bir yaşam döngüsü vardır. Bileşenin yaşam döngüsü, bileşen durumunu başlatmak ve Gelişmiş bileşen davranışları uygulamak için kullanılabilir. 

Tüm Blazor bileşen yaşam döngüsü yöntemlerinin hem zaman uyumlu hem de zaman uyumsuz sürümleri vardır. Bileşen işleme zaman uyumludur. Zaman uyumsuz mantığı bileşen işlemenin bir parçası olarak çalıştıramazsınız. Tüm zaman uyumsuz mantığın bir `async` yaşam döngüsü yönteminin parçası olarak yürütülmesi gerekir.

### <a name="oninitialized"></a>OnInitialized

@No__t_0 ve `OnInitializedAsync` yöntemleri, bileşeni başlatmak için kullanılır. Bir bileşen genellikle ilk işlendikten sonra başlatılır. Bir bileşen başlatıldıktan sonra, en sonunda atılmadan önce birden çok kez oluşturulabilir. @No__t_0 yöntemi, ASP.NET Web Forms sayfaları ve denetimlerinde `Page_Load` olayına benzerdir.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

@No__t_0 ve `OnParametersSetAsync` yöntemleri, bir bileşen üst öğeden parametreleri aldığında ve değer özelliklerine atandığında çağrılır. Bu yöntemler bileşen başlatıldıktan sonra ve *bileşen her işlendiğinde*yürütülür.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

@No__t_0 ve `OnAfterRenderAsync` yöntemleri bir bileşen işlemeyi tamamladıktan sonra çağrılır. Öğe ve bileşen başvuruları bu noktada doldurulur (aşağıdaki kavramlarda daha fazla). Bu noktada tarayıcıyla etkileşim etkinleştirilir. DOM ve JavaScript yürütme etkileşimleri güvenle yapılabilir. 

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

`OnAfterRender` ve `OnAfterRenderAsync` *, sunucuda prerendering çağrıldığında çağrılmaz*.

@No__t_0 parametresi, bileşen ilk kez işlendiğinde `true`; Aksi takdirde, değeri `false`.

### <a name="idisposable"></a>IDisposable

Blazor bileşenleri, bileşen kullanıcı arabiriminden kaldırıldığında kaynakların atılmaya `IDisposable` uygulayabilir. Razor bileşeni, `@implements` yönergesini kullanarak `IDispose` uygulayabilir:

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

ASP.NET Web Forms ' de, bir denetim örneğini kendi KIMLIĞINE başvurarak doğrudan kodda işlemek yaygındır. Blazor ' de, çok daha az yaygın olsa da bir bileşeni bir başvuruyu yakalamak ve işlemek mümkündür.

Blazor içinde bir bileşen başvurusu yakalamak için `@ref` yönerge özniteliğini kullanın. Özniteliğin değeri, başvurulan bileşenle aynı türde ayarlanabilir bir alanın adıyla eşleşmelidir.

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

Blazor bileşenleri, bir öğeye başvuruları yakalayabilir. ASP.NET Web Forms içindeki HTML sunucu denetimlerinden farklı olarak, Blazor içindeki bir öğe başvurusunu kullanarak DOM 'ı doğrudan düzenleyemezsiniz. Blazor, DOM dağıtma algoritmasını kullanarak sizin için çoğu DOM etkileşimini işler. Blazor içindeki yakalanan öğe başvuruları donuk. Ancak, JavaScript birlikte çalışma çağrısında belirli bir öğe başvurusunu geçirmek için kullanılırlar. JavaScript birlikte çalışma hakkında daha fazla bilgi için bkz. [ASP.NET Core Blazor JavaScript Interop](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Şablonlu bileşenler

ASP.NET Web Forms içinde *şablonlu denetimler*oluşturabilirsiniz. Şablonlu denetimler, geliştiricinin bir kapsayıcı denetimini işlemek için kullanılan HTML 'nin bir bölümünü belirtmesini sağlar. Şablonlu sunucu denetimleri oluşturma mekanizması karmaşıktır, ancak kullanıcı tarafından özelleştirilebilir bir şekilde veri işlemeye yönelik güçlü senaryolar sağlar. Şablonlu denetimlerin örnekleri `Repeater` ve `DataList` ' i içerir. 

Blazor bileşenleri, `RenderFragment` veya `RenderFragment<T>` türündeki bileşen parametreleri tanımlayarak de şablonlanır. @No__t_0, daha sonra bileşen tarafından işlenebilen bir Razor biçimlendirme öbeğini temsil eder. @No__t_0, işleme parçası işlendiğinde belirtilebilen bir parametre alan Razor biçimlendirme öbektir.

### <a name="child-content"></a>Alt içerik

Blazor bileşenleri, alt içeriğini `RenderFragment` olarak yakalayabilir ve bu içeriği bileşen işlemenin bir parçası olarak işleyebilir. Alt içeriği yakalamak için `RenderFragment` türünde bir bileşen parametresi tanımlayın ve `ChildContent` olarak adlandırın.

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

Şablonlu bir Blazor bileşeni, `RenderFragment` veya `RenderFragment<T>` türünde birden çok bileşen parametresi de tanımlayabilir. Bir `RenderFragment<T>` parametresi çağrıldığında belirtilebilir. Bir bileşen için genel tür parametresi belirtmek üzere `@typeparam` Razor yönergesini kullanın.

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

Şablonlu bir bileşen kullanırken, şablon parametreleri parametrelerin adlarıyla eşleşen alt öğeler kullanılarak belirtilebilir. Öğe olarak geçirilen `RenderFragment<T>` türündeki bileşen bağımsız değişkenlerinin `context` adlı örtük bir parametresi vardır. Bu uygulama parametresinin adını alt öğedeki `Context` özniteliğini kullanarak değiştirebilirsiniz. Herhangi bir genel tür parametresi, tür parametresinin adıyla eşleşen bir öznitelik kullanılarak belirtilebilir. Mümkünse tür parametresi çıkarsanacaktır:

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

Bu bileşenin çıktısı şuna benzer:

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Arka plan kodu

Bir Blazor bileşeni genellikle tek bir *. Razor* dosyasında yazılır. Ancak, arka plan kod dosyası kullanarak kodu ve biçimlendirmeyi ayırmak de mümkündür. Bir bileşen dosyası kullanmak için, bileşen dosyasının C# dosya adıyla eşleşen bir dosya ekleyin *. cs* uzantısı eklenmiştir (*Counter.Razor.cs*). Bileşen için C# bir temel sınıf tanımlamak üzere dosyasını kullanın. Temel sınıfı istediğiniz şekilde adlandırın, ancak sınıfı bileşen sınıfıyla aynı ada, ancak `Base` uzantısı eklenmiş (`CounterBase`). Bileşen tabanlı sınıfın Ayrıca `ComponentBase` ' dan türetmeniz gerekir. Ardından, Razor bileşen dosyasında, bileşen için temel sınıfı belirtmek üzere `@inherits` yönergesini ekleyin (`@inherits CounterBase`).

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

Bileşen sınıfında görünür olması için, temel sınıftaki bileşen üyelerinin görünürlüğü `protected` veya `public` olmalıdır.

## <a name="additional-resources"></a>Ek kaynaklar

Yukarıdaki, Blazor bileşenlerinin tüm yönlerinin kapsamlı bir şekilde ele alınması değildir. [ASP.NET Core Razor bileşenleri oluşturma ve kullanma](/aspnet/core/blazor/components)hakkında daha fazla bilgi için Blazor belgelerine bakın.

>[!div class="step-by-step"]
>[Önceki](app-startup.md)
>[İleri](pages-routing-layouts.md)
