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
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama

ASP.NET Core 5,0 ' de, öğesinin aşırı yüklemesi <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> eklenmiştir. Yeni aşırı yükleme, özellikleri içeren en üst düzey model örneğini kabul eder:

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> doğrulamayı gerçekleştirmek için bu yeni aşırı yüklemesini çağırır `ValidationVisitor` . Doğrulama kitaplığınız ASP.NET Core MVC 'nin model doğrulama sistemiyle tümleştirirse, bu yeni aşırı yükleme ilgili olur.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="old-behavior"></a>Eski davranış

`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a>Yeni davranış

`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, diğer özelliklerin denetimine bağlı olan gibi Doğrulayıcıları desteklemek için sunulmuştur <xref:System.ComponentModel.DataAnnotations.CompareAttribute> .

## <a name="recommended-action"></a>Önerilen eylem

`ObjectModelValidator`Var olan aşırı yüklemesini çağırmak için kullanan doğrulama çerçeveleri, `ValidationVisitor` .NET 5,0 veya üstünü hedeflerken yeni yöntemi geçersiz kılmalıdır:

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
