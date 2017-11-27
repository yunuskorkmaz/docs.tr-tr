---
title: "İmzalar (F#)"
description: "F # programı öğeleri türleri, ad alanları ve modülleri gibi bir dizi ortak imzalar hakkında bilgiyi tutmak için bir F # imza dosyası kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 76c84a62-b2f6-44ec-8238-e687e2f7d18e
ms.openlocfilehash: d0f71c6472852268303a2d3af2e4b0a3c256704e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="signatures"></a><span data-ttu-id="8da6e-104">İmzalar</span><span class="sxs-lookup"><span data-stu-id="8da6e-104">Signatures</span></span>

<span data-ttu-id="8da6e-105">Bir imza dosyası türleri, ad alanları ve modülleri gibi F # program öğeleri, bir dizi ortak imzalar hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-105">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="8da6e-106">Bu program öğeleri erişilebilirliğini belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-106">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="8da6e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8da6e-107">Remarks</span></span>
<span data-ttu-id="8da6e-108">Her F # için kod dosyası, elinizde bir *imza dosyası*, kod dosyası olarak ancak .fs yerine uzantısı .fsi ile aynı ada sahip bir dosya değil.</span><span class="sxs-lookup"><span data-stu-id="8da6e-108">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="8da6e-109">İmza dosyaları de komut satırı doğrudan kullanıyorsanız, komut satırı derleme eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-109">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="8da6e-110">Kod dosyaları ve imza dosyalarını arasında ayrım yapmak için kod dosyaları olarak da adlandırılır *uygulama dosyaları*.</span><span class="sxs-lookup"><span data-stu-id="8da6e-110">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="8da6e-111">Bir proje ile ilişkili kod dosyası imza dosyası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-111">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="8da6e-112">Ad alanları, modüller, türleri ve üyeleri karşılık gelen uygulama dosyasındaki bir imza dosyası açıklar.</span><span class="sxs-lookup"><span data-stu-id="8da6e-112">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="8da6e-113">Hangi bölümlerinin belirtmek için bir imza dosyası bilgileri kullanın karşılık gelen uygulamasında kodunun dosya uygulama dosyasını dışındaki koddan erişilebilir ve hangi bölümlerinin uygulama dosyasına iç.</span><span class="sxs-lookup"><span data-stu-id="8da6e-113">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="8da6e-114">Ad alanları, modüller ve uygulama dosyasında bulunan türleri bir alt kümesini ad alanları, modüller ve imza dosyasında bulunan türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8da6e-114">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="8da6e-115">Bu konunun ilerleyen bölümlerinde not ettiğiniz bazı istisnalar imza dosyasında listelenmeyen bu dil öğeleri uygulaması dosyanın özel olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-115">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="8da6e-116">Herhangi bir imza dosyası proje veya komut satırı bulunursa, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8da6e-116">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="8da6e-117">Varsayılan erişilebilirlik hakkında daha fazla bilgi için bkz: [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="8da6e-117">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="8da6e-118">Bir imza dosyası türlerinin tanımlarını ve her bir yöntemi veya işlev uygulamaları tekrarlamayın.</span><span class="sxs-lookup"><span data-stu-id="8da6e-118">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="8da6e-119">Bunun yerine, her yöntemi ve tam bir belirtimini bir modül veya ad alanı parça tarafından uygulanan işlevleri gibi davranır işlevi için imza kullanın.</span><span class="sxs-lookup"><span data-stu-id="8da6e-119">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="8da6e-120">Tür imzası sözdizimi Özet yöntem bildirimlerinde arabirimleri ve soyut sınıflar kullanılan aynı ve doğru şekilde derlenmiş giriş görüntülediğinde IntelliSense ve F # Yorumlayıcı fsi.exe tarafından da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-120">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="8da6e-121">Yeterli bilgi türü korumalı olup olmadığını belirtmek için türü imzada değilse veya bir arabirim türü olup olmadığını belirtir, özniteliğin eklemeniz gerekir, derleyici türüne yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-121">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="8da6e-122">Bu amaçla kullanabileceğiniz öznitelikleri aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8da6e-122">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="8da6e-123">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8da6e-123">Attribute</span></span>|<span data-ttu-id="8da6e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8da6e-124">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="8da6e-125">Türü için hiçbir soyut üye olan veya olmayan genişletilmesi.</span><span class="sxs-lookup"><span data-stu-id="8da6e-125">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="8da6e-126">Bir arabirim için bir türü.</span><span class="sxs-lookup"><span data-stu-id="8da6e-126">For a type that is an interface.</span></span>|
<span data-ttu-id="8da6e-127">Derleyici öznitelikleri imza ve uygulama dosyasını bildiriminde arasında tutarlı değilse bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8da6e-127">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="8da6e-128">Anahtar sözcüğü kullanmak `val` bir değer veya işlev değeri için imza oluşturma için.</span><span class="sxs-lookup"><span data-stu-id="8da6e-128">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="8da6e-129">Anahtar sözcüğü `type` tür imzası tanıtır.</span><span class="sxs-lookup"><span data-stu-id="8da6e-129">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="8da6e-130">Kullanarak bir imza dosyası oluşturabilirsiniz `--sig` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="8da6e-130">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="8da6e-131">Genellikle, .fsi dosyaları el ile yazma.</span><span class="sxs-lookup"><span data-stu-id="8da6e-131">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="8da6e-132">Bunun yerine, derleyici kullanarak .fsi dosyaları oluşturmak, biri varsa ve yöntemleri ve erişilebilir olmasını istiyor musunuz işlevlerini kaldırarak Düzenle bunları, projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8da6e-132">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="8da6e-133">Türü imzalar çeşitli kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8da6e-133">There are several rules for type signatures:</span></span>


