---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609310"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="d9850-101">MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama</span><span class="sxs-lookup"><span data-stu-id="d9850-101">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="d9850-102">ASP.NET Core 5,0 ' de, öğesinin aşırı yüklemesi <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9850-102">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="d9850-103">Yeni aşırı yükleme, özellikleri içeren en üst düzey model örneğini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="d9850-103">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="d9850-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> doğrulamayı gerçekleştirmek için bu yeni aşırı yüklemesini çağırır `ValidationVisitor` .</span><span class="sxs-lookup"><span data-stu-id="d9850-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="d9850-105">Doğrulama kitaplığınız ASP.NET Core MVC 'nin model doğrulama sistemiyle tümleştirirse, bu yeni aşırı yükleme ilgili olur.</span><span class="sxs-lookup"><span data-stu-id="d9850-105">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="d9850-106">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).</span><span class="sxs-lookup"><span data-stu-id="d9850-106">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d9850-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d9850-107">Version introduced</span></span>

<span data-ttu-id="d9850-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d9850-108">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d9850-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d9850-109">Old behavior</span></span>

<span data-ttu-id="d9850-110">`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="d9850-110">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a><span data-ttu-id="d9850-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d9850-111">New behavior</span></span>

<span data-ttu-id="d9850-112">`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="d9850-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a><span data-ttu-id="d9850-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d9850-113">Reason for change</span></span>

<span data-ttu-id="d9850-114">Bu değişiklik, diğer özelliklerin denetimine bağlı olan gibi Doğrulayıcıları desteklemek için sunulmuştur <xref:System.ComponentModel.DataAnnotations.CompareAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d9850-114">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d9850-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d9850-115">Recommended action</span></span>

<span data-ttu-id="d9850-116">`ObjectModelValidator`Var olan aşırı yüklemesini çağırmak için kullanan doğrulama çerçeveleri, `ValidationVisitor` .NET 5,0 veya üstünü hedeflerken yeni yöntemi geçersiz kılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="d9850-116">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a><span data-ttu-id="d9850-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="d9850-117">Category</span></span>

<span data-ttu-id="d9850-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d9850-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d9850-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d9850-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
