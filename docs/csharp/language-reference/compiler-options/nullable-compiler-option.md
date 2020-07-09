---
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
ms.openlocfilehash: f1aba7e08f472411640d42f51d78ca6f7e5cc900
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100892"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="1ce32-102">-Nullable (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1ce32-102">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="1ce32-103">**Nullable** seçeneği, istenen null yapılabilir bağlamı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1ce32-103">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ce32-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1ce32-104">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="1ce32-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1ce32-105">Arguments</span></span>

<span data-ttu-id="1ce32-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="1ce32-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="1ce32-107">`+`Ya da yalnızca **Nullable**bir belirtmek, derleyicinin null yapılabilir bağlamı etkinleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1ce32-107">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="1ce32-108">`-` **Null değer atanabilir**, null yapılabilir bağlamı devre dışı bırakdıysanız, etkin olan belirtme.</span><span class="sxs-lookup"><span data-stu-id="1ce32-108">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="1ce32-109">`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`</span><span class="sxs-lookup"><span data-stu-id="1ce32-109">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="1ce32-110">Nullable bağlam seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ce32-110">Specifies the nullable context option.</span></span> <span data-ttu-id="1ce32-111">`+` `-` Ve ' ye benzer, ancak etkinleştirmek ve devre dışı bırakmak, ancak daha fazla boş değer atanabilir bağlam benzerliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ce32-111">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="1ce32-112">Null değer atanabilir `enable` ' i belirttiğinden aynı etkin olan bağımsız değişken. **-nullable**</span><span class="sxs-lookup"><span data-stu-id="1ce32-112">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="1ce32-113">Belirtme `disable` , null yapılabilir bağlamı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1ce32-113">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="1ce32-114">`warnings`Bağımsız değişkeni sağlarken **-Nullable: uyarılar**, null yapılabilir uyarı bağlamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="1ce32-114">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="1ce32-115">`annotations`Bağımsız değişkenini belirtirken **-Nullable: ek açıklamaları**, null yapılabilir ek açıklama bağlamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="1ce32-115">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ce32-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ce32-116">Remarks</span></span>

<span data-ttu-id="1ce32-117">Akış Analizi, çalıştırılabilir koddaki değişkenlerin null olduğunu anlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ce32-117">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="1ce32-118">Bir değişkenin Çıkarsanan null olabilme, değişkenin belirtilen null değer alabilme durumu değerinden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="1ce32-118">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="1ce32-119">Yöntem çağrıları, koşullu olarak atlanırsa bile çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="1ce32-119">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="1ce32-120">Örneğin, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yayın modunda.</span><span class="sxs-lookup"><span data-stu-id="1ce32-120">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="1ce32-121">Aşağıdaki özniteliklerle açıklama eklenmiş yöntemlerin çağrılması, akış analizini de etkiler:</span><span class="sxs-lookup"><span data-stu-id="1ce32-121">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="1ce32-122">Basit ön koşullar: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> ve<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="1ce32-122">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="1ce32-123">Basit son koşullar: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> ve<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="1ce32-123">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="1ce32-124">Koşullu koşul sonrası: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> ve<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="1ce32-124">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="1ce32-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>(örneğin, `DoesNotReturnIf(false)` için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) ve<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="1ce32-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="1ce32-126">Üye son koşullar: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> ve<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="1ce32-126">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="1ce32-127">Bir projede Bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1ce32-127">To set this compiler option in a project</span></span>

<span data-ttu-id="1ce32-128">Etiketi bir hiyerarşi içine eklemek için *. csproj* dosyasını düzenleyin `<Nullable>` `Project/PropertyGroup` :</span><span class="sxs-lookup"><span data-stu-id="1ce32-128">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="1ce32-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ce32-129">See also</span></span>

- [<span data-ttu-id="1ce32-130">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1ce32-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1ce32-131">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="1ce32-131">Nullable reference types</span></span>](../../nullable-references.md)
