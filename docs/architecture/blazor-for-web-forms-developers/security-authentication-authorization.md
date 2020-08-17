---
title: 'Güvenlik: ASP.NET Web Forms ve üzerinde kimlik doğrulaması ve yetkilendirme Blazor'
description: ASP.NET Web Forms ve ' de kimlik doğrulama ve yetkilendirmeyi nasıl işleyeceğinizi öğrenin Blazor .
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 1cc82b14a940465c26377f9181a2e20b46b0783f
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267868"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a>Güvenlik: ASP.NET Web Forms ve üzerinde kimlik doğrulaması ve yetkilendirme Blazor

Bir ASP.NET Web Forms uygulamasından ' ye geçiş yapmak Blazor , uygulamanın kimlik doğrulaması ile yapılandırıldığını varsayarak kimlik doğrulamanın ve yetkilendirmenin nasıl gerçekleştirileceğini neredeyse tamamen gerektirir. Bu bölümde, ASP.NET Web Forms evrensel sağlayıcı modelinden (üyelik, roller ve Kullanıcı profilleri için) ve uygulamalardan ASP.NET Core kimlik ile nasıl çalışabileceğiniz ele alınacaktır Blazor . Bu bölümde üst düzey adımlar ve önemli noktalar ele alınırken, ayrıntılı adımlar ve betikler başvurulan belgelerde bulunabilir.

## <a name="aspnet-universal-providers"></a>ASP.NET evrensel sağlayıcılar

ASP.NET 2,0 ' den itibaren, ASP.NET Web Forms platformu üyelik dahil olmak üzere çeşitli özellikler için bir sağlayıcı modeli destekliyordu. Evrensel üyelik sağlayıcısı, isteğe bağlı rol sağlayıcısıyla birlikte ASP.NET Web Forms uygulamalarıyla çok yaygın olarak dağıtılır. Bugün çalışmaya devam eden kimlik doğrulama ve yetkilendirmeyi yönetmenin sağlam ve güvenli bir yolunu sunar. Bu evrensel sağlayıcıların en son sunumu, [Microsoft. Aspnet. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers)bir NuGet paketi olarak sunulmaktadır.

Evrensel sağlayıcılar,, ve gibi tabloları içeren bir SQL veritabanı şeması ile `aspnet_Applications` çalışır `aspnet_Membership` `aspnet_Roles` `aspnet_Users` . [aspnet_regsql.exe komutu](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140))çalıştırılarak yapılandırıldığında, sağlayıcılar, temel alınan verilerle çalışmak için gerekli tüm sorguları ve komutları sağlayan tabloları ve saklı yordamları yükler. Veritabanı şeması ve bu saklı yordamlar, daha yeni ASP.NET Identity ve ASP.NET Core kimlik sistemleriyle uyumlu değildir, bu nedenle mevcut verilerin yeni sisteme geçirilmesi gerekir. Şekil 1 ' de, evrensel sağlayıcılar için yapılandırılmış örnek bir tablo şeması gösterilmektedir.

![Evrensel sağlayıcılar şeması](./media/security/membership-tables.png)

Evrensel sağlayıcı kullanıcıları, üyeliği, rolleri ve profilleri işler. Kullanıcılara genel benzersiz tanımlayıcılar atanır ve çok temel bilgiler (Kullanıcı kimliği, Kullanıcı adı) `aspnet_Users` tabloda depolanır. Parola, parola biçimi, parola güvenlik, kilitleme sayaçları ve ayrıntılar gibi kimlik doğrulama bilgileri `aspnet_Membership` tabloda depolanır. Roller, yalnızca ilişkilendirme tablosu aracılığıyla kullanıcılara atanan adları ve benzersiz tanımlayıcılardan oluşur ve `aspnet_UsersInRoles` çoktan çoğa bir ilişki sağlar.

