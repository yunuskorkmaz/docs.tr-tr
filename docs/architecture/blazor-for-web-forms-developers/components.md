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
# <a name="build-reusable-ui-components-with-blazor"></a>Blazor ile yeniden kullanılabilir UI bileşenleri oluşturun

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Formları hakkında güzel şeylerden biri, yeniden kullanılabilir kullanıcı arabirimi (UI) kodu parçalarının yeniden kullanılabilir kullanıcı arabirimi denetimlerine kapsüllemesini nasıl sağladığıdır. Özel kullanıcı denetimleri *.ascx* dosyaları kullanılarak biçimlendirme de tanımlanabilir. Ayrıca, tam tasarımcı desteği yle ayrıntılı sunucu denetimlerini kod halinde oluşturabilirsiniz.

Blazor ayrıca *bileşenler*aracılığıyla UI kapsüllemasını destekler. Bir bileşen:

- UI'nin kendi kendine yeten bir parçası.
- Kendi durumunu ve işleme mantığını korur.
- UI olay işleyicileri tanımlayabilir, giriş verilerine bağlanabilir ve kendi yaşam döngüsünü yönetebilir.
- Genellikle Jilet sözdizimi kullanılarak *bir .razor* dosyasında tanımlanır.

## <a name="an-introduction-to-razor"></a>Razor için bir giriş

Razor, HTML ve C#'a dayalı hafif bir biçimlendirme dilidir. Razor ile, bileşen oluşturma mantığınızı tanımlamak için biçimlendirme ve C# kodu arasında sorunsuz bir geçiş yapabilirsiniz. *.razor* dosyası derlendiğinde, işleme mantığı .NET sınıfında yapılandırılmış bir şekilde yakalanır. Derlenen sınıfın adı *.razor* dosya adından alınır. Ad alanı proje ve klasör yolu için varsayılan ad alanından alınır veya `@namespace` yönergeyi kullanarak ad alanını açıkça belirtebilirsiniz (aşağıdaki Razor yönergeleri hakkında daha fazla bilgi).

Bir bileşenin oluşturma mantığı, C# kullanılarak eklenen dinamik mantıkla normal HTML biçimlendirmesi kullanılarak yazılır. `@` Karakter C#'a geçiş için kullanılır. Razor, HTML'ye ne zaman geçtiğinizi anlama konusunda genellikle akıllıdır. Örneğin, aşağıdaki bileşen geçerli `<p>` saatle birlikte bir etiket işler:

```razor
<p>@DateTime.Now</p>
```

C# ifadesinin başlangıcını ve sonunu açıkça belirtmek için parantez leri kullanın:

```razor
<p>@(DateTime.Now)</p>
```

Razor ayrıca render mantığınızda C# kontrol akışını kullanmayı kolaylaştırır. Örneğin, bazı HTML'leri koşullu olarak şu şekilde işleyebilirsiniz:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Veya bunun gibi normal bir C# `foreach` döngüsü kullanarak öğelerin bir listesini oluşturabilirsiniz:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

ASP.NET Web Formlar'daki direktifler gibi jilet yönergeleri, Bir Razor bileşeninin nasıl derlendirilebildiğini birçok yönü denetler. Örnekler bileşenin şunlardır:

- Ad Alanı
- Taban sınıf
- Uygulanan arabirimler
- Genel parametreler
- Alınan ad alanları
- Yollar

Jilet yönergeleri `@` karakterle başlar ve genellikle dosyanın başında yeni bir satırın başında kullanılır. Örneğin, `@namespace` yönerge bileşenin ad alanını tanımlar:

```razor
@namespace MyComponentNamespace
```

Aşağıdaki tablo, Blazor'da kullanılan çeşitli Razor yönergelerini ve varsa ASP.NET Web Formları eşdeğerlerini özetleyilmiştir.

