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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793009"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="aa6f0-102">Tam olarak nitelenmiş tür adlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-102">Specifying fully qualified type names</span></span>

<span data-ttu-id="aa6f0-103">Çeşitli yansıma işlemleri için geçerli bir giriş için tür adları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="aa6f0-104">Bir derleme adı belirtimi, bir ad alanı belirtimine ve bir tür adı tam olarak nitelenmiş tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="aa6f0-105">Tür adı belirtimleri kullanılan yöntemleri tarafından gibi <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="aa6f0-106">Tür adları için dil bilgisi</span><span class="sxs-lookup"><span data-stu-id="aa6f0-106">Grammar for type names</span></span>

 <span data-ttu-id="aa6f0-107">Dilbilgisi biçimsel dillerin sözdizimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="aa6f0-108">Aşağıdaki tabloda, geçerli bir giriş anlamayı açıklayan sözcük temelli kurallar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="aa6f0-109">Tüm büyük harfleri terminaller (daha fazla reducible olmayan bu öğeleri) gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="aa6f0-110">Terminal olmayanları (daha fazla reducible bu öğeleri) karışık veya tek tırnak içine alınmış dizeler gösterilir, ancak tek tırnak (') sözdizimi bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="aa6f0-111">Dikey çizgi karakterinden (&#124;) alt olan kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>

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

## <a name="specifying-special-characters"></a><span data-ttu-id="aa6f0-112">Özel karakter belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-112">Specifying special characters</span></span>

<span data-ttu-id="aa6f0-113">Bir tür adı bir dil kuralları tarafından belirlenen geçerli bir ad tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="aa6f0-114">Ters eğik çizgi kullanın (\\) olarak TANIMLAYICI bir parçası olarak kullanıldığında aşağıdaki belirteçler ayırmak için bir kaçış karakteri.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="aa6f0-115">Belirteç</span><span class="sxs-lookup"><span data-stu-id="aa6f0-115">Token</span></span>|<span data-ttu-id="aa6f0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa6f0-116">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="aa6f0-117">\\,</span><span class="sxs-lookup"><span data-stu-id="aa6f0-117">\\,</span></span>|<span data-ttu-id="aa6f0-118">Derleme ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-118">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="aa6f0-119">İç içe geçmiş tür ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-119">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="aa6f0-120">Başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-120">Reference type.</span></span>|
|\\*|<span data-ttu-id="aa6f0-121">İşaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-121">Pointer type.</span></span>|
|<span data-ttu-id="aa6f0-122">\\[</span><span class="sxs-lookup"><span data-stu-id="aa6f0-122">\\[</span></span>|<span data-ttu-id="aa6f0-123">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-123">Array dimension delimiter.</span></span>|
|<span data-ttu-id="aa6f0-124">\\]</span><span class="sxs-lookup"><span data-stu-id="aa6f0-124">\\]</span></span>|<span data-ttu-id="aa6f0-125">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-125">Array dimension delimiter.</span></span>|
|<span data-ttu-id="aa6f0-126">\\.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-126">\\.</span></span>|<span data-ttu-id="aa6f0-127">Yalnızca nokta bir dizi belirtiminde kullanılıyorsa bir süre önce ters eğik çizgi kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="aa6f0-128">Ters eğik çizgi NamespaceSpec dönemlerde almaz.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-128">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="aa6f0-129">\\\|Değişmez değer dize olarak gerektiğinde ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-129">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="aa6f0-130">Alanları AssemblyNameSpec dışındaki tüm TypeSpec'te bileşenlerinde ilgili olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="aa6f0-131">AssemblyNameSpec ',' ayırıcısından önceki boşluklar ilgilidir, ancak ',' ayırıcısından sonraki boşluklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="aa6f0-132">Yansıma sınıfları, gibi <xref:System.Type.FullName%2A?displayProperty=nameWithType>, böylece bir çağrıda döndürülen adını kullanılabilir karıştırılmış adını döndürmek <xref:System.Type.GetType%2A>, olarak `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="aa6f0-133">Örneğin, bir tür için tam ad olabilir `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="aa6f0-134">Ad alanı varsa `Ozzy.Out+Back`, ardından artı işaretine bir ters eğik çizgi gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="aa6f0-135">Aksi takdirde, ayrıştırıcının, iç içe geçmiş bir ayırıcı olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="aa6f0-136">Yansıma Bu dize olarak yayar `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="aa6f0-137">Derleme adları belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-137">Specifying assembly names</span></span>

<span data-ttu-id="aa6f0-138">Bir derleme adı belirtimi gereken en düşük bilgileri metinsel (TANIMLAYICI) derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="aa6f0-139">Aşağıdaki tabloda açıklandığı gibi özellik/değer çiftlerinin virgülle ayrılmış bir listesini, TANIMLAYICI takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="aa6f0-140">TANIMLAYICI adlandırma dosya adlandırma kuralları izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="aa6f0-141">TANIMLAYICI büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-141">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="aa6f0-142">Özellik adı</span><span class="sxs-lookup"><span data-stu-id="aa6f0-142">Property name</span></span>|<span data-ttu-id="aa6f0-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa6f0-143">Description</span></span>|<span data-ttu-id="aa6f0-144">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="aa6f0-144">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="aa6f0-145">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="aa6f0-145">**Version**</span></span>|<span data-ttu-id="aa6f0-146">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="aa6f0-146">Assembly version number</span></span>|<span data-ttu-id="aa6f0-147">*Major.Minor.Build.Revision*burada *ana*, *küçük*, *derleme*, ve *düzeltme* 0 arasındaki tam sayılardır ve 65535 (dahil).</span><span class="sxs-lookup"><span data-stu-id="aa6f0-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="aa6f0-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="aa6f0-148">**PublicKey**</span></span>|<span data-ttu-id="aa6f0-149">Tam ortak anahtarı</span><span class="sxs-lookup"><span data-stu-id="aa6f0-149">Full public key</span></span>|<span data-ttu-id="aa6f0-150">Onaltılık biçimde tam ortak anahtar dizesi.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="aa6f0-151">Bir null başvurusu belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="aa6f0-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="aa6f0-152">**PublicKeyToken**</span></span>|<span data-ttu-id="aa6f0-153">Ortak anahtar belirteci (8 baytlık tam ortak anahtar karması)</span><span class="sxs-lookup"><span data-stu-id="aa6f0-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="aa6f0-154">Onaltılık biçiminde ortak anahtar belirteci dizesi.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="aa6f0-155">Bir null başvurusu belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="aa6f0-156">**Kültür**</span><span class="sxs-lookup"><span data-stu-id="aa6f0-156">**Culture**</span></span>|<span data-ttu-id="aa6f0-157">Derleme kültürü</span><span class="sxs-lookup"><span data-stu-id="aa6f0-157">Assembly culture</span></span>|<span data-ttu-id="aa6f0-158">RFC 1766 biçimi veya "belirsiz" dilden bağımsız (nonsatellite) derlemeler için derleme kültür.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="aa6f0-159">**Özel**</span><span class="sxs-lookup"><span data-stu-id="aa6f0-159">**Custom**</span></span>|<span data-ttu-id="aa6f0-160">Özel ikili büyük nesne (BLOB).</span><span class="sxs-lookup"><span data-stu-id="aa6f0-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="aa6f0-161">Bu şu anda yalnızca tarafından oluşturulan bütünleştirilmiş kodlarında kullanılır [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="aa6f0-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="aa6f0-162">Yerel Görüntü Oluşturucu aracı tarafından derleme önbelleğine yüklenen derleme bir doğal görüntü ve bu nedenle yerel görüntü önbelleğine yüklenecek olduğunu bildirmek için kullanılan özel bir dize.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="aa6f0-163">Zap dize olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-163">Also called a zap string.</span></span>|

<span data-ttu-id="aa6f0-164">Aşağıdaki örnekte gösterildiği bir **AssemblyName** varsayılan kültür ile yalnızca adlandırılmış bir derleme için.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="aa6f0-165">Aşağıdaki örnek, "en" kültürüyle kesin adlandırılmış bir bütünleştirilmiş kod için tam olarak belirtilen bir başvuru gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="aa6f0-166">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi memnun güçlü veya yalnızca adlandırılmış bir bütünleştirilmiş kod tarafından.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="aa6f0-167">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından yalnızca adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="aa6f0-168">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun kesin adlandırılmış bir derleme tarafından.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="aa6f0-169">Genel türleri belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-169">Specifying generic types</span></span>

<span data-ttu-id="aa6f0-170">SimpleTypeSpec\`SAYIYI temsil eden bir açık genel tür ile 1'den *n* genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-170">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="aa6f0-171">Örneğin, başvuru açık genel tür listesini almak için\<T > ya da kapalı genel tür listesi\<dizesi >, kullanın ``Type.GetType("System.Collections.Generic.List`1")`` genel tür sözlük için bir başvuru almak için\<TKey, TValue >, kullanın ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-171">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="aa6f0-172">İşaretçileri belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-172">Specifying pointers</span></span>

<span data-ttu-id="aa6f0-173">SimpleTypeSpec \* bir yönetilmeyen işaretçi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-173">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="aa6f0-174">Örneğin, MyType tür işaretçisi almak için kullanın `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-174">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="aa6f0-175">MyType tür işaretçisi için bir işaretçi almak için kullanın `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-175">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="aa6f0-176">Başvuruları belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-176">Specifying references</span></span>

<span data-ttu-id="aa6f0-177">SimpleTypeSpec & bir yönetilen işaretçi veya başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-177">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="aa6f0-178">Örneğin, MyType yazmanız için bir başvuru almak için kullanın `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-178">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="aa6f0-179">İşaretçilerin, başvuru bir düzey sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-179">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="aa6f0-180">Diziler belirtme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-180">Specifying arrays</span></span>

<span data-ttu-id="aa6f0-181">BNF dilbilgisi ReflectionEmitDimension eksik tür tanımlarını kullanarak yalnızca geçerli <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-181">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aa6f0-182">Eksik tür tanımları <xref:System.Reflection.Emit.TypeBuilder> kullanılarak oluşturulan nesneleri <xref:System.Reflection.Emit?displayProperty=nameWithType> ancak üretileceği <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-182">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="aa6f0-183">ReflectionDimension, yani tamamlanmış olan herhangi bir tür tanımı, yüklenmiş olan bir tür almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-183">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="aa6f0-184">Diziler, dizi boyut sayısını belirterek yansıma erişilir:</span><span class="sxs-lookup"><span data-stu-id="aa6f0-184">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="aa6f0-185">`Type.GetType("MyArray[]")` bir tek boyutlu dizi alt sınırı 0 ile alır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-185">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="aa6f0-186">`Type.GetType("MyArray[*]")` Bilinmeyen alt sınır olan bir tek boyutlu dizi alır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-186">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="aa6f0-187">`Type.GetType("MyArray[][]")` iki boyutlu bir dizinin dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-187">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="aa6f0-188">`Type.GetType("MyArray[*,*]")` ve `Type.GetType("MyArray[,]")` dikdörtgen iki boyutlu bir dizi ile Bilinmeyen alt sınırını alır.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-188">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="aa6f0-189">Bir çalışma zamanı açısından bakıldığında, dikkat `MyArray[] != MyArray[*]`, ancak çok boyutlu diziler için iki gösterimler eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-189">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="aa6f0-190">Diğer bir deyişle, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` değerlendiren **true**.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-190">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="aa6f0-191">İçin **ModuleBuilder.GetType**, `MyArray[0..5]` bir tek boyutlu dizi boyutu 6, daha düşük ile bağlı 0 gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-191">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="aa6f0-192">`MyArray[4…]` bir tek boyutlu dizi boyutu bilinmeyen ve alt sınırı 4 gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-192">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa6f0-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa6f0-193">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aa6f0-194">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="aa6f0-194">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