Mevcut sisteminiz üyeliğe ek olarak roller kullanıyorsa, Kullanıcı hesaplarını, ilişkili parolaları, rolleri ve rol üyeliğini ASP.NET Core kimliğe geçirmeniz gerekir. Ayrıca, şu anda, ' nin bildirim temelli filtrelerin, özniteliklerin ve/veya etiket yardımcılarını kullanmasını sağlamak için If deyimlerini kullanarak şu anda rol denetimleri gerçekleştirmekte olduğunuz kodunuzu güncelleştirmeniz gerekir. Bu bölümün sonunda, geçiş konularını daha ayrıntılı olarak gözden geçitireceğiz.

### <a name="authorization-configuration-in-web-forms"></a>Web Forms 'de yetkilendirme yapılandırması

Bir ASP.NET Web Forms uygulamasındaki belirli sayfalara yetkili erişimi yapılandırmak için, genellikle belirli sayfaların veya klasörlerin anonim kullanıcılara erişilmez olduğunu belirtirsiniz. Bu, web.config dosyasında yapılır:

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

`authentication`Yapılandırma bölümü, uygulama için form kimlik doğrulamasını ayarlar. Bu `authorization` bölüm, tüm uygulama için anonim kullanıcılara izin vermek için kullanılır. Ancak, bir konum temelinde daha ayrıntılı yetkilendirme kuralları sağlayabilir ve rol tabanlı yetkilendirme denetimleri uygulayabilirsiniz.

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

Yukarıdaki yapılandırma, ilki ile birleştirildiğinde, anonim kullanıcıların oturum açma sayfasına erişmesine izin verir ve bu, kimliği doğrulanmamış kullanıcılar için site genelinde kısıtlamayı geçersiz kılar.

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

Yukarıdaki yapılandırma, diğerleri ile birleştirildiğinde, `/admin` klasöre ve içindeki tüm kaynaklara erişimi "Administrators" rolünün üyeleriyle kısıtlar. Bu `web.config` , klasör köküne ayrı bir dosya yerleştirerek da uygulanabilir `/admin` .

### <a name="authorization-code-in-web-forms"></a>Web Forms 'de yetkilendirme kodu

' Yi kullanarak erişimi yapılandırmanın yanı sıra `web.config` , Web Forms uygulamanızda erişimi ve davranışı programlı bir şekilde de yapılandırabilirsiniz. Örneğin, belirli işlemleri gerçekleştirme veya kullanıcının rolüne bağlı olarak belirli verileri görüntüleme özelliğini kısıtlayabilirsiniz.

Bu kod hem codebehind mantığındaki hem de sayfanın kendisi için kullanılabilir:

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

Kullanıcı rolü üyeliğini denetlemeye ek olarak, kimlik doğrulamasının yapılıp yapılmadığını da belirleyebilirsiniz (genellikle bu, yukarıda bahsedilen konum tabanlı yapılandırma kullanılarak daha iyi yapılır). Aşağıda bu yaklaşımın bir örneği verilmiştir.

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

Yukarıdaki kodda rol tabanlı erişim denetimi (RBAC), sayfanın belirli öğelerinin (örneğin `SecretPanel` ,) geçerli kullanıcının rolüne göre görünür olup olmadığını belirlemekte kullanılır.

Genellikle, ASP.NET Web Forms uygulamalar dosya içinde güvenliği yapılandırır `web.config` ve ardından `.aspx` sayfalarda ve ilgili codebehind dosyalarında gereken yere ek denetimler ekler `.aspx.cs` . Çoğu uygulama, genellikle ek rol sağlayıcısıyla birlikte evrensel üyelik sağlayıcısından faydalanır.

## <a name="aspnet-core-identity"></a>ASP.NET Core kimliği