|Yönergesi    |Açıklama|Örnek|Web Formlar eşdeğeri|
|-------------|-----------|-------|--------------------|
|`@attribute` |Bileşene sınıf düzeyinde bir öznitelik ekler|`@attribute [Authorize]`|None|
|`@code`      |Bileşene sınıf üyeleri ekler|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Belirtilen arabirimi uygular|`@implements IDisposable`|Kod arkası kullanma|
|`@inherits`  |Belirtilen taban sınıftan devralmalar|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Bileşene bir hizmet enjekte eder|`@inject IJSRuntime JS`|None|
|`@layout`    |Bileşen için bir düzen bileşeni belirtir|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Bileşen için ad alanını ayarlar|`@namespace MyNamespace`|None|
|`@page`      |Bileşenin rotasını belirtir|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Bileşen için genel bir tür parametrebelirtir|`@typeparam TItem`|Kod arkası kullanma|
|`@using`     |Kapsamına getirmek için bir ad alanı belirtir|`@using MyComponentNamespace`|*web.config'de* ad alanı ekleme|

Jilet bileşenleri ayrıca, bileşenlerin nasıl derlendirilebildiğini (olay işleme, veri bağlama, bileşen & eleman başvuruları vb.) çeşitli yönlerini denetlemek için öğeler üzerindeki *yönerge özniteliklerini* de kapsamlı bir şekilde kullanır. Yönerge öznitelikleritüm parantez değerleri isteğe bağlı olduğu ortak bir genel sözdizimi izleyin:

```razor
@directive(-suffix(:name))(="value")
```

Aşağıdaki tablo, Blazor'da kullanılan Razor yönergelerinin çeşitli özelliklerini özetleyilmiştir.

|Öznitelik    |Açıklama|Örnek|
|-------------|-----------|-------|
|`@attributes`|Öznitelikler sözlüğü işler|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |İki yönlü veri bağlama oluşturur    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Belirtilen olay için bir olay işleyicisi ekler|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Bir koleksiyondaki öğeleri korumak için difüzör algoritması tarafından kullanılacak bir anahtar belirtir|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Bileşene veya HTML öğesine yapılan bir başvuruyu yakalar|`<MyDialog @ref="myDialog" />`|

Blazor tarafından kullanılan çeşitli`@onclick`direktif `@bind` `@ref`öznitelikleri ( , , , vb) aşağıdaki bölümlerde ve daha sonraki bölümlerde ele alınmıştır.

*.aspx* ve *.ascx* dosyalarında kullanılan sözdizimilerin çoğunda Razor'da paralel sözdizimi bulunur. Aşağıda web formları ve jilet ASP.NET için sözdizimleri basit bir karşılaştırma.

|Özellik                      |Web Forms           |Sözdizimi               |Razor         |Sözdizimi |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Yönergeler                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Kod blokları                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|İfadeler<br>(HTML kodlanmış)|`<%: %>`            |`<%:DateTime.Now %>` |Örtülü:`@`<br>Açık:`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Yorumlar                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Veri bağlama                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Razor bileşen sınıfına üye eklemek `@code` için yönergeyi kullanın. Bu teknik, ASP.NET `<script runat="server">...</script>` Web Forms kullanıcı denetiminde veya sayfasında bir blok kullanmaya benzer.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Razor C#'a dayandığı için, c# projesi *(.csproj)* içinden derlenmelidir. Bir Visual Basic projesinden *.razor* dosyaları *(.vbproj)* derleyebilirsiniz. Blazor projenizden Visual Basic projelerine hala başvuruyapabilirsiniz. Tam tersi de doğrudur.

Tam bir Razor sözdizimi başvurusu [için, ASP.NET Core için Razor sözdizimi başvurusuna](/aspnet/core/mvc/views/razor)bakın.

## <a name="use-components"></a>Bileşenleri kullanma

Normal HTML'nin yanı sıra, bileşenler diğer bileşenleri de görüntüleme mantığının bir parçası olarak kullanabilirler. Razor'da bir bileşeni kullanma sözdizimi, ASP.NET bir Web Forms uygulamasında kullanıcı denetimi kullanmaya benzer. Bileşenler, bileşenin tür adı ile eşleşen bir öğe etiketi kullanılarak belirtilir. Örneğin, buna benzer `Counter` bir bileşen ekleyebilirsiniz:

```razor
<Counter />
```

Web Formlar ASP.NET aksine, Blazor bileşenleri:

- Öğe öneki kullanmayın (örneğin, `asp:`).
- Sayfada veya *web.config'de*kayıt gerektirmeyin.

.NET türleri gibi Razor bileşenleri düşünün, çünkü tam olarak ne oldukları. Bileşeni içeren derleme başvurulmuşsa, bileşen kullanılabilir. Bileşenin ad alanını kapsamına getirmek için `@using` yönergeyi uygulayın:

```razor
@using MyComponentLib

