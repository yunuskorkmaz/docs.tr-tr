---
title: "Son değişiklik: MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama"
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında MVC hakkında bilgi edinin: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrula"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b28c357f51291a4f73889d5d413a983f79e09daf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761681"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="d8eb9-103">MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama</span><span class="sxs-lookup"><span data-stu-id="d8eb9-103">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="d8eb9-104">ASP.NET Core 5,0 ' de, öğesinin aşırı yüklemesi <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8eb9-104">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="d8eb9-105">Yeni aşırı yükleme, özellikleri içeren en üst düzey model örneğini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="d8eb9-105">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="d8eb9-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> doğrulamayı gerçekleştirmek için bu yeni aşırı yüklemesini çağırır `ValidationVisitor` .</span><span class="sxs-lookup"><span data-stu-id="d8eb9-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="d8eb9-107">Doğrulama kitaplığınız ASP.NET Core MVC 'nin model doğrulama sistemiyle tümleştirirse, bu yeni aşırı yükleme ilgili olur.</span><span class="sxs-lookup"><span data-stu-id="d8eb9-107">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="d8eb9-108">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).</span><span class="sxs-lookup"><span data-stu-id="d8eb9-108">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d8eb9-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d8eb9-109">Version introduced</span></span>

<span data-ttu-id="d8eb9-110">5.0</span><span class="sxs-lookup"><span data-stu-id="d8eb9-110">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d8eb9-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d8eb9-111">Old behavior</span></span>

<span data-ttu-id="d8eb9-112">`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="d8eb9-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a><span data-ttu-id="d8eb9-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d8eb9-113">New behavior</span></span>

<span data-ttu-id="d8eb9-114">`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="d8eb9-114">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a><span data-ttu-id="d8eb9-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d8eb9-115">Reason for change</span></span>

<span data-ttu-id="d8eb9-116">Bu değişiklik, diğer özelliklerin denetimine bağlı olan gibi Doğrulayıcıları desteklemek için sunulmuştur <xref:System.ComponentModel.DataAnnotations.CompareAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d8eb9-116">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d8eb9-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d8eb9-117">Recommended action</span></span>

<span data-ttu-id="d8eb9-118">`ObjectModelValidator`Var olan aşırı yüklemesini çağırmak için kullanan doğrulama çerçeveleri, `ValidationVisitor` .NET 5,0 veya üstünü hedeflerken yeni yöntemi geçersiz kılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="d8eb9-118">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a><span data-ttu-id="d8eb9-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d8eb9-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
