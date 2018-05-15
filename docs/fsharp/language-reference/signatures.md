---
title: İmzalar (F#)
description: 'F # programı öğeleri türleri, ad alanları ve modülleri gibi bir dizi ortak imzalar hakkında bilgiyi tutmak için bir F # imza dosyası kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6e182a1a0ac7f3f9fab27026e582d83ee737822e
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2018
---
# <a name="signatures"></a><span data-ttu-id="f6a69-103">İmzalar</span><span class="sxs-lookup"><span data-stu-id="f6a69-103">Signatures</span></span>

<span data-ttu-id="f6a69-104">Bir imza dosyası türleri, ad alanları ve modülleri gibi F # program öğeleri, bir dizi ortak imzalar hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="f6a69-105">Bu program öğeleri erişilebilirliğini belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="f6a69-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6a69-106">Remarks</span></span>
<span data-ttu-id="f6a69-107">Her F # için kod dosyası, elinizde bir *imza dosyası*, kod dosyası olarak ancak .fs yerine uzantısı .fsi ile aynı ada sahip bir dosya değil.</span><span class="sxs-lookup"><span data-stu-id="f6a69-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="f6a69-108">İmza dosyaları de komut satırı doğrudan kullanıyorsanız, komut satırı derleme eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="f6a69-109">Kod dosyaları ve imza dosyalarını arasında ayrım yapmak için kod dosyaları olarak da adlandırılır *uygulama dosyaları*.</span><span class="sxs-lookup"><span data-stu-id="f6a69-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="f6a69-110">Bir proje ile ilişkili kod dosyası imza dosyası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="f6a69-111">Ad alanları, modüller, türleri ve üyeleri karşılık gelen uygulama dosyasındaki bir imza dosyası açıklar.</span><span class="sxs-lookup"><span data-stu-id="f6a69-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="f6a69-112">Hangi bölümlerinin belirtmek için bir imza dosyası bilgileri kullanın karşılık gelen uygulamasında kodunun dosya uygulama dosyasını dışındaki koddan erişilebilir ve hangi bölümlerinin uygulama dosyasına iç.</span><span class="sxs-lookup"><span data-stu-id="f6a69-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="f6a69-113">Ad alanları, modüller ve uygulama dosyasında bulunan türleri bir alt kümesini ad alanları, modüller ve imza dosyasında bulunan türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="f6a69-114">Bu konunun ilerleyen bölümlerinde not ettiğiniz bazı istisnalar imza dosyasında listelenmeyen bu dil öğeleri uygulaması dosyanın özel olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="f6a69-115">Herhangi bir imza dosyası proje veya komut satırı bulunursa, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="f6a69-116">Varsayılan erişilebilirlik hakkında daha fazla bilgi için bkz: [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="f6a69-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="f6a69-117">Bir imza dosyası türlerinin tanımlarını ve her bir yöntemi veya işlev uygulamaları tekrarlamayın.</span><span class="sxs-lookup"><span data-stu-id="f6a69-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="f6a69-118">Bunun yerine, her yöntemi ve tam bir belirtimini bir modül veya ad alanı parça tarafından uygulanan işlevleri gibi davranır işlevi için imza kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6a69-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="f6a69-119">Tür imzası sözdizimi Özet yöntem bildirimlerinde arabirimleri ve soyut sınıflar kullanılan aynı ve doğru şekilde derlenmiş giriş görüntülediğinde IntelliSense ve F # Yorumlayıcı fsi.exe tarafından da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="f6a69-120">Yeterli bilgi türü korumalı olup olmadığını belirtmek için türü imzada değilse veya bir arabirim türü olup olmadığını belirtir, özniteliğin eklemeniz gerekir, derleyici türüne yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="f6a69-121">Bu amaçla kullanabileceğiniz öznitelikleri aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="f6a69-122">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6a69-122">Attribute</span></span>|<span data-ttu-id="f6a69-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6a69-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="f6a69-124">Türü için hiçbir soyut üye olan veya olmayan genişletilmesi.</span><span class="sxs-lookup"><span data-stu-id="f6a69-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="f6a69-125">Bir arabirim için bir türü.</span><span class="sxs-lookup"><span data-stu-id="f6a69-125">For a type that is an interface.</span></span>|
<span data-ttu-id="f6a69-126">Derleyici öznitelikleri imza ve uygulama dosyasını bildiriminde arasında tutarlı değilse bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f6a69-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="f6a69-127">Anahtar sözcüğü kullanmak `val` bir değer veya işlev değeri için imza oluşturma için.</span><span class="sxs-lookup"><span data-stu-id="f6a69-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="f6a69-128">Anahtar sözcüğü `type` tür imzası tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="f6a69-129">Kullanarak bir imza dosyası oluşturabilirsiniz `--sig` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f6a69-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="f6a69-130">Genellikle, .fsi dosyaları el ile yazma.</span><span class="sxs-lookup"><span data-stu-id="f6a69-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="f6a69-131">Bunun yerine, derleyici kullanarak .fsi dosyaları oluşturmak, biri varsa ve yöntemleri ve erişilebilir olmasını istiyor musunuz işlevlerini kaldırarak Düzenle bunları, projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6a69-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="f6a69-132">Türü imzalar çeşitli kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f6a69-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="f6a69-133">Tür kısaltmaları uygulama dosyasındaki bir imza dosyasında kısaltma olmadan türü eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f6a69-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="f6a69-134">Kayıtlar ve ayrılmış birleşimler tüm ya da kendi alanları ve oluşturucular hiçbiri kullanıma gerekir ve imza sırada uygulama dosyasını sırayla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="f6a69-135">Sınıfları, bazıları, tümü veya hiçbiri kendi alanları ve imza yöntemleri ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="f6a69-136">Sınıfları ve yapıları oluşturucular sahip temel sınıflarına bildirimlerini kullanıma gerekir ( `inherits` bildirim).</span><span class="sxs-lookup"><span data-stu-id="f6a69-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="f6a69-137">Ayrıca, sınıfları ve yapıları oluşturucular sahip tüm kullanıcıların soyut yöntemler ve arabirim bildirimleri kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="f6a69-138">Arabirim türleri, yöntemleri ve arabirimleri ortaya gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="f6a69-139">Değer imzalar için kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f6a69-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="f6a69-140">Erişilebilirlik için değiştiriciler (`public`, `internal`, vb.) ve `inline` ve `mutable` imzada değiştiricileri uygulama de eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="f6a69-141">Genel tür parametreleri (ya da örtük olarak yapılandırılacağını veya açıkça bildirilen) sayısı eşleşmelidir ve genel tür parametrelerindeki türü kısıtlamaları ve türleri eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="f6a69-142">Varsa `Literal` özniteliği kullanılır, hem imza hem de uygulama görünmesi gerekir ve her ikisi için aynı sabit değer kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="f6a69-143">Parametreleri desenin (olarak da bilinen *parametre*) imzalar ve uygulamaları tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


- <span data-ttu-id="f6a69-144">Parametre adları bir imza dosyasında karşılık gelen uygulama dosyasından farklıysa, imza dosyası adı bunun yerine, hata ayıklama veya profil sorunlara neden olabilir kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6a69-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="f6a69-145">Bu tür uyuşmazlıkların proje dosyanızda 3218 uyarı etkinleştir bildirilmesini istiyorsanız veya derleyicisini çağırma (bkz `--warnon` altında [derleyici seçenekleri](compiler-options.md)).</span><span class="sxs-lookup"><span data-stu-id="f6a69-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>


<span data-ttu-id="f6a69-146">Aşağıdaki kod örneğinde, ad alanı, modül, işlevi ve türü imzaları uygun özniteliklerini birlikte sahip bir imza dosyası örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="f6a69-147">Ayrıca, karşılık gelen uygulama dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="f6a69-148">Aşağıdaki kod uygulama dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6a69-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="f6a69-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6a69-149">See Also</span></span>
[<span data-ttu-id="f6a69-150">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f6a69-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f6a69-151">Erişim Denetimi</span><span class="sxs-lookup"><span data-stu-id="f6a69-151">Access Control</span></span>](access-control.md)

[<span data-ttu-id="f6a69-152">Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f6a69-152">Compiler Options</span></span>](compiler-options.md)
