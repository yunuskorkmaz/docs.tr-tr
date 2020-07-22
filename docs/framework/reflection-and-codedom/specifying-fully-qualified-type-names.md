---
title: Tam Olarak Nitelenmiş Tür Adlarını Belirtme
description: Yansıma işlemlerine yönelik geçerli giriş için, derleme adı belirtimleri, ad alanı belirtimleri ve tür adları bulunan tam nitelikli tür adlarını kullanın.
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865235"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="b67ff-103">Tam nitelikli tür adlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="b67ff-104">Çeşitli yansıma işlemlerine geçerli giriş sağlamak için tür adları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="b67ff-105">Tam nitelikli tür adı, bir derleme adı belirtimi, bir ad alanı belirtimi ve bir tür adından oluşur.</span><span class="sxs-lookup"><span data-stu-id="b67ff-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="b67ff-106">Tür adı belirtimleri,, ve gibi yöntemler tarafından <xref:System.Type.GetType%2A?displayProperty=nameWithType> kullanılır <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b67ff-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="b67ff-107">Tür adları için dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="b67ff-107">Grammar for type names</span></span>

 <span data-ttu-id="b67ff-108">Dilbilgisi, biçimsel dillerin sözdizimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b67ff-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="b67ff-109">Aşağıdaki tabloda, geçerli bir girişin nasıl tanınacağını betimleyen sözlü kurallar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="b67ff-110">Terminaller (daha fazla indirgenmiş olmayan öğeler) tüm büyük harflerle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="b67ff-111">Nonterminaller (daha fazla indirgenmiş olan bu öğeler), karışık büyük/küçük ve listedir tırnak içinde gösterilir, ancak tek tırnak (') sözdiziminin kendisinin bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="b67ff-112">Kanal karakteri (&#124;), alt kuralların bulunduğu kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="b67ff-113">Özel karakterler belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-113">Specifying special characters</span></span>

<span data-ttu-id="b67ff-114">Tür adında, tanımlayıcı, bir dilin kuralları tarafından belirlenen geçerli bir addır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="b67ff-115">\\Tanımlayıcının bir parçası olarak kullanıldığında aşağıdaki belirteçleri ayırmak için bir kaçış karakteri olarak ters eğik çizgi () kullanın.</span><span class="sxs-lookup"><span data-stu-id="b67ff-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="b67ff-116">Belirteç</span><span class="sxs-lookup"><span data-stu-id="b67ff-116">Token</span></span>|<span data-ttu-id="b67ff-117">Anlamı</span><span class="sxs-lookup"><span data-stu-id="b67ff-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="b67ff-118">\\,</span><span class="sxs-lookup"><span data-stu-id="b67ff-118">\\,</span></span>|<span data-ttu-id="b67ff-119">Derleme ayırıcısı.</span><span class="sxs-lookup"><span data-stu-id="b67ff-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="b67ff-120">İç içe tür ayırıcısı.</span><span class="sxs-lookup"><span data-stu-id="b67ff-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="b67ff-121">Başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="b67ff-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="b67ff-122">İşaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="b67ff-122">Pointer type.</span></span>|
|<span data-ttu-id="b67ff-123">\\[</span><span class="sxs-lookup"><span data-stu-id="b67ff-123">\\[</span></span>|<span data-ttu-id="b67ff-124">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b67ff-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="b67ff-125">\\]</span><span class="sxs-lookup"><span data-stu-id="b67ff-125">\\]</span></span>|<span data-ttu-id="b67ff-126">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b67ff-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="b67ff-127">\\.</span><span class="sxs-lookup"><span data-stu-id="b67ff-127">\\.</span></span>|<span data-ttu-id="b67ff-128">Yalnızca nokta bir dizi belirtiminde kullanılıyorsa, bir dönemden önce ters eğik çizgiyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b67ff-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="b67ff-129">NamespaceSpec içindeki dönemler ters eğik çizgi almaz.</span><span class="sxs-lookup"><span data-stu-id="b67ff-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="b67ff-130">\\\|Dize sabit değeri olarak gerektiğinde ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="b67ff-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="b67ff-131">AssemblyNameSpec hariç tüm TypeSpec bileşenlerinde, boşluklar ilgili olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b67ff-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="b67ff-132">AssemblyNameSpec içinde, ', ' ayırıcısından önceki boşluklar ilgilidir, ancak ', ' ayırıcısından sonra boşluklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="b67ff-133">Gibi yansıma sınıfları <xref:System.Type.FullName%2A?displayProperty=nameWithType> , döndürülen adın ' <xref:System.Type.GetType%2A> de olduğu gibi bir çağrısında kullanılabilmesi için karıştırılmış adı döndürür `MyType.GetType(myType.FullName)` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="b67ff-134">Örneğin, bir türün tam nitelikli adı olabilir `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="b67ff-135">Ad alanı olsaydı `Ozzy.Out+Back` , artı işaretinin önünde ters eğik çizgi gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="b67ff-136">Aksi takdirde, ayrıştırıcı bunu iç içe ayırıcı olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="b67ff-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="b67ff-137">Yansıma bu dizeyi olarak yayar `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="b67ff-138">Derleme adlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-138">Specifying assembly names</span></span>

<span data-ttu-id="b67ff-139">Bir derleme adı belirtiminde gereken en düşük bilgiler, derlemenin metinsel adıdır (tanımlayıcı).</span><span class="sxs-lookup"><span data-stu-id="b67ff-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="b67ff-140">Aşağıdaki tabloda açıklandığı gibi, TANıMLAYıCıYı, bir özellik/değer çiftleri için virgülle ayrılmış bir liste ile takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b67ff-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="b67ff-141">TANıMLAYıCı adlandırması dosya adlandırmayla ilgili kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="b67ff-142">TANıMLAYıCı büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="b67ff-143">Özellik adı</span><span class="sxs-lookup"><span data-stu-id="b67ff-143">Property name</span></span>|<span data-ttu-id="b67ff-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b67ff-144">Description</span></span>|<span data-ttu-id="b67ff-145">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="b67ff-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="b67ff-146">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="b67ff-146">**Version**</span></span>|<span data-ttu-id="b67ff-147">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="b67ff-147">Assembly version number</span></span>|<span data-ttu-id="b67ff-148">*Birincil. Minor. Build. Revision*, burada *büyük*, *küçük*, *derleme*ve *Düzeltme* , 0 ile 65535 dahil olmak üzere tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="b67ff-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="b67ff-149">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="b67ff-149">**PublicKey**</span></span>|<span data-ttu-id="b67ff-150">Tam ortak anahtar</span><span class="sxs-lookup"><span data-stu-id="b67ff-150">Full public key</span></span>|<span data-ttu-id="b67ff-151">Onaltılık biçimdeki tam ortak anahtarın dize değeri.</span><span class="sxs-lookup"><span data-stu-id="b67ff-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="b67ff-152">Özel bir derlemeyi açıkça belirtmek için bir null başvurusu (Visual Basic**hiçbir şey** ) belirtin.</span><span class="sxs-lookup"><span data-stu-id="b67ff-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="b67ff-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="b67ff-153">**PublicKeyToken**</span></span>|<span data-ttu-id="b67ff-154">Ortak anahtar belirteci (tam ortak anahtarın 8 baytlık karması)</span><span class="sxs-lookup"><span data-stu-id="b67ff-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="b67ff-155">Onaltılık biçimdeki ortak anahtar belirtecinin dize değeri.</span><span class="sxs-lookup"><span data-stu-id="b67ff-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="b67ff-156">Özel bir derlemeyi açıkça belirtmek için bir null başvurusu (Visual Basic**hiçbir şey** ) belirtin.</span><span class="sxs-lookup"><span data-stu-id="b67ff-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="b67ff-157">**Culture (Kültür)**</span><span class="sxs-lookup"><span data-stu-id="b67ff-157">**Culture**</span></span>|<span data-ttu-id="b67ff-158">Derleme kültürü</span><span class="sxs-lookup"><span data-stu-id="b67ff-158">Assembly culture</span></span>|<span data-ttu-id="b67ff-159">RFC-1766 biçiminde derlemenin kültürü veya dilden bağımsız (uydu olmayan) derlemeler için "nötr".</span><span class="sxs-lookup"><span data-stu-id="b67ff-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="b67ff-160">**Özel**</span><span class="sxs-lookup"><span data-stu-id="b67ff-160">**Custom**</span></span>|<span data-ttu-id="b67ff-161">Özel ikili büyük nesne (BLOB).</span><span class="sxs-lookup"><span data-stu-id="b67ff-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="b67ff-162">Bu, şu anda yalnızca [Yerel Görüntü Oluşturucu (NGen)](../tools/ngen-exe-native-image-generator.md)tarafından oluşturulan derlemelerde kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="b67ff-163">Yerel Görüntü Oluşturucu aracı tarafından, yüklenen derlemenin yerel görüntü olduğunu ve bu nedenle yerel görüntü önbelleğine yükleneceğini bildiren derleme önbelleğine bildirmek için kullanılan özel dize.</span><span class="sxs-lookup"><span data-stu-id="b67ff-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="b67ff-164">Ayrıca, Zap dizesi olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-164">Also called a zap string.</span></span>|

<span data-ttu-id="b67ff-165">Aşağıdaki örnek, varsayılan kültür ile basitçe adlandırılmış bir derleme için bir **AssemblyName** gösterir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="b67ff-166">Aşağıdaki örnek, "en" kültürü ile kesin adlandırılmış derleme için tam olarak belirtilen başvuruyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="b67ff-167">Aşağıdaki örneklerde her biri, kesin olarak belirtilen bir **AssemblyName**gösterir, bu, güçlü veya basitçe adlandırılmış bir derleme tarafından karşılanır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="b67ff-168">Aşağıdaki örneklerde, tek bir adlandırılmış derleme tarafından karşılanması gereken kısmen belirtilen **AssemblyName**gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="b67ff-169">Aşağıdaki örneklerde her biri, kesin olarak adlandırılmış bir derleme tarafından karşılanması gereken kısmen belirtilen bir **AssemblyName**gösterir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="b67ff-170">Genel türleri belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-170">Specifying generic types</span></span>

<span data-ttu-id="b67ff-171">SimpleTypeSpec \` numarası, 1 ile *n* genel tür parametrelerinden oluşan açık bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b67ff-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="b67ff-172">Örneğin, açık genel tür listesine \<T> veya kapalı genel tür listesine başvuru almak için \<String> , ``Type.GetType("System.Collections.Generic.List`1")`` genel tür sözlüğüne bir başvuru almak için kullanın \<TKey,TValue> ``Type.GetType("System.Collections.Generic.Dictionary`2")`` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="b67ff-173">İşaretçileri belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-173">Specifying pointers</span></span>

<span data-ttu-id="b67ff-174">SimpleTypeSpec \*, yönetilmeyen bir işaretçiyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b67ff-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="b67ff-175">Örneğin, MyType türünde bir işaretçi almak için kullanın `Type.GetType("MyType*")` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="b67ff-176">MyType türünde bir işaretçiye işaretçi almak için kullanın `Type.GetType("MyType**")` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="b67ff-177">Başvuruları belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-177">Specifying references</span></span>

<span data-ttu-id="b67ff-178">SimpleTypeSpec &, yönetilen bir işaretçiyi veya başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b67ff-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="b67ff-179">Örneğin, MyType türü için bir başvuru almak için kullanın `Type.GetType("MyType &")` .</span><span class="sxs-lookup"><span data-stu-id="b67ff-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="b67ff-180">İşaretçilerin aksine, başvuruların bir düzey ile sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b67ff-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="b67ff-181">Dizileri belirtme</span><span class="sxs-lookup"><span data-stu-id="b67ff-181">Specifying arrays</span></span>

<span data-ttu-id="b67ff-182">BNF dilbilgisinde, ReflectionEmitDimension yalnızca kullanılarak alınan eksik tür tanımları için geçerlidir <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b67ff-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b67ff-183">Tamamlanmamış tür tanımları <xref:System.Reflection.Emit.TypeBuilder> kullanılarak oluşturulan, <xref:System.Reflection.Emit?displayProperty=nameWithType> ancak üzerinde olmayan nesneler <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b67ff-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="b67ff-184">ReflectionDimension, tamamlanmış olan ve yüklenmiş bir tür tanımını almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="b67ff-185">Dizilere dizi derecesi belirtilerek bir şekilde erişilir:</span><span class="sxs-lookup"><span data-stu-id="b67ff-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="b67ff-186">`Type.GetType("MyArray[]")`0 alt sınırı olan tek boyutlu bir diziyi alır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="b67ff-187">`Type.GetType("MyArray[*]")`bilinmeyen alt sınır içeren tek boyutlu bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="b67ff-188">`Type.GetType("MyArray[][]")`iki boyutlu bir dizinin dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="b67ff-189">`Type.GetType("MyArray[*,*]")`ve `Type.GetType("MyArray[,]")` Bilinmeyen alt sınırlara sahip dikdörtgen iki boyutlu bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="b67ff-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="b67ff-190">Bir çalışma zamanı noktasından, `MyArray[] != MyArray[*]` ancak çok boyutlu diziler için iki gösterimin eşdeğer olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b67ff-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="b67ff-191">Yani, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` **true**olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="b67ff-192">**ModuleBuilder. GetType**için, `MyArray[0..5]` 6 boyutunda bir tek boyutlu diziyi, alt sınır 0 ' ı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="b67ff-193">`MyArray[4…]`Bilinmeyen boyut ve alt sınır 4 ' ün tek boyutlu dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b67ff-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="b67ff-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b67ff-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b67ff-195">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b67ff-195">Viewing Type Information</span></span>](viewing-type-information.md)
