---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609310"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama

ASP.NET Core 5,0 ' de, öğesinin aşırı yüklemesi <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> eklenmiştir. Yeni aşırı yükleme, özellikleri içeren en üst düzey model örneğini kabul eder:

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> doğrulamayı gerçekleştirmek için bu yeni aşırı yüklemesini çağırır `ValidationVisitor` . Doğrulama kitaplığınız ASP.NET Core MVC 'nin model doğrulama sistemiyle tümleştirirse, bu yeni aşırı yükleme ilgili olur.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="old-behavior"></a>Eski davranış

`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a>Yeni davranış

`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, diğer özelliklerin denetimine bağlı olan gibi Doğrulayıcıları desteklemek için sunulmuştur <xref:System.ComponentModel.DataAnnotations.CompareAttribute> .

#### <a name="recommended-action"></a>Önerilen eylem

`ObjectModelValidator`Var olan aşırı yüklemesini çağırmak için kullanan doğrulama çerçeveleri, `ValidationVisitor` .NET 5,0 veya üstünü hedeflerken yeni yöntemi geçersiz kılmalıdır:

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
