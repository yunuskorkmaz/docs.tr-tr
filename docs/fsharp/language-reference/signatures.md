---
title: İmzalar (F#)
description: 'F # programı öğeleri türleri, ad alanları ve modülleri gibi bir dizi ortak imzalar hakkında bilgiyi tutmak için bir F # imza dosyası kullanmayı öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c98ac6c62fdcee51532a162596e99309a31802ec
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="signatures"></a><span data-ttu-id="103cc-103">İmzalar</span><span class="sxs-lookup"><span data-stu-id="103cc-103">Signatures</span></span>

<span data-ttu-id="103cc-104">Bir imza dosyası türleri, ad alanları ve modülleri gibi F # program öğeleri, bir dizi ortak imzalar hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="103cc-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="103cc-105">Bu program öğeleri erişilebilirliğini belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="103cc-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="103cc-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="103cc-106">Remarks</span></span>
<span data-ttu-id="103cc-107">Her F # için kod dosyası, elinizde bir *imza dosyası*, kod dosyası olarak ancak .fs yerine uzantısı .fsi ile aynı ada sahip bir dosya değil.</span><span class="sxs-lookup"><span data-stu-id="103cc-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="103cc-108">İmza dosyaları de komut satırı doğrudan kullanıyorsanız, komut satırı derleme eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="103cc-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="103cc-109">Kod dosyaları ve imza dosyalarını arasında ayrım yapmak için kod dosyaları olarak da adlandırılır *uygulama dosyaları*.</span><span class="sxs-lookup"><span data-stu-id="103cc-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="103cc-110">Bir proje ile ilişkili kod dosyası imza dosyası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="103cc-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="103cc-111">Ad alanları, modüller, türleri ve üyeleri karşılık gelen uygulama dosyasındaki bir imza dosyası açıklar.</span><span class="sxs-lookup"><span data-stu-id="103cc-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="103cc-112">Hangi bölümlerinin belirtmek için bir imza dosyası bilgileri kullanın karşılık gelen uygulamasında kodunun dosya uygulama dosyasını dışındaki koddan erişilebilir ve hangi bölümlerinin uygulama dosyasına iç.</span><span class="sxs-lookup"><span data-stu-id="103cc-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="103cc-113">Ad alanları, modüller ve uygulama dosyasında bulunan türleri bir alt kümesini ad alanları, modüller ve imza dosyasında bulunan türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="103cc-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="103cc-114">Bu konunun ilerleyen bölümlerinde not ettiğiniz bazı istisnalar imza dosyasında listelenmeyen bu dil öğeleri uygulaması dosyanın özel olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="103cc-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="103cc-115">Herhangi bir imza dosyası proje veya komut satırı bulunursa, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="103cc-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="103cc-116">Varsayılan erişilebilirlik hakkında daha fazla bilgi için bkz: [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="103cc-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="103cc-117">Bir imza dosyası türlerinin tanımlarını ve her bir yöntemi veya işlev uygulamaları tekrarlamayın.</span><span class="sxs-lookup"><span data-stu-id="103cc-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="103cc-118">Bunun yerine, her yöntemi ve tam bir belirtimini bir modül veya ad alanı parça tarafından uygulanan işlevleri gibi davranır işlevi için imza kullanın.</span><span class="sxs-lookup"><span data-stu-id="103cc-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="103cc-119">Tür imzası sözdizimi Özet yöntem bildirimlerinde arabirimleri ve soyut sınıflar kullanılan aynı ve doğru şekilde derlenmiş giriş görüntülediğinde IntelliSense ve F # Yorumlayıcı fsi.exe tarafından da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="103cc-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="103cc-120">Yeterli bilgi türü korumalı olup olmadığını belirtmek için türü imzada değilse veya bir arabirim türü olup olmadığını belirtir, özniteliğin eklemeniz gerekir, derleyici türüne yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="103cc-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="103cc-121">Bu amaçla kullanabileceğiniz öznitelikleri aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="103cc-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="103cc-122">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="103cc-122">Attribute</span></span>|<span data-ttu-id="103cc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="103cc-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="103cc-124">Türü için hiçbir soyut üye olan veya olmayan genişletilmesi.</span><span class="sxs-lookup"><span data-stu-id="103cc-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="103cc-125">Bir arabirim için bir türü.</span><span class="sxs-lookup"><span data-stu-id="103cc-125">For a type that is an interface.</span></span>|
<span data-ttu-id="103cc-126">Derleyici öznitelikleri imza ve uygulama dosyasını bildiriminde arasında tutarlı değilse bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="103cc-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="103cc-127">Anahtar sözcüğü kullanmak `val` bir değer veya işlev değeri için imza oluşturma için.</span><span class="sxs-lookup"><span data-stu-id="103cc-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="103cc-128">Anahtar sözcüğü `type` tür imzası tanıtır.</span><span class="sxs-lookup"><span data-stu-id="103cc-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="103cc-129">Kullanarak bir imza dosyası oluşturabilirsiniz `--sig` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="103cc-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="103cc-130">Genellikle, .fsi dosyaları el ile yazma.</span><span class="sxs-lookup"><span data-stu-id="103cc-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="103cc-131">Bunun yerine, derleyici kullanarak .fsi dosyaları oluşturmak, biri varsa ve yöntemleri ve erişilebilir olmasını istiyor musunuz işlevlerini kaldırarak Düzenle bunları, projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="103cc-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="103cc-132">Türü imzalar çeşitli kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="103cc-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="103cc-133">Tür kısaltmaları uygulama dosyasındaki bir imza dosyasında kısaltma olmadan türü eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="103cc-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="103cc-134">Kayıtlar ve ayrılmış birleşimler tüm ya da kendi alanları ve oluşturucular hiçbiri kullanıma gerekir ve imza sırada uygulama dosyasını sırayla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="103cc-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="103cc-135">Sınıfları, bazıları, tümü veya hiçbiri kendi alanları ve imza yöntemleri ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="103cc-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="103cc-136">Sınıfları ve yapıları oluşturucular sahip temel sınıflarına bildirimlerini kullanıma gerekir ( `inherits` bildirim).</span><span class="sxs-lookup"><span data-stu-id="103cc-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="103cc-137">Ayrıca, sınıfları ve yapıları oluşturucular sahip tüm kullanıcıların soyut yöntemler ve arabirim bildirimleri kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="103cc-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="103cc-138">Arabirim türleri, yöntemleri ve arabirimleri ortaya gerekir.</span><span class="sxs-lookup"><span data-stu-id="103cc-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="103cc-139">Değer imzalar için kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="103cc-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="103cc-140">Erişilebilirlik için değiştiriciler (`public`, `internal`, vb.) ve `inline` ve `mutable` imzada değiştiricileri uygulama de eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="103cc-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="103cc-141">Genel tür parametreleri (ya da örtük olarak yapılandırılacağını veya açıkça bildirilen) sayısı eşleşmelidir ve genel tür parametrelerindeki türü kısıtlamaları ve türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="103cc-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="103cc-142">Varsa `Literal` özniteliği kullanılır, hem imza hem de uygulama görünmesi gerekir ve her ikisi için aynı sabit değer kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="103cc-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="103cc-143">Parametreleri desenin (olarak da bilinen *parametre*) imzalar ve uygulamaları tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="103cc-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


<span data-ttu-id="103cc-144">Aşağıdaki kod örneğinde, ad alanı, modül, işlevi ve türü imzaları uygun özniteliklerini birlikte sahip bir imza dosyası örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="103cc-144">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="103cc-145">Ayrıca, karşılık gelen uygulama dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="103cc-145">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="103cc-146">Aşağıdaki kod uygulama dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="103cc-146">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="103cc-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="103cc-147">See Also</span></span>
[<span data-ttu-id="103cc-148">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="103cc-148">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="103cc-149">Erişim Denetimi</span><span class="sxs-lookup"><span data-stu-id="103cc-149">Access Control</span></span>](access-control.md)

[<span data-ttu-id="103cc-150">Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="103cc-150">Compiler Options</span></span>](compiler-options.md)