<Counter />
```

Varsayılan Blazor projelerinde görüldüğü gibi, direktifleri `@using` *_Imports.jilet* dosyasına koymak yaygındır, böylece aynı dizindeki ve çocuk dizindeki tüm *.razor* dosyalarına aktarılırlar.

Bir bileşenin ad alanı kapsamiçinde değilse, c#'da olduğu gibi, tam tür adını kullanarak bir bileşen belirtebilirsiniz:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Bileşen parametreleri

web formlarını ASP.NET, genel özellikleri kullanarak denetimlere parametreler ve veriler aktarabilirsiniz. Bu özellikler öznitelikleri kullanılarak biçimlendirme olarak ayarlanabilir veya doğrudan kod olarak ayarlanabilir. Blazor bileşenleri de benzer bir şekilde çalışır, ancak bileşen `[Parameter]` özellikleri de bileşen parametreleri olarak kabul edilecek öznitelik ile işaretlenmiş olmalıdır.

Aşağıdaki `Counter` bileşen, düğme her tıklatıldığında artış `IncrementAmount` `Counter` yapılması gereken miktarı belirtmek için kullanılabilecek bir bileşen parametresi tanımlar.

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

Blazor'da bir bileşen parametresi belirtmek için, web formlarında olduğu gibi bir öznitelik ASP.NET kullanın:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Olay işleyicileri

Hem ASP.NET Web Formları hem de Blazor, Web-oi olaylarını işlemek için olay tabanlı bir programlama modeli sağlar. Bu tür olaylara örnek olarak düğme tıklamaları ve metin girişi verilebilir. Web Formları ASP.NET, DOM tarafından açığa çıkarılan Web Telefonu etkinliklerini işlemek için HTML sunucu denetimlerini kullanırsınız veya web sunucusu denetimleri tarafından açığa çıkarılan olayları işleyebilirsiniz. Olaylar, form post-back istekleri aracılığıyla sunucuda su yüzüne çıkar. Aşağıdaki Web Formları düğmesine tıklama örneğini göz önünde bulundurun:

*Counter.ascx*

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

Blazor'da, doğrudan formun `@on{event}`yönerge özniteliklerini kullanarak DOM Web Gücü olayları için işleyicileri kaydedebilirsiniz. `{event}` Yer tutucu, olayın adını temsil eder. Örneğin, şu gibi düğme tıklamalarını dinleyebilirsiniz:

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

Olay işleyicisi için bir yöntem grubuna atıfta bulunarak yerine lambda ifadesini kullanabilirsiniz. Lambda ifadesi, diğer kapsam içi değerleri kapatmanızı sağlar.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Olay işleyicileri eşzamanlı veya eşzamanlı olarak yürütebilir. Örneğin, aşağıdaki `OnClick` olay işleyicisi eşeşitleme yürütülür:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Bir olay işlendikten sonra, bileşen tüm bileşen durumu değişikliklerini hesaba katmak üzere işlenir. Eşsenkronize olay işleyicileri ile, bileşen işleyici yürütme tamamlandıktan hemen sonra işlenir. Bileşen, eşzamanlı `Task` tamamlandıktan sonra *yeniden* işlenir. Bu eşzamanlı yürütme modu, asenkron `Task` hala devam ederken bazı uygun Kullanıcı Arabirimi işlemek için bir fırsat sağlar.

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

Bileşenler, bir `EventCallback<TValue>`bileşen parametresi tanımlayarak kendi olaylarını da tanımlayabilir. Olay geri aramaları DOM Kullanıcı Arabirimi olay işleyicilerinin tüm varyasyonlarını destekler: isteğe bağlı bağımsız değişkenler, senkron veya eşzamanlı, yöntem grupları veya lambda ifadeleri.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Veri bağlama

Blazor, kullanıcı bir kullanıcı bir kullanıcı bir kullanıcı tarafından bileşenin durumuna verileri bağlamak için basit bir mekanizma sağlar. Bu yaklaşım, veri kaynaklarından UI denetimlerine veri bağlamak için ASP.NET Web Formları'ndaki özelliklerden farklıdır. [Verilerle Başa Çıkma](data.md) bölümünde farklı veri kaynaklarından gelen verileri işlemeyi ele alacağız.

UI bileşeninden bileşenin durumuna iki yönlü veri bağlama oluşturmak için `@bind` yönerge özniteliğini kullanın. Aşağıdaki örnekte, onay kutusunun değeri `isChecked` alana bağlıdır.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Bileşen işlendiğinde, onay kutusunun değeri `isChecked` alanın değerine ayarlanır. Kullanıcı onay kutusunu attığında, `onchange` olay ateşlenir ve `isChecked` alan yeni değere ayarlanır. Bu `@bind` durumda sözdizimi aşağıdaki biçimlendirmeye eşdeğerdir:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Bağlama için kullanılan olayı değiştirmek için `@bind:event` özniteliği kullanın.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Bileşenler, parametrelerine veri bağlamayı da destekleyebilir. Veri bağlama için, bağlanabilir parametreyle aynı ada sahip bir olay geri arama parametresi tanımla. Ada "Değiştirildi" soneki eklenir.

*PasswordBox.razor*

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

Bir veriyi temel deki bir UI öğesine bağlamak için, değeri ayarlayın ve olayı `@bind` özniteliği kullanmak yerine doğrudan UI öğesiüzerinde işleyebilir.

Bileşen parametresine bağlamak için, `@bind-{Parameter}` bağlamak istediğiniz parametreyi belirtmek için bir öznitelik kullanın.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Durum değişiklikleri

Bileşenin durumu normal bir Ara-Görüntü olayı veya olay geri araması dışında değiştiyse, bileşenin yeniden işlenmesi gerektiğini el ile işaret etmesi gerekir. Bir bileşenin durumunun değiştiğini bildirmek için `StateHasChanged` bileşendeki yöntemi arayın.

Aşağıdaki örnekte, bileşen, uygulamanın `AppState` diğer bölümleri tarafından güncelleştirilebilen bir hizmetten gelen bir iletiyi görüntüler. Bileşen, `StateHasChanged` ileti güncelleştirildiğinde `AppState.OnChange` bileşenin işlenmesi için yöntemini olaya kaydeder.

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

ASP.NET Web Forms çerçevesi, modüller, sayfalar ve denetimler için iyi tanımlanmış yaşam döngüsü yöntemlerine sahiptir. Örneğin, aşağıdaki denetim `Init`, , `Load`ve `UnLoad` yaşam döngüsü olaylar için olay işleyicileri uygular:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor bileşenleri de iyi tanımlanmış bir yaşam döngüsüne sahiptir. Bileşenin yaşam döngüsü, bileşen durumunu başlatmave gelişmiş bileşen davranışlarını uygulamak için kullanılabilir.

Blazor'un tüm bileşen yaşam döngüsü yöntemlerinin hem senkron hem de eşzamanlı versiyonları vardır. Bileşen oluşturma eşzamanlıdır. Bileşen oluşturmanın bir parçası olarak eşzamanlı mantığı çalıştıramazsınız. Tüm eşzamanlı mantık bir yaşam döngüsü `async` yönteminin bir parçası olarak yürütülmelidir.

### <a name="oninitialized"></a>OnInitialized

Ve `OnInitialized` `OnInitializedAsync` yöntemler bileşeni başlatmaiçin kullanılır. Bir bileşen genellikle ilk işlendikten sonra başharfe getirilir. Bir bileşen para başlatılan sonra, sonunda elden önce birden çok kez işlenebilir. Yöntem, `OnInitialized` web formları `Page_Load` sayfalarında ve denetimlerine ASP.NET olayla benzer.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnparametersSet

Ve `OnParametersSet` `OnParametersSetAsync` yöntemleri bir bileşenin üst parametre aldı ve değer özelliklerine atanır denir. Bu yöntemler bileşen başlatmadan sonra yürütülür ve *bileşen her işlendi.*

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Ve `OnAfterRender` `OnAfterRenderAsync` yöntemler, bir bileşen işleme yi bitirdikten sonra çağrılır. Öğe ve bileşen başvuruları bu noktada doldurulur (aşağıdaki kavramlar hakkında daha fazla bilgi). Bu noktada tarayıcıile etkileşim etkindir. DOM ve JavaScript yürütme ile etkileşimler güvenle gerçekleşebilir.

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

`OnAfterRender`ve `OnAfterRenderAsync` *sunucuda önişleme çağrılırken çağrılmaz.*

`firstRender` Parametre, `true` bileşenin ilk işlenme zamanıdır; aksi takdirde, `false`değeri .

### <a name="idisposable"></a>ıdisposable

Blazor bileşenleri, `IDisposable` bileşen UI'den kaldırıldığında kaynakları elden çıkarmak için uygulayabilir. Bir Razor bileşeni `IDispose` yönergeyi `@implements` kullanarak uygulayabilir:

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

## <a name="capture-component-references"></a>Bileşen başvurularını yakalama

ASP.NET Web Formlarında, bir denetim örneğini kimliğine atıfta bulunarak doğrudan kod olarak işlemek yaygındır. Blazor'da, çok daha az yaygın olmasına rağmen, bir bileşene yapılan bir başvuruyup manipüle etmek de mümkündür.

Blazor'da bir bileşen başvurusu `@ref` yakalamak için yönerge özniteliğini kullanın. Öznitelik değeri, başvurulan bileşenle aynı türde bir ayaralanının adı yla eşleşmelidir.

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

Üst bileşen işlendiğinde, alan alt bileşen örneğiyle doldurulur. Daha sonra yöntem üzerinde arama veya başka bir şekilde, bileşen örneği işlemek.

Bileşen başvurularını kullanarak bileşen durumunu doğrudan manipüle etmek önerilmez. Bunu yapmak, bileşenin doğru zamanlarda otomatik olarak işlenmesini engeller.

## <a name="capture-element-references"></a>Eleman başvurularını yakalama

Blazor bileşenleri bir öğeye yapılan başvuruları yakalayabilir. ASP.NET Web Formlar'daki HTML sunucu denetimlerinden farklı olarak, Blazor'daki bir öğe referansını kullanarak DOM'u doğrudan manipüle edemezsiniz. Blazor, DOM difüzyon algoritmasını kullanarak sizin için en ÇOK DOM etkileşimini yönetir. Blazor'da yakalanan eleman başvuruları opak. Ancak, bir JavaScript interop aramasında belirli bir öğe başvurusu geçmek için kullanılırlar. JavaScript interop hakkında daha fazla bilgi için Core [Blazor JavaScript interop ASP.NET](/aspnet/core/blazor/javascript-interop)bakın.

## <a name="templated-components"></a>Şablonlu bileşenler

Web Formları ASP.NET *şablonlanmış denetimler*oluşturabilirsiniz. Şablondenetimler, geliştiricinin kapsayıcı denetimini işlemek için kullanılan HTML'nin bir bölümünü belirtmesini sağlar. Şablonlanmış sunucu denetimleri oluşturma mekaniği karmaşıktır, ancak verileri kullanıcıtarafından özelleştirilebilir bir şekilde işlemek için güçlü senaryolar sağlar. Şablonlanmış denetimörnekleri `Repeater` şunlardır ve `DataList`.

Blazor bileşenleri de tip `RenderFragment` veya `RenderFragment<T>`bileşen parametreleri tanımlayarak şablonolabilir. A, `RenderFragment` daha sonra bileşen tarafından oluşturulabilen bir jilet biçimlendirme yığınını temsil eder. A, `RenderFragment<T>` render parçası işlendiğinde belirtilebilen bir parametre alan bir Jilet biçimlendirmesi yığınıdır.

### <a name="child-content"></a>Alt içerik

Blazor bileşenleri alt içeriklerini `RenderFragment` bir olarak yakalayabilir ve bu içeriği bileşen oluşturmanın bir parçası olarak işleyebilir. Alt içeriği yakalamak için, bir `RenderFragment` bileşen parametresi yazın ve adını belirleyin. `ChildContent`

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Bir üst bileşen daha sonra normal Razor sözdizimini kullanarak alt içerik sağlayabilir.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Şablon parametreleri

Şablonlanmış bir Blazor bileşeni de tür `RenderFragment` veya `RenderFragment<T>`birden çok bileşen parametreleri tanımlayabilir. Bir `RenderFragment<T>` parametre çağrıldığı zaman belirtilebilir. Bir bileşen için genel bir tür parametresi belirtmek için Razor yönergesini `@typeparam` kullanın.

*SimpleListView.razor*

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

Şablonlu bir bileşen kullanırken, şablon parametreleri parametrelerin adlarıyla eşleşen alt öğeler kullanılarak belirtilebilir. Öğeler olarak `RenderFragment<T>` geçirilen tür bileşen bağımsız değişkenleri, örtülü bir parametreye sahiptir. `context` Alt öğedeki özniteliği kullanarak `Context` bu uygulama parametresinin adını değiştirebilirsiniz. Herhangi bir genel tür parametreleri, tür parametresinin adıyla eşleşen bir öznitelik kullanılarak belirtilebilir. Tür parametresi mümkünse çıkarılacaktır:

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

Bu bileşenin çıktısı aşağıdaki gibi görünür:

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Kod arkası

Blazor bileşeni genellikle tek bir *.razor* dosyasında yazar. Ancak, kod ve biçimlendirmeyi kod arkası dosyasını kullanarak ayırmak da mümkündür. Bileşen dosyasını kullanmak için, bileşen dosyasının dosya adıyla eşleşen ancak *.cs* uzantısı eklenmiştir *(Counter.razor.cs)* içeren bir C# dosyası ekleyin. Bileşen için bir taban sınıf tanımlamak için C# dosyasını kullanın. Taban sınıfa istediğiniz her şeyi adlandırabilirsiniz, ancak sınıfın bileşen sınıfıyla aynı ada ad `Base` vermek yaygındır, ancak bir uzantı eklenmirken (`CounterBase`). Bileşen tabanlı sınıf da. `ComponentBase` Daha sonra, Razor bileşen dosyasında, bileşeniçin taban sınıf`@inherits CounterBase`( belirtmek için `@inherits` yönerge ekleyin.

*Counter.razor*

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

Bileşenin alt sınıftaki üyelerinin görünürlüğü bileşen `protected` sınıfı `public` tarafından görülebilmeli veya görünür olmalıdır.

## <a name="additional-resources"></a>Ek kaynaklar

Önceki Blazor bileşenlerinin tüm yönleriyle ayrıntılı bir tedavi değildir. Core Razor bileşenlerinin nasıl [oluşturulup ASP.NET kullanılacağı](/aspnet/core/blazor/components)hakkında daha fazla bilgi için Blazor belgelerine bakın.

>[!div class="step-by-step"]
>[Önceki](app-startup.md)
>[Sonraki](pages-routing-layouts.md)
