---
description: -Nullable (C# derleyici seçenekleri)
title: -Nullable (C# derleyici seçenekleri)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125052"
---
# <a name="-nullable-c-compiler-options"></a>-Nullable (C# derleyici seçenekleri)

**Nullable** seçeneği, istenen null yapılabilir bağlamı belirtmenize olanak tanır.

## <a name="syntax"></a>Söz dizimi

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Bağımsız değişkenler

`+` &#124; `-`  
`+`Ya da yalnızca **Nullable**bir belirtmek, derleyicinin null yapılabilir bağlamı etkinleştirmesine neden olur. `-` **Null değer atanabilir**, null yapılabilir bağlamı devre dışı bırakdıysanız, etkin olan belirtme.

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
Nullable bağlam seçeneğini belirtir. `+` `-` Ve ' ye benzer, ancak etkinleştirmek ve devre dışı bırakmak, ancak daha fazla boş değer atanabilir bağlam benzerliği sağlar. Null değer atanabilir `enable` ' i belirttiğinden aynı etkin olan bağımsız değişken. **-nullable** Belirtme `disable` , null yapılabilir bağlamı devre dışı bırakır. `warnings`Bağımsız değişkeni sağlarken **-Nullable: uyarılar**, null yapılabilir uyarı bağlamı etkindir. `annotations`Bağımsız değişkenini belirtirken **-Nullable: ek açıklamaları**, null yapılabilir ek açıklama bağlamı etkindir.

## <a name="remarks"></a>Açıklamalar

Akış Analizi, çalıştırılabilir koddaki değişkenlerin null olduğunu anlamak için kullanılır. Bir değişkenin Çıkarsanan null olabilme, değişkenin belirtilen null değer alabilme durumu değerinden bağımsızdır. Yöntem çağrıları, koşullu olarak atlanırsa bile çözümlenir. Örneğin, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yayın modunda.

Aşağıdaki özniteliklerle açıklama eklenmiş yöntemlerin çağrılması, akış analizini de etkiler:

- Basit ön koşullar: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Basit son koşullar: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Koşullu koşul sonrası: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (örneğin, `DoesNotReturnIf(false)` için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) ve <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Üye son koşullar: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> ve <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>Bir projede Bu derleyici seçeneğini ayarlamak için

Etiketi bir hiyerarşi içine eklemek için *. csproj* dosyasını düzenleyin `<Nullable>` `Project/PropertyGroup` :

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Boş değer atanabilir başvuru türleri](../../nullable-references.md)
