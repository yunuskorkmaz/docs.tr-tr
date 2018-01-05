---
title: "Tam Olarak Nitelenmiş Tür Adlarını Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e19aebbeee7fd65e27704af49185a1b8d48b9639
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="6e346-102">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="6e346-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="6e346-103">Tür adları çeşitli yansıma işlemleri için geçerli giriş belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e346-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="6e346-104">Tam olarak nitelenmiş tür adını bir derleme adı belirtimi, bir ad alanı belirtimi ve tür adı oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e346-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="6e346-105">Tür adı belirtimleri kullanılan yöntemler tarafından gibi <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e346-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="backus-naur-form-grammar-for-type-names"></a><span data-ttu-id="6e346-106">Tür adları için Backus-Naur formu dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="6e346-106">Backus-Naur Form Grammar for Type Names</span></span>  
 <span data-ttu-id="6e346-107">Backus-Naur formu (BNF) resmi diller sözdizimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e346-107">The Backus-Naur form (BNF) defines the syntax of formal languages.</span></span> <span data-ttu-id="6e346-108">Aşağıdaki tabloda, geçerli bir giriş tanımak nasıl açıklayan BNF sözcük kuralları listeler.</span><span class="sxs-lookup"><span data-stu-id="6e346-108">The following table lists BNF lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="6e346-109">Terminal (daha fazla reducible olmayan bu öğeleri) tüm büyük harflerle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6e346-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="6e346-110">Terminal dışı (daha fazla reducible bu öğeleri) harf karışık veya tek tırnak içine alınmış dizeler gösterilir, ancak tek tırnak işareti (') sözdizimi bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="6e346-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="6e346-111">Dikey çizgi karakterinden (&#124;) alt kurallar sahip kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e346-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  
  
|<span data-ttu-id="6e346-112">BNF dilbilgisi tam olarak nitelenmiş tür adları</span><span class="sxs-lookup"><span data-stu-id="6e346-112">BNF grammar of fully qualified type names</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="6e346-113">TypeSpec'te: ReferenceTypeSpec =</span><span class="sxs-lookup"><span data-stu-id="6e346-113">TypeSpec                          :=   ReferenceTypeSpec</span></span><br /><br /> <span data-ttu-id="6e346-114">&#124;     SimpleTypeSpec</span><span class="sxs-lookup"><span data-stu-id="6e346-114">&#124;     SimpleTypeSpec</span></span>|  
|<span data-ttu-id="6e346-115">ReferenceTypeSpec: SimpleTypeSpec = '&'</span><span class="sxs-lookup"><span data-stu-id="6e346-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span></span>|  
|<span data-ttu-id="6e346-116">SimpleTypeSpec: PointerTypeSpec =</span><span class="sxs-lookup"><span data-stu-id="6e346-116">SimpleTypeSpec                :=   PointerTypeSpec</span></span><br /><br /> <span data-ttu-id="6e346-117">&#124;     ArrayTypeSpec</span><span class="sxs-lookup"><span data-stu-id="6e346-117">&#124;     ArrayTypeSpec</span></span><br /><br /> <span data-ttu-id="6e346-118">&#124;     TypeName</span><span class="sxs-lookup"><span data-stu-id="6e346-118">&#124;     TypeName</span></span>|  
|<span data-ttu-id="6e346-119">PointerTypeSpec: SimpleTypeSpec = ' *'</span><span class="sxs-lookup"><span data-stu-id="6e346-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span></span>|  
|<span data-ttu-id="6e346-120">ArrayTypeSpec: '[ReflectionDimension]' SimpleTypeSpec =</span><span class="sxs-lookup"><span data-stu-id="6e346-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span></span><br /><br /> <span data-ttu-id="6e346-121">&#124;     SimpleTypeSpec [ReflectionEmitDimension]</span><span class="sxs-lookup"><span data-stu-id="6e346-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span></span>|  
|<span data-ttu-id="6e346-122">ReflectionDimension: = ' *'</span><span class="sxs-lookup"><span data-stu-id="6e346-122">ReflectionDimension           :=   '*'</span></span><br /><br /> <span data-ttu-id="6e346-123">&#124;     ReflectionDimension ',' ReflectionDimension</span><span class="sxs-lookup"><span data-stu-id="6e346-123">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="6e346-124">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="6e346-124">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="6e346-125">ReflectionEmitDimension: = ' *'</span><span class="sxs-lookup"><span data-stu-id="6e346-125">ReflectionEmitDimension    :=   '*'</span></span><br /><br /> <span data-ttu-id="6e346-126">&#124;     Sayı '..'</span><span class="sxs-lookup"><span data-stu-id="6e346-126">&#124;     Number '..'</span></span> <span data-ttu-id="6e346-127">Sayı</span><span class="sxs-lookup"><span data-stu-id="6e346-127">Number</span></span><br /><br /> <span data-ttu-id="6e346-128">&#124;     Sayı '...'</span><span class="sxs-lookup"><span data-stu-id="6e346-128">&#124;     Number '…'</span></span><br /><br /> <span data-ttu-id="6e346-129">&#124;     ReflectionDimension ',' ReflectionDimension</span><span class="sxs-lookup"><span data-stu-id="6e346-129">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="6e346-130">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="6e346-130">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="6e346-131">Sayı: = [0-9] +</span><span class="sxs-lookup"><span data-stu-id="6e346-131">Number                            :=   [0-9]+</span></span>|  
|<span data-ttu-id="6e346-132">TypeName: NamespaceTypeName =</span><span class="sxs-lookup"><span data-stu-id="6e346-132">TypeName                         :=   NamespaceTypeName</span></span><br /><br /> <span data-ttu-id="6e346-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span><span class="sxs-lookup"><span data-stu-id="6e346-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span></span>|  
|<span data-ttu-id="6e346-134">NamespaceTypeName: NestedTypeName =</span><span class="sxs-lookup"><span data-stu-id="6e346-134">NamespaceTypeName        :=   NestedTypeName</span></span><br /><br /> <span data-ttu-id="6e346-135">&#124;     NamespaceSpec '.' NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="6e346-135">&#124;     NamespaceSpec '.' NestedTypeName</span></span>|  
|<span data-ttu-id="6e346-136">NestedTypeName: TANITICISI =</span><span class="sxs-lookup"><span data-stu-id="6e346-136">NestedTypeName               :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="6e346-137">&#124;     NestedTypeName '+' TANIMLAYICISI</span><span class="sxs-lookup"><span data-stu-id="6e346-137">&#124;     NestedTypeName '+' IDENTIFIER</span></span>|  
|<span data-ttu-id="6e346-138">NamespaceSpec: TANITICISI =</span><span class="sxs-lookup"><span data-stu-id="6e346-138">NamespaceSpec                 :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="6e346-139">&#124;     NamespaceSpec '.' TANIMLAYICI</span><span class="sxs-lookup"><span data-stu-id="6e346-139">&#124;     NamespaceSpec '.' IDENTIFIER</span></span>|  
|<span data-ttu-id="6e346-140">AssemblyNameSpec: TANITICISI =</span><span class="sxs-lookup"><span data-stu-id="6e346-140">AssemblyNameSpec           :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="6e346-141">&#124;     TANIMLAYICI ',' AssemblyProperties</span><span class="sxs-lookup"><span data-stu-id="6e346-141">&#124;     IDENTIFIER ',' AssemblyProperties</span></span>|  
|<span data-ttu-id="6e346-142">AssemblyProperties: AssemblyProperty =</span><span class="sxs-lookup"><span data-stu-id="6e346-142">AssemblyProperties            :=   AssemblyProperty</span></span><br /><br /> <span data-ttu-id="6e346-143">&#124;     AssemblyProperties ',' AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="6e346-143">&#124;     AssemblyProperties ',' AssemblyProperty</span></span>|  
|<span data-ttu-id="6e346-144">AssemblyProperty: AssemblyPropertyName '=' AssemblyPropertyValue =</span><span class="sxs-lookup"><span data-stu-id="6e346-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span></span>|  
  
## <a name="specifying-special-characters"></a><span data-ttu-id="6e346-145">Özel karakterler belirtme</span><span class="sxs-lookup"><span data-stu-id="6e346-145">Specifying Special Characters</span></span>  
 <span data-ttu-id="6e346-146">Bir tür adı bir dil kuralları tarafından belirlenen geçerli bir ad tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="6e346-146">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="6e346-147">Ters eğik çizgi kullanın (\\) TANIMLAYICI bir parçası olarak kullanıldığında aşağıdaki belirteçleri ayırmak için çıkış karakteri olarak.</span><span class="sxs-lookup"><span data-stu-id="6e346-147">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="6e346-148">Belirteç</span><span class="sxs-lookup"><span data-stu-id="6e346-148">Token</span></span>|<span data-ttu-id="6e346-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e346-149">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="6e346-150">\\,</span><span class="sxs-lookup"><span data-stu-id="6e346-150">\\,</span></span>|<span data-ttu-id="6e346-151">Derleme ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="6e346-151">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="6e346-152">İç içe geçmiş tür ayırıcısı.</span><span class="sxs-lookup"><span data-stu-id="6e346-152">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="6e346-153">Başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="6e346-153">Reference type.</span></span>|  
|\\*|<span data-ttu-id="6e346-154">İşaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="6e346-154">Pointer type.</span></span>|  
|<span data-ttu-id="6e346-155">\\[</span><span class="sxs-lookup"><span data-stu-id="6e346-155">\\[</span></span>|<span data-ttu-id="6e346-156">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6e346-156">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="6e346-157">\\]</span><span class="sxs-lookup"><span data-stu-id="6e346-157">\\]</span></span>|<span data-ttu-id="6e346-158">Dizi boyut sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6e346-158">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="6e346-159">\\.</span><span class="sxs-lookup"><span data-stu-id="6e346-159">\\.</span></span>|<span data-ttu-id="6e346-160">Yalnızca bir dizi belirtimi dönem kullanılıyorsa bir süre önce ters eğik çizgi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e346-160">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="6e346-161">NamespaceSpec dönemlerini ters eğik çizgi kazanmaz.</span><span class="sxs-lookup"><span data-stu-id="6e346-161">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|\\\|<span data-ttu-id="6e346-162">Bir dize olarak değişmez değer gerektiğinde ters eğik çizgi.</span><span class="sxs-lookup"><span data-stu-id="6e346-162">Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="6e346-163">AssemblyNameSpec dışındaki tüm TypeSpec'te bileşenlerinde alanları ilgili olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e346-163">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="6e346-164">AssemblyNameSpec ',' ayırıcıdan önce alanları ilgilidir, ancak ',' ayırıcı sonra boşluklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="6e346-164">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="6e346-165">Yansıma sınıfları, gibi <xref:System.Type.FullName%2A?displayProperty=nameWithType>, böylece döndürülen adını çağrıda kullanılabilir karıştırılmış adını döndürmek <xref:System.Type.GetType%2A>, olarak `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="6e346-165">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="6e346-166">Örneğin, bir tür için tam ad olabilir `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="6e346-166">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="6e346-167">Ad alanı olsaydı `Ozzy.Out+Back`, sonra da artı bir eğik gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e346-167">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="6e346-168">Aksi takdirde, ayrıştırıcı, iç içe geçmiş ayırıcı olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="6e346-168">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="6e346-169">Yansıma yayar Bu dize olarak `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="6e346-169">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="6e346-170">Derleme adları belirtme</span><span class="sxs-lookup"><span data-stu-id="6e346-170">Specifying Assembly Names</span></span>  
 <span data-ttu-id="6e346-171">Bir derleme adı belirtiminde gerekli en az bilgiyi metinsel (TANIMLAYICI) derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="6e346-171">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="6e346-172">Aşağıdaki tabloda açıklandığı şekilde özellik/değer çifti virgülle ayrılmış listesi TANIMLAYICISI izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e346-172">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="6e346-173">TANIMLAYICI adlandırma dosya adlandırma kuralları izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="6e346-173">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="6e346-174">TANIMLAYICI büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e346-174">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="6e346-175">Özellik adı</span><span class="sxs-lookup"><span data-stu-id="6e346-175">Property name</span></span>|<span data-ttu-id="6e346-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e346-176">Description</span></span>|<span data-ttu-id="6e346-177">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="6e346-177">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="6e346-178">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="6e346-178">**Version**</span></span>|<span data-ttu-id="6e346-179">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="6e346-179">Assembly version number</span></span>|<span data-ttu-id="6e346-180">*Major.Minor.Build.Revision*, burada *ana*, *küçük*, *yapı*, ve *düzeltme* 0 arasında tamsayı olan ve 65535 (dahil).</span><span class="sxs-lookup"><span data-stu-id="6e346-180">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="6e346-181">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="6e346-181">**PublicKey**</span></span>|<span data-ttu-id="6e346-182">Tam ortak anahtar</span><span class="sxs-lookup"><span data-stu-id="6e346-182">Full public key</span></span>|<span data-ttu-id="6e346-183">Onaltılık biçimde tam ortak anahtarın değerini dize.</span><span class="sxs-lookup"><span data-stu-id="6e346-183">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="6e346-184">Bir null başvuru belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6e346-184">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="6e346-185">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="6e346-185">**PublicKeyToken**</span></span>|<span data-ttu-id="6e346-186">Ortak anahtar belirteci (tam ortak anahtarı karmasını 8-bayt)</span><span class="sxs-lookup"><span data-stu-id="6e346-186">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="6e346-187">Dize değeri, onaltılık biçimde ortak anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="6e346-187">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="6e346-188">Bir null başvuru belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6e346-188">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="6e346-189">**Kültür**</span><span class="sxs-lookup"><span data-stu-id="6e346-189">**Culture**</span></span>|<span data-ttu-id="6e346-190">Derleme kültür</span><span class="sxs-lookup"><span data-stu-id="6e346-190">Assembly culture</span></span>|<span data-ttu-id="6e346-191">RFC 1766 biçimi veya dilden bağımsız (nonsatellite) derlemeler için "nötr" derlemesinde kültür.</span><span class="sxs-lookup"><span data-stu-id="6e346-191">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="6e346-192">**Özel**</span><span class="sxs-lookup"><span data-stu-id="6e346-192">**Custom**</span></span>|<span data-ttu-id="6e346-193">Özel ikili büyük nesne (BLOB).</span><span class="sxs-lookup"><span data-stu-id="6e346-193">Custom binary large object (BLOB).</span></span> <span data-ttu-id="6e346-194">Bu şu anda yalnızca tarafından oluşturulan derlemelerde kullanılır [yerel Görüntü Oluşturucu (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="6e346-194">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="6e346-195">Yerel Görüntü Oluşturucu aracı tarafından Derleme Önbelleği yüklenen derleme yerel görüntü ve bu nedenle yerel görüntü Önbelleği'yüklenecek olduğunu bildirmek için kullanılan özel bir dize.</span><span class="sxs-lookup"><span data-stu-id="6e346-195">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="6e346-196">Bir zap dize olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="6e346-196">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="6e346-197">Aşağıdaki örnekte gösterildiği bir **AssemblyName** varsayılan kültürü yalnızca adlandırılmış bir derleme için.</span><span class="sxs-lookup"><span data-stu-id="6e346-197">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="6e346-198">Aşağıdaki örnek kültür "tr" kesin adlandırılmış bir derleme tam olarak belirtilen bir başvuru gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e346-198">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="6e346-199">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi memnun güçlü bir ya da yalnızca adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="6e346-199">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="6e346-200">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından yalnızca adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="6e346-200">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="6e346-201">Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından kesin adlandırılmış bir derleme.</span><span class="sxs-lookup"><span data-stu-id="6e346-201">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="6e346-202">İşaretçileri belirtme</span><span class="sxs-lookup"><span data-stu-id="6e346-202">Specifying Pointers</span></span>  
 <span data-ttu-id="6e346-203">SimpleTypeSpec * bir yönetilmeyen işaretçi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e346-203">SimpleTypeSpec* represents an unmanaged pointer.</span></span> <span data-ttu-id="6e346-204">Örneğin, MyType yazmanız için bir işaretçi almak için kullanın `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="6e346-204">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="6e346-205">Bir işaretçi MyType yazmanız için bir işaretçi almak için `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="6e346-205">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="6e346-206">Başvuruları belirtme</span><span class="sxs-lookup"><span data-stu-id="6e346-206">Specifying References</span></span>  
 <span data-ttu-id="6e346-207">SimpleTypeSpec & Yönetilen işaretçi veya reference temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e346-207">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="6e346-208">Örneğin, MyType yazmanız için bir başvuru almak için kullanın `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="6e346-208">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="6e346-209">İşaretçileri, başvuru bir düzey sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e346-209">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="6e346-210">Diziler belirtme</span><span class="sxs-lookup"><span data-stu-id="6e346-210">Specifying Arrays</span></span>  
 <span data-ttu-id="6e346-211">BNF dilbilgisi ReflectionEmitDimension yalnızca kullanarak alınan tamamlanmamış tür tanımları için geçerlidir. <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e346-211">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e346-212">Tamamlanmamış türü tanımlarının <xref:System.Reflection.Emit.TypeBuilder> kullanılarak oluşturulan nesneler <xref:System.Reflection.Emit?displayProperty=nameWithType> ancak üretileceği <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="6e346-212">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="6e346-213">ReflectionDimension, yani tamamlanmış herhangi bir tür tanımı, yüklenmiş bir türü almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e346-213">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="6e346-214">Diziler, dizi derecesini belirterek yansıma erişilen:</span><span class="sxs-lookup"><span data-stu-id="6e346-214">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="6e346-215">`Type.GetType("MyArray[]")`0 alt sınır olan tek boyutlu dizi alır.</span><span class="sxs-lookup"><span data-stu-id="6e346-215">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="6e346-216">`Type.GetType("MyArray[*]")`Bilinmeyen alt sınır olan tek boyutlu dizi alır.</span><span class="sxs-lookup"><span data-stu-id="6e346-216">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="6e346-217">`Type.GetType("MyArray[][]")`iki boyutlu bir dizinin dizi alır.</span><span class="sxs-lookup"><span data-stu-id="6e346-217">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="6e346-218">`Type.GetType("MyArray[*,*]")`ve `Type.GetType("MyArray[,]")` dikdörtgen iki boyutlu bir dizi Bilinmeyen alt sınırlarını ile alır.</span><span class="sxs-lookup"><span data-stu-id="6e346-218">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="6e346-219">Bir çalışma zamanı açısından bakıldığında, unutmayın `MyArray[] != MyArray[*]`, ancak çok boyutlu diziler için iki gösterimler eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6e346-219">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="6e346-220">Diğer bir deyişle, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` değerlendiren **doğru**.</span><span class="sxs-lookup"><span data-stu-id="6e346-220">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="6e346-221">İçin **ModuleBuilder.GetType**, `MyArray[0..5]` boyutu 6, daha düşük olan tek boyutlu dizi bağlı 0 gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e346-221">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="6e346-222">`MyArray[4…]`Bilinmeyen boyutu ve alt sınır 4 tek boyutlu dizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e346-222">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e346-223">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e346-223">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6e346-224">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6e346-224">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
