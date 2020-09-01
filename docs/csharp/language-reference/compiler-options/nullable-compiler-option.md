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
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="32a16-103">-Nullable (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="32a16-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="32a16-104">**Nullable** seçeneği, istenen null yapılabilir bağlamı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="32a16-104">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="32a16-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="32a16-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="32a16-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="32a16-106">Arguments</span></span>

<span data-ttu-id="32a16-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="32a16-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="32a16-108">`+`Ya da yalnızca **Nullable**bir belirtmek, derleyicinin null yapılabilir bağlamı etkinleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="32a16-108">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="32a16-109">`-` **Null değer atanabilir**, null yapılabilir bağlamı devre dışı bırakdıysanız, etkin olan belirtme.</span><span class="sxs-lookup"><span data-stu-id="32a16-109">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="32a16-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="32a16-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="32a16-111">Nullable bağlam seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32a16-111">Specifies the nullable context option.</span></span> <span data-ttu-id="32a16-112">`+` `-` Ve ' ye benzer, ancak etkinleştirmek ve devre dışı bırakmak, ancak daha fazla boş değer atanabilir bağlam benzerliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a16-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="32a16-113">Null değer atanabilir `enable` ' i belirttiğinden aynı etkin olan bağımsız değişken. **-nullable**</span><span class="sxs-lookup"><span data-stu-id="32a16-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="32a16-114">Belirtme `disable` , null yapılabilir bağlamı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="32a16-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="32a16-115">`warnings`Bağımsız değişkeni sağlarken **-Nullable: uyarılar**, null yapılabilir uyarı bağlamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="32a16-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="32a16-116">`annotations`Bağımsız değişkenini belirtirken **-Nullable: ek açıklamaları**, null yapılabilir ek açıklama bağlamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="32a16-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="32a16-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32a16-117">Remarks</span></span>

<span data-ttu-id="32a16-118">Akış Analizi, çalıştırılabilir koddaki değişkenlerin null olduğunu anlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32a16-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="32a16-119">Bir değişkenin Çıkarsanan null olabilme, değişkenin belirtilen null değer alabilme durumu değerinden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="32a16-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="32a16-120">Yöntem çağrıları, koşullu olarak atlanırsa bile çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="32a16-120">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="32a16-121">Örneğin, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yayın modunda.</span><span class="sxs-lookup"><span data-stu-id="32a16-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="32a16-122">Aşağıdaki özniteliklerle açıklama eklenmiş yöntemlerin çağrılması, akış analizini de etkiler:</span><span class="sxs-lookup"><span data-stu-id="32a16-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="32a16-123">Basit ön koşullar: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="32a16-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="32a16-124">Basit son koşullar: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="32a16-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="32a16-125">Koşullu koşul sonrası: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="32a16-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="32a16-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (örneğin, `DoesNotReturnIf(false)` için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) ve <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="32a16-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="32a16-127">Üye son koşullar: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> ve <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="32a16-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="32a16-128">Bir projede Bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="32a16-128">To set this compiler option in a project</span></span>

<span data-ttu-id="32a16-129">Etiketi bir hiyerarşi içine eklemek için *. csproj* dosyasını düzenleyin `<Nullable>` `Project/PropertyGroup` :</span><span class="sxs-lookup"><span data-stu-id="32a16-129">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="32a16-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32a16-130">See also</span></span>

- [<span data-ttu-id="32a16-131">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="32a16-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="32a16-132">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="32a16-132">Nullable reference types</span></span>](../../nullable-references.md)
