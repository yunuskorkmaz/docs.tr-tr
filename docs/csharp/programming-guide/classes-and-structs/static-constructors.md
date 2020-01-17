---
title: Statik oluşturucular- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 7b8171e75bbd27a1079f2c6cc1b7aef6400d7419
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115749"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="e5d32-102">Statik Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e5d32-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="e5d32-103">Statik bir Oluşturucu, herhangi bir [statik](../../language-reference/keywords/static.md) veriyi başlatmak veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-103">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="e5d32-104">İlk örnek oluşturulmadan veya herhangi bir statik üyeye başvurulmadan önce bu otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a><span data-ttu-id="e5d32-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5d32-105">Remarks</span></span>
<span data-ttu-id="e5d32-106">Statik oluşturucular aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e5d32-106">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="e5d32-107">Statik bir Oluşturucu erişim değiştiricileri almaz veya parametrelere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e5d32-107">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="e5d32-108">Bir sınıf veya yapı birimi yalnızca bir statik oluşturucuya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d32-108">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="e5d32-109">Statik oluşturucular devralınamaz veya aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e5d32-109">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="e5d32-110">Statik bir Oluşturucu doğrudan çağrılamaz ve yalnızca ortak dil çalışma zamanı (CLR) tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d32-110">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="e5d32-111">Otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-111">It is invoked automatically.</span></span>

- <span data-ttu-id="e5d32-112">Programda statik Oluşturucu yürütüldüğünde kullanıcının denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e5d32-112">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="e5d32-113">Statik bir Oluşturucu, ilk örnek oluşturulmadan veya herhangi bir statik üyeye başvurulmadan önce [sınıfı](../../language-reference/keywords/class.md) başlatmak için otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-113">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="e5d32-114">Bir statik oluşturucu, örnek oluşturucudan önce çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-114">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="e5d32-115">Bir olaya atanan statik bir yöntem veya temsilci atandığında, bir türün statik Oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-115">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="e5d32-116">Statik alan değişkeni başlatıcıları statik oluşturucunun sınıfında mevcutsa, statik oluşturucunun yürütülmesinden hemen önce sınıf bildiriminde göründükleri metin sırasına göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e5d32-116">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="e5d32-117">Statik alanları başlatmak için statik bir Oluşturucu sağlamazsanız, tüm statik alanlar varsayılan değer [ C# türlerinde](../../language-reference/builtin-types/default-values.md)listelendiği gibi varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-117">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="e5d32-118">Statik bir Oluşturucu bir özel durum oluşturursa, çalışma zamanı ikinci bir kez çağrılmaz ve programınızın çalıştığı uygulama etki alanının ömrü boyunca tür başlatılmamış olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-118">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="e5d32-119">En yaygın olarak, bir statik oluşturucu bir tür örneklememediğinde veya statik oluşturucu içinde oluşan işlenmeyen bir özel durum için <xref:System.TypeInitializationException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5d32-119">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="e5d32-120">Kaynak kodunda açıkça tanımlanmayan örtük statik oluşturucular için, sorun giderme ara dil (IL) kodunu denetlemesini gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e5d32-120">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="e5d32-121">Statik bir oluşturucunun varlığı, <xref:System.Reflection.TypeAttributes.BeforeFieldInit> türü özniteliğinin eklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="e5d32-121">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="e5d32-122">Bu, çalışma zamanının iyileştirmesini sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-122">This limits runtime optimization.</span></span>

- <span data-ttu-id="e5d32-123">`static readonly` olarak belirtilen bir alan, yalnızca bildiriminin bir parçası olarak veya bir statik oluşturucuda atanabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d32-123">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="e5d32-124">Açık bir statik Oluşturucu gerekli olmadığında, daha iyi çalışma zamanı iyileştirmesi için bir statik Oluşturucu yerine bildiriminde statik alanları başlatın.</span><span class="sxs-lookup"><span data-stu-id="e5d32-124">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="e5d32-125">Doğrudan erişilemeyen halde, açık bir statik oluşturucunun varlığı, başlatma özel durumlarının giderilmesi için yardımcı olmak üzere açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-125">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="e5d32-126">Kullanım</span><span class="sxs-lookup"><span data-stu-id="e5d32-126">Usage</span></span>

- <span data-ttu-id="e5d32-127">Statik oluşturucuların tipik kullanımı, sınıfın bir günlük dosyası kullanıldığı ve oluşturucunun bu dosyaya giriş yazmak için kullanıldığı durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-127">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="e5d32-128">Statik oluşturucular, Oluşturucu `LoadLibrary` yöntemini çağırabilmesini, yönetilmeyen kod için sarmalayıcı sınıflar oluştururken de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-128">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="e5d32-129">Statik oluşturucular, derleme zamanında kısıtlama aracılığıyla denetlenemeyen tür parametresinde çalışma zamanı denetimlerini zorlamak için de kullanışlı bir yerdir (tür parametresi kısıtlamaları).</span><span class="sxs-lookup"><span data-stu-id="e5d32-129">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="e5d32-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5d32-130">Example</span></span>
 <span data-ttu-id="e5d32-131">Bu örnekte, `Bus` sınıfının statik bir Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-131">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="e5d32-132">İlk `Bus` örneği oluşturulduğunda (`bus1`), sınıfı başlatmak için statik oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e5d32-132">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="e5d32-133">Örnek çıktı, statik oluşturucunun iki `Bus` örneği oluşturulsa ve örnek Oluşturucu çalıştırılmadan önce çalışmasına rağmen yalnızca bir kez çalıştığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="e5d32-133">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a><span data-ttu-id="e5d32-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e5d32-134">C# language specification</span></span>
<span data-ttu-id="e5d32-135">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e5d32-135">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5d32-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5d32-136">See also</span></span>

- [<span data-ttu-id="e5d32-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e5d32-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e5d32-138">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="e5d32-138">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e5d32-139">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e5d32-139">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e5d32-140">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="e5d32-140">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="e5d32-141">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="e5d32-141">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="e5d32-142">Oluşturucu tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e5d32-142">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="e5d32-143">Güvenlik Uyarısı-CA2121: statik oluşturucular özel olmalıdır</span><span class="sxs-lookup"><span data-stu-id="e5d32-143">Security Warning - CA2121: Static constructors should be private</span></span>](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
