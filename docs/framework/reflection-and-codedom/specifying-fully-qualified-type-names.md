---
title: Tam Olarak Nitelenmiş Tür Adlarını Belirtme
ms.date: 03/14/2018
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
ms.openlocfilehash: 437bbb7a1645c0ab13da33e57c1e70b5ec98984c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398684"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="84974-102">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="84974-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="84974-103">Tür adları çeşitli yansıma işlemleri için geçerli giriş belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84974-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="84974-104">Tam olarak nitelenmiş tür adını bir derleme adı belirtimi, bir ad alanı belirtimi ve tür adı oluşur.</span><span class="sxs-lookup"><span data-stu-id="84974-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="84974-105">Tür adı belirtimleri kullanılan yöntemler tarafından gibi <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84974-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="grammar-for-type-names"></a><span data-ttu-id="84974-106">Tür adları için dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="84974-106">Grammar for Type Names</span></span>  
 <span data-ttu-id="84974-107">Dilbilgisi resmi diller sözdizimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84974-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="84974-108">Aşağıdaki tabloda, geçerli bir giriş tanımak açıklar sözcük kuralları listeler.</span><span class="sxs-lookup"><span data-stu-id="84974-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="84974-109">Terminal (daha fazla reducible olmayan bu öğeleri) tüm büyük harflerle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="84974-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="84974-110">Terminal dışı (daha fazla reducible bu öğeleri) harf karışık veya tek tırnak içine alınmış dizeler gösterilir, ancak tek tırnak işareti (') sözdizimi bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="84974-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="84974-111">Dikey çizgi karakterinden (&#124;) alt kurallar sahip kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="84974-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  

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
    | ArrayTypeSpec
    | TypeName
    ;

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

## <a name="specifying-special-characters"></a><span data-ttu-id="84974-112">Özel karakterler belirtme</span><span class="sxs-lookup"><span data-stu-id="84974-112">Specifying Special Characters</span></span>  
 <span data-ttu-id="84974-113">Bir tür adı bir dil kuralları tarafından belirlenen geçerli bir ad tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="84974-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="84974-114">Ters eğik çizgi kullanın (\\) TANIMLAYICI bir parçası olarak kullanıldığında aşağıdaki belirteçleri ayırmak için çıkış karakteri olarak.</span><span class="sxs-lookup"><span data-stu-id="84974-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="84974-115">Belirteç</span><span class="sxs-lookup"><span data-stu-id="84974-115">Token</span></span>|<span data-ttu-id="84974-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84974-116">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="84974-117">\\,</span><span class="sxs-lookup"><span data-stu-id="84974-117">\\,</span></span>|<span data-ttu-id="84974-118">Derleme ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="84974-118">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="84974-119">İç içe geçmiş tür ayırıcısı.</span><span class="sxs-lookup"><span data-stu-id="84974-119">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="84974-120">Başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="84974-120">Reference type.</span></span>|  
|\\*|<span data-ttu-id="84974-121">İşaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="84974-121">Pointer type.</span></span>|  
|<span data-ttu-id="84974-122">\\[</span><span class="sxs-lookup"><span data-stu-id="84974-122">\\[</span></span>|<span data-ttu-id="84974-123">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="84974-123">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="84974-124">\\]</span><span class="sxs-lookup"><span data-stu-id="84974-124">\\]</span></span>|<span data-ttu-id="84974-125">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="84974-125">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="84974-126">\\.</span><span class="sxs-lookup"><span data-stu-id="84974-126">\\.</span></span>|<span data-ttu-id="84974-127">Yalnızca bir dizi belirtimi dönem kullanılıyorsa bir süre önce ters eğik çizgi kullanın.</span><span class="sxs-lookup"><span data-stu-id="84974-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="84974-128">NamespaceSpec dönemlerini ters eğik çizgi kazanmaz.</span><span class="sxs-lookup"><span data-stu-id="84974-128">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|<span data-ttu-id="84974-129">\\\|Bir dize olarak değişmez değer gerektiğinde ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="84974-129">\\\|Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="84974-130">AssemblyNameSpec dışındaki tüm TypeSpec'te bileşenlerinde alanları ilgili olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="84974-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="84974-131">AssemblyNameSpec ',' ayırıcıdan önce alanları ilgilidir, ancak ',' ayırıcı sonra boşluklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="84974-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="84974-132">Yansıma sınıfları, gibi <xref:System.Type.FullName%2A?displayProperty=nameWithType>, böylece döndürülen adını çağrıda kullanılabilir karıştırılmış adını döndürmek <xref:System.Type.GetType%2A>, olarak `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="84974-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="84974-133">Örneğin, bir tür için tam ad olabilir `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="84974-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="84974-134">Ad alanı olsaydı `Ozzy.Out+Back`, sonra da artı bir eğik gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="84974-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="84974-135">Aksi takdirde, ayrıştırıcı, iç içe geçmiş ayırıcı olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="84974-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="84974-136">Yansıma yayar Bu dize olarak `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="84974-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="84974-137">Derleme adları belirtme</span><span class="sxs-lookup"><span data-stu-id="84974-137">Specifying Assembly Names</span></span>  
 <span data-ttu-id="84974-138">Bir derleme adı belirtiminde gerekli en az bilgiyi metinsel (TANIMLAYICI) derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="84974-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="84974-139">Aşağıdaki tabloda açıklandığı şekilde özellik/değer çifti virgülle ayrılmış listesi TANIMLAYICISI izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84974-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="84974-140">TANIMLAYICI adlandırma dosya adlandırma kuralları izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="84974-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="84974-141">TANIMLAYICI büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="84974-141">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="84974-142">Özellik adı</span><span class="sxs-lookup"><span data-stu-id="84974-142">Property name</span></span>|<span data-ttu-id="84974-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84974-143">Description</span></span>|<span data-ttu-id="84974-144">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="84974-144">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="84974-145">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="84974-145">**Version**</span></span>|<span data-ttu-id="84974-146">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="84974-146">Assembly version number</span></span>|<span data-ttu-id="84974-147">*Major.Minor.Build.Revision*, burada *ana*, *küçük*, *yapı*, ve *düzeltme* 0 arasında tamsayı olan ve 65535 (dahil).</span><span class="sxs-lookup"><span data-stu-id="84974-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="84974-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="84974-148">**PublicKey**</span></span>|<span data-ttu-id="84974-149">Tam ortak anahtar</span><span class="sxs-lookup"><span data-stu-id="84974-149">Full public key</span></span>|<span data-ttu-id="84974-150">Onaltılık biçimde tam ortak anahtarın değerini dize.</span><span class="sxs-lookup"><span data-stu-id="84974-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="84974-151">Bir null başvuru belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="84974-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="84974-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="84974-152">**PublicKeyToken**</span></span>|<span data-ttu-id="84974-153">Ortak anahtar belirteci (tam ortak anahtarı karmasını 8-bayt)</span><span class="sxs-lookup"><span data-stu-id="84974-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="84974-154">Dize değeri, onaltılık biçimde ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="84974-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="84974-155">Bir null başvuru belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="84974-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="84974-156">**Kültür**</span><span class="sxs-lookup"><span data-stu-id="84974-156">**Culture**</span></span>|<span data-ttu-id="84974-157">Derleme kültür</span><span class="sxs-lookup"><span data-stu-id="84974-157">Assembly culture</span></span>|<span data-ttu-id="84974-158">RFC 1766 biçimi veya dilden bağımsız (nonsatellite) derlemeler için "nötr" derlemesinde kültür.</span><span class="sxs-lookup"><span data-stu-id="84974-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="84974-159">**Özel**</span><span class="sxs-lookup"><span data-stu-id="84974-159">**Custom**</span></span>|<span data-ttu-id="84974-160">Özel ikili büyük nesne (BLOB).</span><span class="sxs-lookup"><span data-stu-id="84974-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="84974-161">Bu şu anda yalnızca tarafından oluşturulan derlemelerde kullanılır [yerel Görüntü Oluşturucu (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="84974-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="84974-162">Yerel Görüntü Oluşturucu aracı tarafından Derleme Önbelleği yüklenen derleme yerel görüntü ve bu nedenle yerel görüntü Önbelleği'yüklenecek olduğunu bildirmek için kullanılan özel bir dize.</span><span class="sxs-lookup"><span data-stu-id="84974-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="84974-163">Bir zap dize olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="84974-163">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="84974-164">Aşağıdaki örnekte gösterildiği bir **AssemblyName** varsayılan kültürü yalnızca adlandırılmış bir derleme için.</span><span class="sxs-lookup"><span data-stu-id="84974-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="84974-165">Aşağıdaki örnek kültür "tr" kesin adlandırılmış bir derleme tam olarak belirtilen bir başvuru gösterir.</span><span class="sxs-lookup"><span data-stu-id="84974-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="84974-166">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi memnun güçlü bir ya da yalnızca adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="84974-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="84974-167">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından yalnızca adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="84974-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="84974-168">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından kesin adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="84974-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="84974-169">İşaretçileri belirtme</span><span class="sxs-lookup"><span data-stu-id="84974-169">Specifying Pointers</span></span>  
 <span data-ttu-id="84974-170">SimpleTypeSpec \* bir yönetilmeyen işaretçi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84974-170">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="84974-171">Örneğin, MyType yazmanız için bir işaretçi almak için kullanın `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="84974-171">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="84974-172">Bir işaretçi MyType yazmanız için bir işaretçi almak için `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="84974-172">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="84974-173">Başvuruları belirtme</span><span class="sxs-lookup"><span data-stu-id="84974-173">Specifying References</span></span>  
 <span data-ttu-id="84974-174">SimpleTypeSpec & Yönetilen işaretçi veya reference temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84974-174">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="84974-175">Örneğin, MyType yazmanız için bir başvuru almak için kullanın `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="84974-175">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="84974-176">İşaretçileri, başvuru bir düzey sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="84974-176">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="84974-177">Diziler belirtme</span><span class="sxs-lookup"><span data-stu-id="84974-177">Specifying Arrays</span></span>  
 <span data-ttu-id="84974-178">BNF dilbilgisi ReflectionEmitDimension yalnızca kullanarak alınan tamamlanmamış tür tanımları için geçerlidir. <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84974-178">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84974-179">Tamamlanmamış türü tanımlarının <xref:System.Reflection.Emit.TypeBuilder> kullanılarak oluşturulan nesneler <xref:System.Reflection.Emit?displayProperty=nameWithType> ancak üretileceği <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="84974-179">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="84974-180">ReflectionDimension, yani tamamlanmış herhangi bir tür tanımı, yüklenmiş bir türü almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84974-180">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="84974-181">Diziler, dizi derecesini belirterek yansıma erişilen:</span><span class="sxs-lookup"><span data-stu-id="84974-181">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="84974-182">`Type.GetType("MyArray[]")` 0 alt sınır olan tek boyutlu dizi alır.</span><span class="sxs-lookup"><span data-stu-id="84974-182">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="84974-183">`Type.GetType("MyArray[*]")` Bilinmeyen alt sınır olan tek boyutlu dizi alır.</span><span class="sxs-lookup"><span data-stu-id="84974-183">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="84974-184">`Type.GetType("MyArray[][]")` iki boyutlu bir dizinin dizi alır.</span><span class="sxs-lookup"><span data-stu-id="84974-184">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="84974-185">`Type.GetType("MyArray[*,*]")` ve `Type.GetType("MyArray[,]")` dikdörtgen iki boyutlu bir dizi Bilinmeyen alt sınırlarını ile alır.</span><span class="sxs-lookup"><span data-stu-id="84974-185">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="84974-186">Bir çalışma zamanı açısından bakıldığında, unutmayın `MyArray[] != MyArray[*]`, ancak çok boyutlu diziler için iki gösterimler eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="84974-186">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="84974-187">Diğer bir deyişle, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` değerlendiren **doğru**.</span><span class="sxs-lookup"><span data-stu-id="84974-187">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="84974-188">İçin **ModuleBuilder.GetType**, `MyArray[0..5]` boyutu 6, daha düşük olan tek boyutlu dizi bağlı 0 gösterir.</span><span class="sxs-lookup"><span data-stu-id="84974-188">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="84974-189">`MyArray[4…]` Bilinmeyen boyutu ve alt sınır 4 tek boyutlu dizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="84974-189">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84974-190">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84974-190">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="84974-191">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="84974-191">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
