---
title: Kod Analizi uyarılarını gösterme
description: .NET kod analizi ihlallerini bastırmak için kullanabileceğiniz farklı yolları öğrenin.
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: a8fdfbddd2393f9c6c8cd882a63a9ecc6cb1dc95
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637045"
---
# <a name="how-to-suppress-code-analysis-warnings"></a>Kod Analizi uyarılarını gösterme

Bu makalede, .NET uygulamanızı oluştururken kod analizinden gelen uyarıları bastırmak için çeşitli yollar ele alınmaktadır.

> [!TIP]
> Geliştirme ortamınız olarak Visual Studio kullanıyorsanız *ampul* menüsü, uyarıları sizin için göstermede kodu oluşturan seçenekler sağlar. Daha fazla bilgi için bkz. [Ihlalleri gösterme](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).

## <a name="disable-the-rule"></a>Kuralı devre dışı bırak

Uyarıya neden olan kod analizi kuralını devre dışı bırakarak, tüm dosyanız veya projeniz için kuralı devre dışı bırakın (kullandığınız [yapılandırma dosyasının](configuration-files.md) kapsamına bağlı olarak). Kuralı devre dışı bırakmak için yapılandırma dosyasında önem derecesini ayarlayın `none` .

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

Kural özellikleri hakkında daha fazla bilgi için bkz. [kural önem derecesini yapılandırma](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).

## <a name="use-a-preprocessor-directive"></a>Önişlemci yönergesi kullanma

Yalnızca belirli bir kod satırı için uyarıyı bastırmak üzere [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) veya [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) yönergesini kullanın.

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a>SuppressMessageAttribute kullanın

Bir <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> uyarıyı, kaynak dosyasında ya da proje için küresel bir gizlemeler dosyasında (*globalsuppressions. cs* veya *globalsuppressions. vb*) gizlemek için kullanabilirsiniz. Bu öznitelik, bir uyarıyı yalnızca projenizin veya dosyanızın belirli bölümlerinde bastırmak için bir yol sağlar.

Özniteliği için gereken iki, Konumsal parametre <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ve kural *kimliği* *kategorisidir* . Aşağıdaki kod parçacığı, `"Usage"` ve `"CA2200:Rethrow to preserve stack details"` Bu parametreleri geçirir.

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

Özniteliği genel gizlemeleri dosyasına eklerseniz, gizleme, örneğin, gizlemeyi istediğiniz düzeye göre [kapsamınızda](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) `"member"` . Uyarının özelliği kullanılarak gizlenmesi gereken API 'YI belirtirsiniz <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> .

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

Açıkça sağlanmış Kullanıcı kaynağıyla eşleşmeyen derleyici tarafından oluşturulan koda yönelik uyarıları gizlemek için, gizleme özniteliğini küresel bir gizlemeleri dosyasına koymanız gerekir. Örneğin, aşağıdaki kod derleyiciye yayılan bir oluşturucuya karşı bir ihlalin bastırır:

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a>Ayrıca bkz.

- [İhlalleri gösterme (Visual Studio)](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
