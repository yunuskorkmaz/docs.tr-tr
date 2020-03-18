---
title: Statik Sınıflar ve Statik Sınıf Üyeleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 7add512b262afbabe996f752c083566a2c394dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705437"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a><span data-ttu-id="5a214-102">Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5a214-102">Static Classes and Static Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="5a214-103">[Statik](../../language-reference/keywords/static.md) bir sınıf temelde statik olmayan bir sınıfla aynıdır, ancak bir fark vardır: statik bir sınıf anında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5a214-103">A [static](../../language-reference/keywords/static.md) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated.</span></span> <span data-ttu-id="5a214-104">Başka bir deyişle, sınıf türünden bir değişken oluşturmak için [yeni](../../language-reference/operators/new-operator.md) işleci kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5a214-104">In other words, you cannot use the [new](../../language-reference/operators/new-operator.md) operator to create a variable of the class type.</span></span> <span data-ttu-id="5a214-105">Örnek değişken olmadığından, sınıf adının kendisini kullanarak statik sınıfın üyelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a214-105">Because there is no instance variable, you access the members of a static class by using the class name itself.</span></span> <span data-ttu-id="5a214-106">Örneğin, adlandırılmış `UtilityClass` bir statik sınıfıniz varsa, buna `MethodA`aşağıdaki örnekte gösterildiği gibi çağrıbilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a214-106">For example, if you have a static class that is named `UtilityClass` that has a public static method named `MethodA`, you call the method as shown in the following example:</span></span>  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 <span data-ttu-id="5a214-107">Statik bir sınıf, giriş parametreleri üzerinde çalışan ve herhangi bir iç örnek alanını almak veya ayarlamak zorunda olmayan yöntem kümeleri için uygun bir kapsayıcı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-107">A static class can be used as a convenient container for sets of methods that just operate on input parameters and do not have to get or set any internal instance fields.</span></span> <span data-ttu-id="5a214-108">Örneğin, .NET Framework Class Kitaplığı'nda statik <xref:System.Math?displayProperty=nameWithType> sınıf, <xref:System.Math> sınıfın belirli bir örneğine özgü verileri depolamaveya alma gereksinimi olmadan matematiksel işlemleri gerçekleştiren yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="5a214-108">For example, in the .NET Framework Class Library, the static <xref:System.Math?displayProperty=nameWithType> class contains methods that perform mathematical operations, without any requirement to store or retrieve data that is unique to a particular instance of the <xref:System.Math> class.</span></span> <span data-ttu-id="5a214-109">Diğer bir deyişle, aşağıdaki örnekte gösterildiği gibi sınıf adını ve yöntem adını belirterek sınıf üyelerini uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="5a214-109">That is, you apply the members of the class by specifying the class name and the method name, as shown in the following example.</span></span>  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 <span data-ttu-id="5a214-110">Tüm sınıf türlerinde olduğu gibi, statik bir sınıfın tür bilgileri,.NET Framework ortak dil çalışma zamanı (CLR) tarafından sınıfa başvurulan program yüklendiğinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5a214-110">As is the case with all class types, the type information for a static class is loaded by the .NET Framework common language runtime (CLR) when the program that references the class is loaded.</span></span> <span data-ttu-id="5a214-111">Program sınıfın tam olarak ne zaman yüklendiğini belirtemez.</span><span class="sxs-lookup"><span data-stu-id="5a214-111">The program cannot specify exactly when the class is loaded.</span></span> <span data-ttu-id="5a214-112">Ancak, programda ilk kez sınıfbaşvurulmadan önce, yükleme ve alanlarının başlatılması ve statik oluşturucusu çağrılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-112">However, it is guaranteed to be loaded and to have its fields initialized and its static constructor called before the class is referenced for the first time in your program.</span></span> <span data-ttu-id="5a214-113">Statik bir oluşturucu yalnızca bir kez çağrılır ve statik bir sınıf, programınızın bulunduğu uygulama etki alanının ömrü boyunca bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="5a214-113">A static constructor is only called one time, and a static class remains in memory for the lifetime of the application domain in which your program resides.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a214-114">Yalnızca bir örneğinin oluşturulmasına izin veren statik olmayan bir sınıf oluşturmak için [bkz.](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29)</span><span class="sxs-lookup"><span data-stu-id="5a214-114">To create a non-static class that allows only one instance of itself to be created, see [Implementing Singleton in C#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).</span></span>  
  
 <span data-ttu-id="5a214-115">Aşağıdaki liste statik bir sınıfın ana özelliklerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="5a214-115">The following list provides the main features of a static class:</span></span>  
  
- <span data-ttu-id="5a214-116">Yalnızca statik üyeler içerir.</span><span class="sxs-lookup"><span data-stu-id="5a214-116">Contains only static members.</span></span>  
  
- <span data-ttu-id="5a214-117">Anlık olarak yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="5a214-117">Cannot be instantiated.</span></span>  
  
- <span data-ttu-id="5a214-118">Mühürlü.</span><span class="sxs-lookup"><span data-stu-id="5a214-118">Is sealed.</span></span>  
  
- <span data-ttu-id="5a214-119">Örnek [Oluşturucular](./instance-constructors.md)içeremez.</span><span class="sxs-lookup"><span data-stu-id="5a214-119">Cannot contain [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="5a214-120">Bu nedenle statik bir sınıf oluşturmak temelde yalnızca statik üyeler ve özel bir oluşturucu içeren bir sınıf oluşturmakla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5a214-120">Creating a static class is therefore basically the same as creating a class that contains only static members and a private constructor.</span></span> <span data-ttu-id="5a214-121">Özel bir oluşturucu sınıfın anlık olmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="5a214-121">A private constructor prevents the class from being instantiated.</span></span> <span data-ttu-id="5a214-122">Statik bir sınıf kullanmanın avantajı, derleyicinin hiçbir örnek üyenin yanlışlıkla eklenmediğinden emin olmak için denetlemesidir.</span><span class="sxs-lookup"><span data-stu-id="5a214-122">The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added.</span></span> <span data-ttu-id="5a214-123">Derleyici, bu sınıfın örneklerinin oluşturulamayacağını garanti eder.</span><span class="sxs-lookup"><span data-stu-id="5a214-123">The compiler will guarantee that instances of this class cannot be created.</span></span>  
  
 <span data-ttu-id="5a214-124">Statik sınıflar mühürlenir ve bu nedenle devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="5a214-124">Static classes are sealed and therefore cannot be inherited.</span></span> <span data-ttu-id="5a214-125">Onlar dışında <xref:System.Object>herhangi bir sınıftan miras olamaz.</span><span class="sxs-lookup"><span data-stu-id="5a214-125">They cannot inherit from any class except <xref:System.Object>.</span></span> <span data-ttu-id="5a214-126">Statik sınıflar örnek oluşturucu içeremez; ancak statik bir oluşturucu içerebilirler.</span><span class="sxs-lookup"><span data-stu-id="5a214-126">Static classes cannot contain an instance constructor; however, they can contain a static constructor.</span></span> <span data-ttu-id="5a214-127">Non-statik sınıflar da bir statik oluşturucu tanımlamak gerekir sınıf önemsiz olmayan başlatma gerektiren statik üyeler içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="5a214-127">Non-static classes should also define a static constructor if the class contains static members that require non-trivial initialization.</span></span> <span data-ttu-id="5a214-128">Daha fazla bilgi için Statik [Oluşturucular'a](./static-constructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5a214-128">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a214-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a214-129">Example</span></span>  
 <span data-ttu-id="5a214-130">Sıcaklığı Santigrat'tan Fahrenhayt'a ve Fahrenhayt'tan Santigrat'a dönüştüren iki yöntem içeren statik bir sınıf örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5a214-130">Here is an example of a static class that contains two methods that convert temperature from Celsius to Fahrenheit and from Fahrenheit to Celsius:</span></span>  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a><span data-ttu-id="5a214-131">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="5a214-131">Static Members</span></span>  
 <span data-ttu-id="5a214-132">Statik olmayan bir sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-132">A non-static class can contain static methods, fields, properties, or events.</span></span> <span data-ttu-id="5a214-133">Statik üye, sınıfın hiçbir örneği oluşturulmasa bile bir sınıfta çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-133">The static member is callable on a class even when no instance of the class has been created.</span></span> <span data-ttu-id="5a214-134">Statik üyeye her zaman örnek adı değil, sınıf adı tarafından erişilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-134">The static member is always accessed by the class name, not the instance name.</span></span> <span data-ttu-id="5a214-135">Sınıfın kaç örneği oluşturulduğundan bağımsız olarak statik bir üyenin yalnızca bir kopyası vardır.</span><span class="sxs-lookup"><span data-stu-id="5a214-135">Only one copy of a static member exists, regardless of how many instances of the class are created.</span></span> <span data-ttu-id="5a214-136">Statik yöntemler ve özellikler, içeren türünde statik olmayan alanlara ve olaylara erişemez ve yöntem parametresinde açıkça geçilmediği sürece herhangi bir nesnenin örnek değişkenine erişemezler.</span><span class="sxs-lookup"><span data-stu-id="5a214-136">Static methods and properties cannot access non-static fields and events in their containing type, and they cannot access an instance variable of any object unless it is explicitly passed in a method parameter.</span></span>  
  
 <span data-ttu-id="5a214-137">Tüm bir sınıfı statik olarak bildirmektense, bazı statik üyelerle statik olmayan bir sınıfı bildirmek daha tipiktir.</span><span class="sxs-lookup"><span data-stu-id="5a214-137">It is more typical to declare a non-static class with some static members, than to declare an entire class as static.</span></span> <span data-ttu-id="5a214-138">Statik alanların iki yaygın kullanımı, anında alınan nesne sayısının sayısını tutmak veya tüm örnekler arasında paylaşılması gereken bir değeri depolamak içindir.</span><span class="sxs-lookup"><span data-stu-id="5a214-138">Two common uses of static fields are to keep a count of the number of objects that have been instantiated, or to store a value that must be shared among all instances.</span></span>  
  
 <span data-ttu-id="5a214-139">Statik yöntemler, sınıfın herhangi bir örneğine değil, sınıfa ait olduğundan aşırı yüklenebilir, ancak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-139">Static methods can be overloaded but not overridden, because they belong to the class, and not to any instance of the class.</span></span>  
  
 <span data-ttu-id="5a214-140">Bir alan olarak `static const`bildirilemese de, [const](../../language-reference/keywords/const.md) alan aslında davranışında statiktir.</span><span class="sxs-lookup"><span data-stu-id="5a214-140">Although a field cannot be declared as `static const`, a [const](../../language-reference/keywords/const.md) field is essentially static in its behavior.</span></span> <span data-ttu-id="5a214-141">Türe ait, tür örneklerine değil.</span><span class="sxs-lookup"><span data-stu-id="5a214-141">It belongs to the type, not to instances of the type.</span></span> <span data-ttu-id="5a214-142">Bu nedenle, const alanlara statik `ClassName.MemberName` alanlar için kullanılan aynı gösterim kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-142">Therefore, const fields can be accessed by using the same `ClassName.MemberName` notation that is used for static fields.</span></span> <span data-ttu-id="5a214-143">Nesne örneği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5a214-143">No object instance is required.</span></span>  
  
 <span data-ttu-id="5a214-144">C# statik yerel değişkenleri (yöntem kapsamında bildirilen değişkenler) desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5a214-144">C# does not support static local variables (variables that are declared in method scope).</span></span>  
  
 <span data-ttu-id="5a214-145">Aşağıdaki örnekte gösterildiği gibi, üyenin `static` dönüş türünden önce anahtar sözcüğü kullanarak statik sınıf üyelerini beyan emzmiş olursunuz:</span><span class="sxs-lookup"><span data-stu-id="5a214-145">You declare static class members by using the `static` keyword before the return type of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 <span data-ttu-id="5a214-146">Statik üyeye ilk kez erişilmeden önce ve statik yapıcı dan önce statik üyeler ekime denilir.</span><span class="sxs-lookup"><span data-stu-id="5a214-146">Static members are initialized before the static member is accessed for the first time and before the static constructor, if there is one, is called.</span></span> <span data-ttu-id="5a214-147">Statik bir sınıf üyesine erişmek için, aşağıdaki örnekte gösterildiği gibi, üyenin konumunu belirtmek için değişken adı yerine sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a214-147">To access a static class member, use the name of the class instead of a variable name to specify the location of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 <span data-ttu-id="5a214-148">Sınıfınız statik alanlar içeriyorsa, sınıf yüklendiğinde bunları başlatifleştiren statik bir oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5a214-148">If your class contains static fields, provide a static constructor that initializes them when the class is loaded.</span></span>  
  
 <span data-ttu-id="5a214-149">Statik bir yönteme yapılan çağrı, Microsoft ara dilinde (MSIL) bir çağrı yönergesi oluştururken, örnek yöntemine yapılan bir çağrı, boş nesne başvurularını da denetleyen bir `callvirt` yönerge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a214-149">A call to a static method generates a call instruction in Microsoft intermediate language (MSIL), whereas a call to an instance method generates a `callvirt` instruction, which also checks for a null object references.</span></span> <span data-ttu-id="5a214-150">Ancak, çoğu zaman ikisi arasındaki performans farkı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="5a214-150">However, most of the time the performance difference between the two is not significant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5a214-151">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5a214-151">C# Language Specification</span></span>  

<span data-ttu-id="5a214-152">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Statik sınıflar](~/_csharplang/spec/classes.md#static-classes) ve Statik ve [örnek üyelere](~/_csharplang/spec/classes.md#static-and-instance-members) bakın.</span><span class="sxs-lookup"><span data-stu-id="5a214-152">For more information, see [Static classes](~/_csharplang/spec/classes.md#static-classes) and [Static and instance members](~/_csharplang/spec/classes.md#static-and-instance-members) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5a214-153">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="5a214-153">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5a214-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a214-154">See also</span></span>

- [<span data-ttu-id="5a214-155">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5a214-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5a214-156">Statik</span><span class="sxs-lookup"><span data-stu-id="5a214-156">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="5a214-157">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="5a214-157">Classes</span></span>](./classes.md)
- [<span data-ttu-id="5a214-158">Sınıfı</span><span class="sxs-lookup"><span data-stu-id="5a214-158">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="5a214-159">Statik Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5a214-159">Static Constructors</span></span>](./static-constructors.md)
- [<span data-ttu-id="5a214-160">Örnek Oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="5a214-160">Instance Constructors</span></span>](./instance-constructors.md)