- <span data-ttu-id="8da6e-134">Tür kısaltmaları uygulama dosyasındaki bir imza dosyasında kısaltma olmadan türü eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8da6e-134">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="8da6e-135">Kayıtlar ve ayrılmış birleşimler tüm ya da kendi alanları ve oluşturucular hiçbiri kullanıma gerekir ve imza sırada uygulama dosyasını sırayla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-135">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="8da6e-136">Sınıfları, bazıları, tümü veya hiçbiri kendi alanları ve imza yöntemleri ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-136">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="8da6e-137">Sınıfları ve yapıları oluşturucular sahip temel sınıflarına bildirimlerini kullanıma gerekir ( `inherits` bildirim).</span><span class="sxs-lookup"><span data-stu-id="8da6e-137">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="8da6e-138">Ayrıca, sınıfları ve yapıları oluşturucular sahip tüm kullanıcıların soyut yöntemler ve arabirim bildirimleri kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-138">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="8da6e-139">Arabirim türleri, yöntemleri ve arabirimleri ortaya gerekir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-139">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="8da6e-140">Değer imzalar için kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8da6e-140">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="8da6e-141">Erişilebilirlik için değiştiriciler (`public`, `internal`, vb.) ve `inline` ve `mutable` imzada değiştiricileri uygulama de eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-141">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="8da6e-142">Genel tür parametreleri (ya da örtük olarak yapılandırılacağını veya açıkça bildirilen) sayısı eşleşmelidir ve genel tür parametrelerindeki türü kısıtlamaları ve türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-142">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="8da6e-143">Varsa `Literal` özniteliği kullanılır, hem imza hem de uygulama görünmesi gerekir ve her ikisi için aynı sabit değer kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8da6e-143">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="8da6e-144">Parametreleri desenin (olarak da bilinen *parametre*) imzalar ve uygulamaları tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8da6e-144">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


<span data-ttu-id="8da6e-145">Aşağıdaki kod örneğinde, ad alanı, modül, işlevi ve türü imzaları uygun özniteliklerini birlikte sahip bir imza dosyası örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-145">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="8da6e-146">Ayrıca, karşılık gelen uygulama dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-146">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="8da6e-147">Aşağıdaki kod uygulama dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8da6e-147">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="8da6e-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8da6e-148">See Also</span></span>
[<span data-ttu-id="8da6e-149">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="8da6e-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="8da6e-150">Erişim denetimi</span><span class="sxs-lookup"><span data-stu-id="8da6e-150">Access Control</span></span>](access-control.md)

[<span data-ttu-id="8da6e-151">Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8da6e-151">Compiler Options</span></span>](compiler-options.md)
