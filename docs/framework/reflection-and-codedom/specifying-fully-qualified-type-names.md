---
title: Tam Olarak Nitelenmiş Tür Adlarını Belirtme
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc8395492992c22da3c635f0de010516127f9be4
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2019
ms.locfileid: "61793009"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="9d845-102">Tam nitelikli tür adlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-102">Specifying fully qualified type names</span></span>

<span data-ttu-id="9d845-103">Çeşitli yansıma işlemlerine geçerli giriş sağlamak için tür adları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d845-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="9d845-104">Tam nitelikli tür adı, bir derleme adı belirtimi, bir ad alanı belirtimi ve bir tür adından oluşur.</span><span class="sxs-lookup"><span data-stu-id="9d845-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="9d845-105">Tür <xref:System.Type.GetType%2A?displayProperty=nameWithType>adı belirtimleri <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> ,<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>gibi yöntemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d845-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="9d845-106">Tür adları için dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="9d845-106">Grammar for type names</span></span>

 <span data-ttu-id="9d845-107">Dilbilgisi, biçimsel dillerin sözdizimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d845-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="9d845-108">Aşağıdaki tabloda, geçerli bir girişin nasıl tanınacağını betimleyen sözlü kurallar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="9d845-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="9d845-109">Terminaller (daha fazla indirgenmiş olmayan öğeler) tüm büyük harflerle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9d845-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="9d845-110">Nonterminaller (daha fazla indirgenmiş olan bu öğeler), karışık büyük/küçük ve listedir tırnak içinde gösterilir, ancak tek tırnak (') sözdiziminin kendisinin bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="9d845-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="9d845-111">Kanal karakteri (&#124;), alt kuralların bulunduğu kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d845-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>

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

## <a name="specifying-special-characters"></a><span data-ttu-id="9d845-112">Özel karakterler belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-112">Specifying special characters</span></span>

<span data-ttu-id="9d845-113">Tür adında, tanımlayıcı, bir dilin kuralları tarafından belirlenen geçerli bir addır.</span><span class="sxs-lookup"><span data-stu-id="9d845-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="9d845-114">Tanımlayıcının bir parçası olarak\\kullanıldığında aşağıdaki belirteçleri ayırmak için bir kaçış karakteri olarak ters eğik çizgi () kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d845-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="9d845-115">Belirteç</span><span class="sxs-lookup"><span data-stu-id="9d845-115">Token</span></span>|<span data-ttu-id="9d845-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d845-116">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="9d845-117">\\,</span><span class="sxs-lookup"><span data-stu-id="9d845-117">\\,</span></span>|<span data-ttu-id="9d845-118">Derleme ayırıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d845-118">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="9d845-119">İç içe tür ayırıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d845-119">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="9d845-120">Başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="9d845-120">Reference type.</span></span>|
|\\*|<span data-ttu-id="9d845-121">İşaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="9d845-121">Pointer type.</span></span>|
|<span data-ttu-id="9d845-122">\\[</span><span class="sxs-lookup"><span data-stu-id="9d845-122">\\[</span></span>|<span data-ttu-id="9d845-123">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d845-123">Array dimension delimiter.</span></span>|
|<span data-ttu-id="9d845-124">\\]</span><span class="sxs-lookup"><span data-stu-id="9d845-124">\\]</span></span>|<span data-ttu-id="9d845-125">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d845-125">Array dimension delimiter.</span></span>|
|<span data-ttu-id="9d845-126">\\.</span><span class="sxs-lookup"><span data-stu-id="9d845-126">\\.</span></span>|<span data-ttu-id="9d845-127">Yalnızca nokta bir dizi belirtiminde kullanılıyorsa, bir dönemden önce ters eğik çizgiyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d845-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="9d845-128">NamespaceSpec içindeki dönemler ters eğik çizgi almaz.</span><span class="sxs-lookup"><span data-stu-id="9d845-128">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="9d845-129">\\\|Dize sabit değeri olarak gerektiğinde ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="9d845-129">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="9d845-130">AssemblyNameSpec hariç tüm TypeSpec bileşenlerinde, boşluklar ilgili olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d845-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="9d845-131">AssemblyNameSpec içinde, ', ' ayırıcısından önceki boşluklar ilgilidir, ancak ', ' ayırıcısından sonra boşluklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="9d845-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="9d845-132">Gibi yansıma sınıfları <xref:System.Type.FullName%2A?displayProperty=nameWithType>, döndürülen adın ' de `MyType.GetType(myType.FullName)`olduğu gibi bir çağrısında kullanılabilmesi için <xref:System.Type.GetType%2A>karıştırılmış adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d845-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="9d845-133">Örneğin, bir türün `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`tam nitelikli adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d845-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="9d845-134">Ad alanı olsaydı `Ozzy.Out+Back`, artı işaretinin önünde ters eğik çizgi gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="9d845-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="9d845-135">Aksi takdirde, ayrıştırıcı bunu iç içe ayırıcı olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="9d845-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="9d845-136">Yansıma bu dizeyi olarak `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`yayar.</span><span class="sxs-lookup"><span data-stu-id="9d845-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="9d845-137">Derleme adlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-137">Specifying assembly names</span></span>

<span data-ttu-id="9d845-138">Bir derleme adı belirtiminde gereken en düşük bilgiler, derlemenin metinsel adıdır (tanımlayıcı).</span><span class="sxs-lookup"><span data-stu-id="9d845-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="9d845-139">Aşağıdaki tabloda açıklandığı gibi, TANıMLAYıCıYı, bir özellik/değer çiftleri için virgülle ayrılmış bir liste ile takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d845-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="9d845-140">TANıMLAYıCı adlandırması dosya adlandırmayla ilgili kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d845-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="9d845-141">TANıMLAYıCı büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="9d845-141">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="9d845-142">Özellik adı</span><span class="sxs-lookup"><span data-stu-id="9d845-142">Property name</span></span>|<span data-ttu-id="9d845-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d845-143">Description</span></span>|<span data-ttu-id="9d845-144">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="9d845-144">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="9d845-145">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="9d845-145">**Version**</span></span>|<span data-ttu-id="9d845-146">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="9d845-146">Assembly version number</span></span>|<span data-ttu-id="9d845-147">*Birincil. Minor. Build. Revision*, burada *büyük*, *küçük*, *derleme*ve *Düzeltme* , 0 ile 65535 dahil olmak üzere tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="9d845-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="9d845-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="9d845-148">**PublicKey**</span></span>|<span data-ttu-id="9d845-149">Tam ortak anahtar</span><span class="sxs-lookup"><span data-stu-id="9d845-149">Full public key</span></span>|<span data-ttu-id="9d845-150">Onaltılık biçimdeki tam ortak anahtarın dize değeri.</span><span class="sxs-lookup"><span data-stu-id="9d845-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="9d845-151">Özel bir derlemeyi açıkça belirtmek için bir null başvurusu (Visual Basic**hiçbir şey** ) belirtin.</span><span class="sxs-lookup"><span data-stu-id="9d845-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="9d845-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="9d845-152">**PublicKeyToken**</span></span>|<span data-ttu-id="9d845-153">Ortak anahtar belirteci (tam ortak anahtarın 8 baytlık karması)</span><span class="sxs-lookup"><span data-stu-id="9d845-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="9d845-154">Onaltılık biçimdeki ortak anahtar belirtecinin dize değeri.</span><span class="sxs-lookup"><span data-stu-id="9d845-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="9d845-155">Özel bir derlemeyi açıkça belirtmek için bir null başvurusu (Visual Basic**hiçbir şey** ) belirtin.</span><span class="sxs-lookup"><span data-stu-id="9d845-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="9d845-156">**Ayarı**</span><span class="sxs-lookup"><span data-stu-id="9d845-156">**Culture**</span></span>|<span data-ttu-id="9d845-157">Derleme kültürü</span><span class="sxs-lookup"><span data-stu-id="9d845-157">Assembly culture</span></span>|<span data-ttu-id="9d845-158">RFC-1766 biçiminde derlemenin kültürü veya dilden bağımsız (uydu olmayan) derlemeler için "nötr".</span><span class="sxs-lookup"><span data-stu-id="9d845-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="9d845-159">**Özel**</span><span class="sxs-lookup"><span data-stu-id="9d845-159">**Custom**</span></span>|<span data-ttu-id="9d845-160">Özel ikili büyük nesne (BLOB).</span><span class="sxs-lookup"><span data-stu-id="9d845-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="9d845-161">Bu, şu anda yalnızca [Yerel Görüntü Oluşturucu (NGen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)tarafından oluşturulan derlemelerde kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d845-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="9d845-162">Yerel Görüntü Oluşturucu aracı tarafından, yüklenen derlemenin yerel görüntü olduğunu ve bu nedenle yerel görüntü önbelleğine yükleneceğini bildiren derleme önbelleğine bildirmek için kullanılan özel dize.</span><span class="sxs-lookup"><span data-stu-id="9d845-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="9d845-163">Ayrıca, Zap dizesi olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="9d845-163">Also called a zap string.</span></span>|

<span data-ttu-id="9d845-164">Aşağıdaki örnek, varsayılan kültür ile basitçe adlandırılmış bir derleme için bir **AssemblyName** gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d845-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="9d845-165">Aşağıdaki örnek, "en" kültürü ile kesin adlandırılmış derleme için tam olarak belirtilen başvuruyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d845-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="9d845-166">Aşağıdaki örneklerde her biri, kesin olarak belirtilen bir **AssemblyName**gösterir, bu, güçlü veya basitçe adlandırılmış bir derleme tarafından karşılanır.</span><span class="sxs-lookup"><span data-stu-id="9d845-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="9d845-167">Aşağıdaki örneklerde, tek bir adlandırılmış derleme tarafından karşılanması gereken kısmen belirtilen **AssemblyName**gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9d845-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="9d845-168">Aşağıdaki örneklerde her biri, kesin olarak adlandırılmış bir derleme tarafından karşılanması gereken kısmen belirtilen bir **AssemblyName**gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d845-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="9d845-169">Genel türleri belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-169">Specifying generic types</span></span>

<span data-ttu-id="9d845-170">SimpleTypeSpec\`numarası, 1 ile *n* genel tür parametrelerinden oluşan açık bir genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d845-170">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="9d845-171">Örneğin, açık genel tür listesi\<T > veya kapalı genel tür listesi\<dize > başvuru almak için, genel tür sözlüğü\<TKey ``Type.GetType("System.Collections.Generic.List`1")`` , TValue > ``Type.GetType("System.Collections.Generic.Dictionary`2")``başvurusunu almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d845-171">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="9d845-172">İşaretçileri belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-172">Specifying pointers</span></span>

<span data-ttu-id="9d845-173">SimpleTypeSpec \*, yönetilmeyen bir işaretçiyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d845-173">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="9d845-174">Örneğin, MyType türünde bir işaretçi almak için kullanın `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="9d845-174">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="9d845-175">MyType türünde bir işaretçiye işaretçi almak için kullanın `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="9d845-175">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="9d845-176">Başvuruları belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-176">Specifying references</span></span>

<span data-ttu-id="9d845-177">SimpleTypeSpec &, yönetilen bir işaretçiyi veya başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d845-177">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="9d845-178">Örneğin, MyType türü için bir başvuru almak için kullanın `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="9d845-178">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="9d845-179">İşaretçilerin aksine, başvuruların bir düzey ile sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d845-179">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="9d845-180">Dizileri belirtme</span><span class="sxs-lookup"><span data-stu-id="9d845-180">Specifying arrays</span></span>

<span data-ttu-id="9d845-181">BNF dilbilgisinde, ReflectionEmitDimension yalnızca kullanılarak <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>alınan eksik tür tanımları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9d845-181">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9d845-182">Tamamlanmamış tür tanımları <xref:System.Reflection.Emit.TypeBuilder> kullanılarak <xref:System.Reflection.Emit?displayProperty=nameWithType> oluşturulan, ancak üzerinde <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> olmayan nesneler.</span><span class="sxs-lookup"><span data-stu-id="9d845-182">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="9d845-183">ReflectionDimension, tamamlanmış olan ve yüklenmiş bir tür tanımını almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d845-183">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="9d845-184">Dizilere dizi derecesi belirtilerek bir şekilde erişilir:</span><span class="sxs-lookup"><span data-stu-id="9d845-184">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="9d845-185">`Type.GetType("MyArray[]")`0 alt sınırı olan tek boyutlu bir diziyi alır.</span><span class="sxs-lookup"><span data-stu-id="9d845-185">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="9d845-186">`Type.GetType("MyArray[*]")`bilinmeyen alt sınır içeren tek boyutlu bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="9d845-186">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="9d845-187">`Type.GetType("MyArray[][]")`iki boyutlu bir dizinin dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="9d845-187">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="9d845-188">`Type.GetType("MyArray[*,*]")`ve `Type.GetType("MyArray[,]")` bilinmeyen alt sınırlara sahip dikdörtgen iki boyutlu bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="9d845-188">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="9d845-189">Bir çalışma zamanı noktasından, ancak çok boyutlu diziler `MyArray[] != MyArray[*]`için iki gösterimin eşdeğer olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d845-189">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="9d845-190">Yani, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` **true**olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d845-190">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="9d845-191">**ModuleBuilder. GetType**için, `MyArray[0..5]` 6 boyutunda bir tek boyutlu diziyi, alt sınır 0 ' ı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d845-191">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="9d845-192">`MyArray[4…]`Bilinmeyen boyut ve alt sınır 4 ' ün tek boyutlu dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d845-192">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d845-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d845-193">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9d845-194">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="9d845-194">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