Kimlik doğrulama ve yetkilendirme ile hala çalışmaya devam etse de ASP.NET Core kimliği, evrensel sağlayıcılardan karşılaştırıldığında farklı bir soyutlama ve varsayımlar kümesi kullanır. Örneğin, yeni kimlik modeli üçüncü taraf kimlik doğrulamasını destekler, böylece kullanıcılar sosyal medya hesabı veya diğer güvenilir kimlik doğrulama sağlayıcısı kullanarak kimlik doğrulaması yapabilir. ASP.NET Core kimlik, oturum açma, oturum kapatma ve kayıt gibi yaygın olarak gereken sayfaların Kullanıcı arabirimini destekler. Veri erişimi için EF Core yararlanır ve veri modelini desteklemek için gereken gerekli şemayı oluşturmak üzere EF Core geçişleri kullanır. Bu [ASP.NET Core kimliğe giriş](https://docs.microsoft.com/aspnet/core/security/authentication/identity) , ASP.NET Core kimliği ile nelerin dahil olduğu ve onunla çalışmaya başlama hakkında iyi bir genel bakış sunar. Uygulamanızda ve veritabanında ASP.NET Core kimlik ayarlamadıysanız, başlamanıza yardımcı olur.

### <a name="roles-claims-and-policies"></a>Roller, talepler ve ilkeler

Hem Evrensel sağlayıcılar hem de ASP.NET Core kimlik, rol kavramını destekler. Kullanıcılar için roller oluşturabilir ve kullanıcılara roller atayabilirsiniz. Kullanıcılar herhangi bir sayıda role ait olabilir ve yetkilendirme uygulamanızın bir parçası olarak rol üyeliğini doğrulayabilirsiniz.

Rollere ek olarak, ASP.NET Core kimlik, talepler ve ilkelerin kavramlarını destekler. Bir rol özellikle bu roldeki bir kullanıcının erişim sağlayabilmesi gereken bir kaynak kümesine karşılık gelmelidir, bir talep yalnızca kullanıcının kimliğinin bir parçasıdır. Talep, konunun ne yapabileceğini temsil eden bir ad değer çiftidir.

Bir kullanıcının taleplerini doğrudan incelemek ve bir kullanıcıya bir kaynağa erişim verilmesi gerekip gerekmediğini temel alarak bunları belirleme olanağınız vardır. Ancak, bu tür denetimler genellikle sistem genelinde tekrarlanır ve dağılmış olur. Bir *ilke*tanımlamak daha iyi bir yaklaşımdır.

Yetkilendirme ilkesi bir veya daha fazla gereksinimden oluşur. İlkeler, yetkilendirme hizmeti yapılandırmasının bir parçası olarak ' `ConfigureServices` ın yönteminde kaydedilir `Startup.cs` . Örneğin, aşağıdaki kod parçacığı, "CanadiansOnly" adlı bir ilke yapılandırır ve bu, kullanıcının "Kanada" değeriyle ülke talebine sahip olması gereksinimini içerir.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

[Belgelerde özel ilkeler oluşturma hakkında daha fazla bilgi](https://docs.microsoft.com/aspnet/core/security/authorization/policies)edinebilirsiniz.

İlkeleri veya rolleri kullanıp kullansanız, uygulamanızdaki belirli bir sayfanın Blazor Bu rolü veya ilkeyi, `[Authorize]` yönergeyle birlikte uygulanmış özniteliğiyle kullanmasını sağlayabilirsiniz `@attribute` .

Rol gerektirme:

```csharp
@attribute [Authorize(Roles ="administrators")]
```

Bir ilkenin karşılanmasını gerektirme:

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

Kodunuzun kodunuzda bir kullanıcının kimlik doğrulama durumuna, rolüne veya taleplerine erişmeniz gerekiyorsa, bunu gerçekleştirmenin iki temel yolu vardır. Birincisi, kimlik doğrulama durumunu basamaklı bir parametre olarak almadır. İkincisi, eklenen ' i kullanarak duruma erişdir `AuthenticationStateProvider` . Bu yaklaşımların her birinin ayrıntıları [ Blazor güvenlik belgelerinde](https://docs.microsoft.com/aspnet/core/blazor/security/)açıklanmıştır.

Aşağıdaki kod, nasıl `AuthenticationState` bir geçişli parametre olarak alınacağını gösterir:

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

Bu parametre yerine, kullanıcıyı şu kodu kullanarak edinebilirsiniz:

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

Aşağıdaki kod, aşağıdakilerin nasıl ekleneceğini göstermektedir `AuthenticationStateProvider` :

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

Sağlayıcı ile, aşağıdaki kodla kullanıcıya erişim sağlayabilirsiniz:

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**Note:** `AuthorizeView` Bu bölümün ilerleyen kısımlarında yer alan bileşen, kullanıcının bir sayfada veya bileşende ne göreceğini denetlemek için bildirim temelli bir yol sağlar.

Kullanıcılar ve talepler (sunucu uygulamalarında) ile çalışmak için, bir Blazor `UserManager<T>` `IdentityUser` kullanıcının taleplerini numaralandırmak ve değiştirmek üzere kullanabileceğiniz bir (varsayılan için kullanın) eklemeniz gerekebilir. Önce türü ekleme ve bir özelliğe atama:

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

Daha sonra kullanıcının taleplerine göre çalışmak için bu uygulamayı kullanın. Aşağıdaki örnek, bir kullanıcıya bir talebin nasıl ekleneceğini ve kalıcı hale alınacağını gösterir:

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

Rollerle çalışmanız gerekiyorsa, aynı yaklaşımı izleyin. `RoleManager<T>` `IdentityRole` Rolleri listelemek ve yönetmek için bir (varsayılan tür için kullanın) eklemeniz gerekebilir.

**Note:** Blazor Webassembly projelerinde, bu işlemleri gerçekleştirmek için sunucu API 'leri sağlamanız gerekir ( `UserManager<T>` veya doğrudan kullanmak yerine `RoleManager<T>` ). BlazorWebassembly istemci uygulaması, bu amaçla sunulan API uç noktalarını güvenli bir şekilde çağırarak talepleri ve/veya rolleri yönetebilir.

### <a name="migration-guide"></a>Geçiş kılavuzu

ASP.NET Web Forms ve evrensel sağlayıcılardan ASP.NET Core kimliğe geçiş için birkaç adım gerekir:

1. Hedef veritabanında ASP.NET Core Identity Database şeması oluştur
2. Verileri evrensel sağlayıcı şemasından ASP.NET Core Identity şemasına geçirme
3. web.config yapılandırmasını ara yazılım ve hizmetlere geçirme (genellikle `Startup.cs`
4. Etiket Yardımcıları ve yeni kimlik API 'Lerini kullanmak için denetimleri ve koşulları kullanarak sayfaları tek tek güncelleştirin.

Bu adımların her biri, aşağıdaki bölümlerde ayrıntılı olarak açıklanmıştır.

### <a name="creating-the-aspnet-core-identity-schema"></a>ASP.NET Core Identity şeması oluşturma

ASP.NET Core kimliği için kullanılan gerekli tablo yapısını oluşturmanın birkaç yolu vardır. En basit, yeni bir ASP.NET Core Web uygulaması oluşturmaktır. Web uygulaması ' nı seçin ve kimlik doğrulamasını bireysel kullanıcı hesapları kullanacak şekilde değiştirin.

![bireysel kullanıcı hesaplarıyla Yeni proje](./media/security/individual-user-accounts.png)

Komut satırından, komutunu çalıştırarak aynı şeyi yapabilirsiniz `dotnet new webapp -au Individual` . Uygulama oluşturulduktan sonra çalıştırın ve siteye kaydolun. Bir sayfayı aşağıda gösterildiği gibi tetiklemeniz gerekir:

![geçişleri uygula sayfası](./media/security/apply-migrations-page.png)

"Geçişleri Uygula" düğmesine tıklayın ve gerekli veritabanı tablolarının sizin için oluşturulması gerekir. Ayrıca, geçiş dosyaları projenizde gösterildiği gibi görünmelidir:

![geçiş dosyaları](./media/security/migration-files.png)

Bu komut satırı aracını kullanarak, Web uygulamasını çalıştırmadan geçişi kendiniz çalıştırabilirsiniz:

```powershell
dotnet ef database update
```

Yeni şemayı mevcut bir veritabanına uygulamak için bir komut dosyası çalıştırırsanız, komut satırından bu geçişlere komut dosyası ekleyebilirsiniz. Betiği oluşturmak için şu komutu çalıştırın:

```powershell
dotnet ef migrations script -o auth.sql
```

Bu işlem, çıkış dosyasında `auth.sql` istediğiniz herhangi bir veritabanına göre çalıştırılabilecek BIR SQL betiği oluşturur. Komutları çalıştırırken sorun yaşarsanız `dotnet ef` [sisteminizde EF Core araçlarının yüklü olduğundan emin olun](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).

Kaynak tablolarınızda ek sütunlarınız varsa, bu sütunlar için yeni şemada en iyi konumu belirlemeniz gerekir. Genellikle tabloda bulunan sütunların `aspnet_Membership` tabloya eşlenmesi gerekir `AspNetUsers` . Üzerindeki sütunlar `aspnet_Roles` ile eşlenmelidir `AspNetRoles` . Tablodaki ek sütunlar `aspnet_UsersInRoles` `AspNetUserRoles` tabloya eklenir.

Ayrıca, bazı ek sütunları ayrı tablolara yerleştirmeyi de göz önünde bulundurarak, gelecekteki geçişlerin varsayılan kimlik şemasının özelleştirmeleri göz önüne almanız gerekmez.

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>Verileri evrensel sağlayıcılardan ASP.NET Core kimliğe geçirme

Hedef tablo şemasını oluşturduktan sonra, bir sonraki adım, Kullanıcı ve rol kayıtlarınızı yeni şemaya geçirmadır. Hangi sütunların yeni sütunlara eşlenebileceği de dahil olmak üzere, şema farklarının kapsamlı bir listesi [burada](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)bulunabilir.

Kullanıcılarınıza yeni kimlik tablolarına geçiş yapmak için [belgelerde açıklanan adımları izlemeniz](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)gerekir. Bu adımlar ve komut dosyası sağlandıktan sonra kullanıcılarınızın bir sonraki oturum açışlarında parolasını değiştirmesi gerekir.

Kullanıcı parolalarının geçirilmesi mümkündür ancak işlem çok daha karmaşıktır. Kullanıcıların, geçiş işleminin bir parçası olarak parolalarını güncelleştirmeleri gerekliliği ve bunları yeni, benzersiz parolalar kullanacak şekilde teşvik, uygulamanın genel güvenliğini artırmaları olasıdır.

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>web.config güvenlik ayarlarını Startup.cs 'e geçirme

Yukarıda belirtildiği gibi, ASP.NET üyeliği ve rol sağlayıcıları uygulamanın web.config dosyasında yapılandırılır. ASP.NET Core uygulamalar IIS 'ye bağlı olmadığından ve yapılandırma için ayrı bir sistem kullandıklarından, bu ayarların başka bir yerde yapılandırılması gerekir. Çoğu bölüm için, ASP.NET Core kimlik `Startup.cs` dosyada yapılandırılır. Daha önce oluşturulmuş olan Web projesini açın (kimlik tablosu şeması oluşturmak için) ve dosyasını gözden geçirin `Startup.cs` .

Varsayılan ConfigureServices yöntemi EF Core ve kimlik için destek ekler:

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

`AddDefaultIdentity`Genişletme yöntemi, kimliği varsayılan `ApplicationDbContext` ve çerçevesinin türünü kullanacak şekilde yapılandırmak için kullanılır `IdentityUser` . Özel bir kullanıyorsanız `IdentityUser` , türünü burada belirttiğinizden emin olun. Bu uzantı yöntemleri uygulamanızda çalışmıyorsa, uygun bir using deyimlerinin olduğunu ve gerekli NuGet paket başvurularına sahip olup olmadığınızı kontrol edin. Örneğin, projeniz `Microsoft.AspNetCore.Identity.EntityFrameworkCore` başvurulan ve paketlerinin bazı sürümlerine sahip olmalıdır `Microsoft.AspNetCore.Identity.UI` .

Ayrıca, `Startup.cs` site için yapılandırılmış gerekli ara yazılımı görmeniz gerekir. Özellikle, `UseAuthentication` ve `UseAuthorization` doğru konumda ayarlanmalıdır.

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

ASP.NET Identity, içindeki konumlara anonim veya rol tabanlı erişimi yapılandırmaz `Startup.cs` . Konuma özgü herhangi bir Yetkilendirme yapılandırma verilerini ASP.NET Core filtrelerine geçirmeniz gerekecektir. Hangi klasör ve sayfaların bu güncelleştirme için gerekli olacağını unutmayın. Sonraki bölümde bu değişiklikleri yaparsınız.

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>Bağımsız sayfaları ASP.NET Core kimlik soyutlamalarını kullanacak şekilde güncelleştirme

ASP.NET Web Forms uygulamanızda, anonim kullanıcılara belirli sayfalara veya klasörlere erişimi reddetmek için web.config ayarlarınıza sahipseniz, bu `[Authorize]` tür sayfalara özniteliği ekleyerek geçişi yaparsınız:

```razor
@attribute [Authorize]
```

Belirli bir role ait olan kullanıcılar hariç erişimi daha fazla reddetseyiyorsa, bunu bir rol belirten bir öznitelik ekleyerek de geçirebilirsiniz:

```razor
@attribute [Authorize(Roles ="administrators")]
```

`[Authorize]`Özniteliğin yalnızca `@page` yönlendirici üzerinden ulaşılan bileşenlerde çalışıp çalışmadığını unutmayın Blazor . Özniteliği, bunun yerine kullanılması gereken alt bileşenleriyle birlikte çalışmaz `AuthorizeView` .

Belirli bir kullanıcıya bazı kodların görüntülenip görüntülenmeyeceğini belirlemek için sayfa biçimlendirmesinde mantığa sahipseniz, bunu `AuthorizeView` bileşeniyle değiştirebilirsiniz. [Authorizeview bileşeni](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) , kullanıcının onu görme yetkisine sahip olup olmadığına bağlı olarak Kullanıcı arabirimini seçmeli olarak görüntüler. Ayrıca `context` , Kullanıcı bilgilerine erişmek için kullanılabilecek bir değişken gösterir.

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

Kullanıcıya özniteliğiyle yapılandırılmış bir öğesinden erişerek, yordamsal mantığdaki kimlik doğrulama durumuna erişebilirsiniz `Task<AuthenticationState` `[CascadingParameter]` . Bu, kullanıcıya erişim sağlar. Bu, kimlik doğrulamasının yapılıp kalmadığını ve belirli bir role ait olup olmadığını belirlemenizi sağlar. Bir ilke procedurally değerlendirmeniz gerekiyorsa, bir örneğini ekleyebilir `IAuthorizationService` ve `AuthorizeAsync` üzerinde yöntemi çağırır. Aşağıdaki örnek kod, Kullanıcı bilgilerinin nasıl alınacağını ve yetkili bir kullanıcının ilke tarafından kısıtlanan bir görevi gerçekleştirmesine nasıl izin verildiğini gösterir `content-editor` .

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

`AuthenticationState`İlk olarak, bunun gibi bir geçişli parametreye bağlanmadan önce basamaklı bir değer olarak kurulum yapması gerekir. Bu genellikle bileşeni kullanılarak yapılır `CascadingAuthenticationState` . Bu genellikle içinde yapılır `App.razor` :

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a>Özet

Blazor , ASP.NET Core kimlik olan ASP.NET Core ile aynı güvenlik modelini kullanır. Evrensel sağlayıcılardan ASP.NET Core kimlik 'e geçiş oldukça basittir, ancak özgün veri şemasına çok fazla özelleştirme uygulandığını varsayarsak. Veriler geçirildikten sonra, uygulamalarda kimlik doğrulama ve yetkilendirme ile çalışma, Blazor çoğu güvenlik gereksinimi için programlı destek ile iyi şekilde belgelenmiştir.

## <a name="references"></a>Başvurular

- [ASP.NET Core kimliğe giriş](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [ASP.NET üyelik kimlik doğrulamasından ASP.NET Core 2,0 kimliği 'ne geçiş](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [Kimlik doğrulaması ve kimliği ASP.NET Core geçir](https://docs.microsoft.com/aspnet/core/migration/identity)
- [ASP.NET Core Blazor kimlik doğrulaması ve yetkilendirme](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[Önceki](config.md) 
> [Sonraki](migration.md)
