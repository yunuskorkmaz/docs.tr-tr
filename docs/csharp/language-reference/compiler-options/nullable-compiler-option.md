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
ms.openlocfilehash: 68857d0cb4d0cd1177506e0b7ce897d2cfc3aa5b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099230"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="c3c80-103">-Nullable (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c3c80-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="c3c80-104">**Nullable** seçeneği, null yapılabilir bağlamı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c3c80-104">The **-nullable** option lets you specify the nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3c80-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c3c80-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="c3c80-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c3c80-106">Arguments</span></span>

<span data-ttu-id="c3c80-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c3c80-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="c3c80-108">`+`Ya da **Nullable**, derleyicinin null yapılabilir bağlamı etkinleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c3c80-108">Specifying `+`, or **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="c3c80-109">`-` **Null değer atanamaz** belirtmezseniz, etkin olmayan, null olabilen bağlamı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c3c80-109">Specifying `-`, which is in effect if you don't specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="c3c80-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="c3c80-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="c3c80-111">Nullable bağlam seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3c80-111">Specifies the nullable context option.</span></span> <span data-ttu-id="c3c80-112">`+` `-` Ve ' ye benzer, ancak etkinleştirmek ve devre dışı bırakmak, ancak daha fazla boş değer atanabilir bağlam benzerliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3c80-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="c3c80-113">Null değer atanabilir `enable` ' i belirttiğinden aynı etkin olan bağımsız değişken. **-nullable**</span><span class="sxs-lookup"><span data-stu-id="c3c80-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="c3c80-114">Belirtme `disable` , null yapılabilir bağlamı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c3c80-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="c3c80-115">`warnings`Bağımsız değişkeni sağlarken **-Nullable: uyarılar**, null yapılabilir uyarı bağlamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="c3c80-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="c3c80-116">`annotations`Bağımsız değişkenini belirtirken **-Nullable: ek açıklamaları**, null yapılabilir ek açıklama bağlamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="c3c80-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3c80-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3c80-117">Remarks</span></span>

<span data-ttu-id="c3c80-118">Akış Analizi, çalıştırılabilir koddaki değişkenlerin null olduğunu anlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3c80-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="c3c80-119">Bir değişkenin Çıkarsanan null olabilme, değişkenin belirtilen null değer alabilme durumu değerinden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c3c80-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="c3c80-120">Yöntem çağrıları, koşullu olarak atlanırsa bile çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="c3c80-120">Method calls are analyzed even when they're conditionally omitted.</span></span> <span data-ttu-id="c3c80-121">Örneğin, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yayın modunda.</span><span class="sxs-lookup"><span data-stu-id="c3c80-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="c3c80-122">Aşağıdaki özniteliklerle açıklama eklenmiş yöntemlerin çağrılması, akış analizini de etkiler:</span><span class="sxs-lookup"><span data-stu-id="c3c80-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="c3c80-123">Basit ön koşullar: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="c3c80-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="c3c80-124">Basit son koşullar: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="c3c80-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="c3c80-125">Koşullu koşul sonrası: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="c3c80-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="c3c80-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (örneğin, `DoesNotReturnIf(false)` için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) ve <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="c3c80-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="c3c80-127">Üye son koşullar: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> ve <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="c3c80-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3c80-128">Global null yapılabilir bağlam, oluşturulan kod dosyaları için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="c3c80-128">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="c3c80-129">Bu ayardan bağımsız olarak, null yapılabilir bağlam, oluşturuldu olarak işaretlenen tüm kaynak dosyaları için *devre dışıdır* .</span><span class="sxs-lookup"><span data-stu-id="c3c80-129">Regardless of this setting, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="c3c80-130">Bir dosyanın oluşturulduğu şekilde işaretlenmiş dört yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="c3c80-130">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="c3c80-131">. Editorconfig dosyasında, `generated_code = true` Bu dosya için geçerli olan bir bölümde belirtin.</span><span class="sxs-lookup"><span data-stu-id="c3c80-131">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="c3c80-132">`<auto-generated>` `<auto-generated/>` Dosyanın üst kısmına bir açıklama koyun.</span><span class="sxs-lookup"><span data-stu-id="c3c80-132">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="c3c80-133">Bu, açıklama içindeki herhangi bir satırda olabilir, ancak açıklama bloğu dosyadaki ilk öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3c80-133">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="c3c80-134">Dosya adını *TemporaryGeneratedFile_* başlatın</span><span class="sxs-lookup"><span data-stu-id="c3c80-134">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="c3c80-135">Dosya adını *. Designer.cs*, *. generated.cs*, *. g.cs* veya *. g.i.cs* ile sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="c3c80-135">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="c3c80-136">Oluşturucular, Önişlemci yönergesini kullanarak kabul edebilir [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) .</span><span class="sxs-lookup"><span data-stu-id="c3c80-136">Generators can opt-in using the [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="c3c80-137">Bir projede Bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c3c80-137">To set this compiler option in a project</span></span>

<span data-ttu-id="c3c80-138">Etiketi bir hiyerarşi içine eklemek için *. csproj* dosyasını düzenleyin `<Nullable>` `Project/PropertyGroup` :</span><span class="sxs-lookup"><span data-stu-id="c3c80-138">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="c3c80-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3c80-139">See also</span></span>

- [<span data-ttu-id="c3c80-140">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c3c80-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c3c80-141">`#nullable` Önişlemci yönergesi</span><span class="sxs-lookup"><span data-stu-id="c3c80-141">`#nullable` preprocessor directive</span></span>](../preprocessor-directives/preprocessor-nullable.md)
- [<span data-ttu-id="c3c80-142">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="c3c80-142">Nullable reference types</span></span>](../../nullable-references.md)
