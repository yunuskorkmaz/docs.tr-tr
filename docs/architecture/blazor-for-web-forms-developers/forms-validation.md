---
title: Formlar ve doğrulama
description: Blazor içinde istemci tarafı doğrulama ile form oluşturmayı öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 40b0c4ecce15032b0ae834fe3100414abd7e4e59
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183933"
---
# <a name="forms-and-validation"></a><span data-ttu-id="d2f1b-103">Formlar ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="d2f1b-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d2f1b-104">ASP.NET Web Forms Framework, bir forma (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`vb.) girilen kullanıcı girişini doğrulamayı işleyen bir doğrulama sunucusu denetimleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="d2f1b-105">ASP.NET Web Forms Framework, model bağlamayı ve veri ek açıklamalarına (`[Required]` `[Range]`, `[StringLength]`, vb.) göre modeli doğrulamayı da destekler.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="d2f1b-106">Doğrulama mantığı hem sunucuda hem de istemci üzerinde, kaldırma JavaScript tabanlı doğrulama kullanılarak zorlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="d2f1b-107">`ValidationSummary` Sunucu denetimi, kullanıcıya doğrulama hatalarının özetini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="d2f1b-108">Blazor, hem istemci hem de sunucu arasında doğrulama mantığının paylaşımını destekler.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="d2f1b-109">ASP.NET birçok ortak sunucu doğrulamayla önceden oluşturulmuş JavaScript uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="d2f1b-110">Çoğu durumda, geliştirici uygulamaya özgü doğrulama mantığını tam olarak uygulamak için JavaScript yazmak zorunda kalır.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="d2f1b-111">Aynı model türleri, veri ek açıklamaları ve doğrulama mantığı hem sunucu hem de istemcide kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="d2f1b-112">Blazor, bir giriş bileşenleri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="d2f1b-113">Giriş bileşenleri, alan verilerini bir modele bağlamayı ve form gönderildiğinde kullanıcı girişini doğrulamayı işler.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="d2f1b-114">Giriş bileşeni</span><span class="sxs-lookup"><span data-stu-id="d2f1b-114">Input component</span></span>|<span data-ttu-id="d2f1b-115">İşlenmiş HTML öğesi</span><span class="sxs-lookup"><span data-stu-id="d2f1b-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="d2f1b-116">Bileşen bu giriş bileşenlerini sarmalanmış ve doğrulama sürecini bir `EditContext`ile düzenler. `EditForm`</span><span class="sxs-lookup"><span data-stu-id="d2f1b-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="d2f1b-117">Bir `EditForm`oluştururken, `Model` parametresini kullanarak hangi model örneğinin bağlanılacağını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="d2f1b-118">Doğrulama genellikle veri ek açıklamaları kullanılarak yapılır ve genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="d2f1b-119">Veri ek açıklaması tabanlı doğrulamayı etkinleştirmek için, `DataAnnotationsValidator` bileşenini `EditForm`öğesinin bir alt öğesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="d2f1b-120">Bileşen geçerli (`OnValidSubmit`) ve geçersiz (`OnInvalidSubmit`) gönderimleri işlemek için uygun bir olay sağlar. `EditForm`</span><span class="sxs-lookup"><span data-stu-id="d2f1b-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="d2f1b-121">Ayrıca, doğrulamayı kendiniz tetiklemenizi `OnSubmit` ve işlemesini sağlayan daha genel bir olay da vardır.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="d2f1b-122">Doğrulama hatası özetini göstermek için `ValidationSummary` bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="d2f1b-123">Belirli bir giriş alanı için doğrulama iletilerini göstermek için, uygun model `ValidationMessage` üyesine işaret eden `For` parametresi için bir lambda ifadesi belirterek bileşeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="d2f1b-124">Aşağıdaki model türü, veri ek açıklamalarını kullanarak çeşitli doğrulama kuralları tanımlar:</span><span class="sxs-lookup"><span data-stu-id="d2f1b-124">The following model type defines several validation rules using data annotations:</span></span>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16, 
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000, 
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true", 
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

<span data-ttu-id="d2f1b-125">Aşağıdaki bileşen, `Starship` model türüne göre Blazor içinde bir form oluşturmayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f1b-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => "starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => "starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => "starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => "starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => "starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

<span data-ttu-id="d2f1b-126">Form gönderildikten sonra, model bağlantılı veriler veritabanı gibi herhangi bir veri deposuna kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="d2f1b-127">Blazor WebAssembly uygulamasında, verilerin sunucuya gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="d2f1b-128">Örneğin, bir HTTP POST isteği kullanma.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="d2f1b-129">Bir Blazor sunucu uygulamasında veriler zaten sunucuda bulunur, ancak kalıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="d2f1b-130">Blazor uygulamalarında veri erişiminin yönetilmesi, [verilerle ilgilenme](data.md) konusunun konusudur.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d2f1b-131">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d2f1b-131">Additional resources</span></span>

<span data-ttu-id="d2f1b-132">Blazor uygulamalarında [Formlar ve doğrulama](/aspnet/core/blazor/forms-validation) hakkında daha fazla bilgi için bkz. Blazor belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d2f1b-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d2f1b-133">[Önceki](state-management.md)
>[İleri](data.md)</span><span class="sxs-lookup"><span data-stu-id="d2f1b-133">[Previous](state-management.md)
[Next](data.md)</span></span>
