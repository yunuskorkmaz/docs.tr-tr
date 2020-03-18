---
title: Statik Yapıcılar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 744bcacbc38299c0ef7d16e814c415ec5caf95dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170123"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="9b476-102">Statik Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9b476-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="9b476-103">Statik oluşturucu, [statik](../../language-reference/keywords/static.md) verileri başlatmaya veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-103">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="9b476-104">İlk örnek oluşturulmadan veya statik üyelere başvurulmadan önce otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a><span data-ttu-id="9b476-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b476-105">Remarks</span></span>
<span data-ttu-id="9b476-106">Statik oluşturucular aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9b476-106">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="9b476-107">Statik bir oluşturucu erişim değiştiriciler almaz veya parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9b476-107">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="9b476-108">Bir sınıf veya yapı yalnızca bir statik oluşturucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b476-108">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="9b476-109">Statik yapıcılar kalıtsal veya aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="9b476-109">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="9b476-110">Statik bir oluşturucu doğrudan çağrılamaz ve yalnızca ortak dil çalışma zamanı (CLR) tarafından çağrılması amaçlanır.</span><span class="sxs-lookup"><span data-stu-id="9b476-110">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="9b476-111">Otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-111">It is invoked automatically.</span></span>

- <span data-ttu-id="9b476-112">Kullanıcı, statik oluşturucunun programda ne zaman yürütüldürün üzerinde hiçbir denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9b476-112">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="9b476-113">İlk örnek oluşturulmadan veya statik üyelerbaşvurulmadan önce [sınıfı](../../language-reference/keywords/class.md) başlatmak için statik bir oluşturucu otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-113">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="9b476-114">Statik bir oluşturucu, örnek oluşturucunun önünde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9b476-114">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="9b476-115">Bir olaya veya temsilciye atanan statik bir yöntem çağrıldığında, atandığında değil, bir türün statik oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-115">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="9b476-116">Statik alan değişkeni başförü statik yapıcının sınıfında mevcutsa, statik yapıcının yürütülmesinden hemen önce sınıf bildiriminde göründükleri metin sırasına göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9b476-116">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="9b476-117">Statik alanları başlatmak için statik bir oluşturucu sağlamazsanız, tüm statik alanlar [C# türlerinin Varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md)listelenen varsayılan değerlerine başolarak başolarak verilir.</span><span class="sxs-lookup"><span data-stu-id="9b476-117">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="9b476-118">Statik bir oluşturucu bir özel durum atarsa, çalışma zamanı ikinci kez çağrılmaz ve tür, programınızın çalıştırıldığı uygulama etki alanının ömrü boyunca baş harfe dönüşmez.</span><span class="sxs-lookup"><span data-stu-id="9b476-118">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="9b476-119">En sık, <xref:System.TypeInitializationException> statik bir oluşturucu bir türü anında oluşturamıyorsa veya statik bir oluşturucu içinde oluşan işlenmemiş bir özel durum için bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-119">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="9b476-120">Kaynak kodunda açıkça tanımlanmayan örtük statik oluşturucular için sorun giderme, ara dil (IL) kodunun denetlenmesi gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="9b476-120">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="9b476-121">Statik bir oluşturucunun varlığı tür özniteliğinin eklenmesini <xref:System.Reflection.TypeAttributes.BeforeFieldInit> engeller.</span><span class="sxs-lookup"><span data-stu-id="9b476-121">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="9b476-122">Bu, çalışma zamanı optimizasyonunu sınırlar.</span><span class="sxs-lookup"><span data-stu-id="9b476-122">This limits runtime optimization.</span></span>

- <span data-ttu-id="9b476-123">Beyan `static readonly` edilen bir alan yalnızca bildiriminin bir parçası olarak veya statik bir oluşturucu olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="9b476-123">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="9b476-124">Açık statik bir oluşturucu gerekli olmadığında, daha iyi çalışma zamanı optimizasyonu için statik bir oluşturucu aracılığıyla değil, bildirimde statik alanları başlaşın.</span><span class="sxs-lookup"><span data-stu-id="9b476-124">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="9b476-125">Doğrudan erişilebilir olmasa da, sorun giderme başlatma özel durumlarına yardımcı olmak için açık statik bir oluşturucunun varlığı belgelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9b476-125">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="9b476-126">Kullanım</span><span class="sxs-lookup"><span data-stu-id="9b476-126">Usage</span></span>

- <span data-ttu-id="9b476-127">Statik oluşturucuların tipik bir kullanımı, sınıfın bir günlük dosyası kullanması ve oluşturucunun bu dosyaya giriş yazmak için kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9b476-127">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="9b476-128">Statik oluşturucular, yönetilmeyen kod için sarıcı sınıfları oluştururken, `LoadLibrary` oluşturucu yöntemi çağırabildiği zaman da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9b476-128">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="9b476-129">Statik oluşturucular, kısıtlamalar (Tür parametre kısıtlamaları) aracılığıyla derleme zamanında denetlenemeyen tür parametresi üzerinde çalışma zamanı denetimleri uygulamak için de kullanışlı bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="9b476-129">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="9b476-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b476-130">Example</span></span>
 <span data-ttu-id="9b476-131">Bu örnekte, `Bus` sınıfın statik bir oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="9b476-131">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="9b476-132">İlk örneği `Bus` oluşturulduğunda (`bus1`), statik oluşturucu sınıfı başlatmaya çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9b476-132">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="9b476-133">Örnek çıktı, statik oluşturucunun iki örnek `Bus` oluşturulsa bile yalnızca bir kez çalıştığını ve örnek oluşturucu çalıştırmadan önce çalıştığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="9b476-133">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="9b476-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9b476-134">C# language specification</span></span>
<span data-ttu-id="9b476-135">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9b476-135">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9b476-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b476-136">See also</span></span>

- [<span data-ttu-id="9b476-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9b476-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9b476-138">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="9b476-138">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9b476-139">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9b476-139">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="9b476-140">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="9b476-140">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="9b476-141">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="9b476-141">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="9b476-142">Yapıcı Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9b476-142">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="9b476-143">Güvenlik Uyarısı - CA2121: Statik yapıcılar özel olmalıdır</span><span class="sxs-lookup"><span data-stu-id="9b476-143">Security Warning - CA2121: Static constructors should be private</span></span>](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
