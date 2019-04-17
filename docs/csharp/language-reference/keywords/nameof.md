---
title: nameof - C# başvurusu
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04de4dc6f320213c1a9c95b1abb92488fac0a81f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614096"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="7f616-102">nameof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7f616-102">nameof (C# Reference)</span></span>

<span data-ttu-id="7f616-103">Değişken, tür veya üyenin basit (nitelenmemiş) dize adını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f616-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>

<span data-ttu-id="7f616-104">Model-view-controller (MVC) bağlantıları, takma kodundaki bildirirken tetikleme özellik değişti olayları, vb. genellikle bir yöntemin dize adını yakalamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="7f616-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="7f616-105">Kullanarak `nameof` tutan kodunuzu geçerli tanımları adlandırırken.</span><span class="sxs-lookup"><span data-stu-id="7f616-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="7f616-106">Önce dize sabit değerleri tanımları için başvuruda bulunmak için kullanmanız araçları bu dize değişmez değerleri denetlemek için bilmiyorsanız çünkü kod öğeleri yeniden adlandırılırken kırılır gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="7f616-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>

<span data-ttu-id="7f616-107">A `nameof` ifadesi bu formu sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7f616-107">A `nameof` expression has this form:</span></span>

```csharp
if (x == null) throw new ArgumentNullException(nameof(x));
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"
```

## <a name="key-use-cases"></a><span data-ttu-id="7f616-108">Anahtar kullanım örnekleri</span><span class="sxs-lookup"><span data-stu-id="7f616-108">Key Use Cases</span></span>

<span data-ttu-id="7f616-109">Bu örnekler için anahtar kullanım örnekleri `nameof`.</span><span class="sxs-lookup"><span data-stu-id="7f616-109">These examples show the key use cases for `nameof`.</span></span>

<span data-ttu-id="7f616-110">Parametreleri doğrula:</span><span class="sxs-lookup"><span data-stu-id="7f616-110">Validate parameters:</span></span>

 ```csharp
void f(string s) {
    if (s == null) throw new ArgumentNullException(nameof(s));
}
```

<span data-ttu-id="7f616-111">MVC eylemi bağlantılar:</span><span class="sxs-lookup"><span data-stu-id="7f616-111">MVC Action links:</span></span>

```html
<%= Html.ActionLink("Sign up",
             @typeof(UserController),
             @nameof(UserController.SignUp))
%>
```

<span data-ttu-id="7f616-112">INotifyPropertyChanged:</span><span class="sxs-lookup"><span data-stu-id="7f616-112">INotifyPropertyChanged:</span></span>

```csharp
int p {
    get { return this.p; }
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too
}
```

<span data-ttu-id="7f616-113">XAML bağımlılık özelliği:</span><span class="sxs-lookup"><span data-stu-id="7f616-113">XAML dependency property:</span></span>

```csharp
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));
```

<span data-ttu-id="7f616-114">Günlüğe kaydetme:</span><span class="sxs-lookup"><span data-stu-id="7f616-114">Logging:</span></span>

```csharp
void f(int i) {
    Log(nameof(f), "method entry");
}
```

<span data-ttu-id="7f616-115">Öznitelikleri:</span><span class="sxs-lookup"><span data-stu-id="7f616-115">Attributes:</span></span>

```csharp
[DebuggerDisplay("={" + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

## <a name="examples"></a><span data-ttu-id="7f616-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7f616-116">Examples</span></span>

<span data-ttu-id="7f616-117">Bazı C# örnekleri:</span><span class="sxs-lookup"><span data-stu-id="7f616-117">Some C# examples:</span></span>

```csharp
using Stuff = Some.Cool.Functionality
class C {
    static int Method1 (string x, int y) {}
    static int Method1 (string x, string y) {}
    int Method2 (int z) {}
    string f<T>() => nameof(T);
}

var c = new C()

class Test {
    static void Main (string[] args) {
        Console.WriteLine(nameof(C)); // -> "C"
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]
        Console.WriteLine(nameof(f)); // -> "f"
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]
        // Console.WriteLine(nameof(f<>)); -> [syntax error]
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]
    }
}
```

## <a name="remarks"></a><span data-ttu-id="7f616-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f616-118">Remarks</span></span>

<span data-ttu-id="7f616-119">Bağımsız değişkeni `nameof` basit bir ad, tam adı, üye erişimi, temel erişim belirtilen bir üyeye sahip veya bu erişim belirli bir üyeye sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f616-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="7f616-120">Kod tanımı bağımsız değişken ifadesi tanımlar, ancak hiçbir zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7f616-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>

<span data-ttu-id="7f616-121">Bağımsız değişken bir ifadenin sözdizimi kurallarına göre olması gerektiğinden, vardır listelemek kullanışlı olmayan birçok şey izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="7f616-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="7f616-122">Hataları üreten söz şunlardır: önceden tanımlanmış türleri (örneğin, `int` veya `void`), boş değer atanabilir türler (`Point?`), dizisi, türlerini (`Customer[,]`), işaretçi türleri (`Buffer*`), diğer koşullu (`A::B` ) ve genel türler ilişkisiz (`Dictionary<,>`), ön işlem sembolleri (`DEBUG`) ve etiketleri (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="7f616-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>

<span data-ttu-id="7f616-123">Tam olarak nitelenmiş adını almak gerekiyorsa, kullanabileceğiniz `typeof` ifadesinin yanı sıra `nameof`.</span><span class="sxs-lookup"><span data-stu-id="7f616-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="7f616-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7f616-124">For example:</span></span>

```csharp
class C {
    void f(int i) {
        Log($"{typeof(C)}.{nameof(f)}", "method entry");
    }
}
```

<span data-ttu-id="7f616-125">Ne yazık ki `typeof` gibi sabit bir ifade değil `nameof`, bu nedenle `typeof` ile birlikte kullanılamaz `nameof` aynı olarak yerleştirir `nameof`.</span><span class="sxs-lookup"><span data-stu-id="7f616-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="7f616-126">Örneğin, aşağıdaki CS0182 derleme hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="7f616-126">For example, the following would cause a CS0182 compile error:</span></span>

```csharp
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

<span data-ttu-id="7f616-127">Örneklerde, bir tür adı kullanın ve bir örnek yöntem adı erişim görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="7f616-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="7f616-128">Türünün bir örneği için gereken değerlendirilen ifadeleri olarak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7f616-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="7f616-129">Tür adı kullanarak, yalnızca adına başvuran ve örnek verileri kullanarak değil, bir örnek değişkeni veya ifade contrive gerekmez bazı durumlarda ve çok kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f616-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>

<span data-ttu-id="7f616-130">Bir sınıf özniteliği ifadelerinde sınıf üyelerinin başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f616-130">You can reference the members of a class in attribute expressions on the class.</span></span>

<span data-ttu-id="7f616-131">Aşağıdaki gibi bir imza bilgileri almak için bir yolu yoktur "`Method1 (str, str)`".</span><span class="sxs-lookup"><span data-stu-id="7f616-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="7f616-132">Bunu yapmanın bir yolu olan bir ifade kullanmanızı `Expression e = () => A.B.Method1("s1", "s2")`ve elde edilen ifadenin ağacından MemberInfo çekin.</span><span class="sxs-lookup"><span data-stu-id="7f616-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="7f616-133">Dil özellikleri</span><span class="sxs-lookup"><span data-stu-id="7f616-133">Language Specifications</span></span>

<span data-ttu-id="7f616-134">Daha fazla bilgi için [Nameof ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f616-134">For more information, see [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="7f616-135">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="7f616-135">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f616-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f616-136">See also</span></span>

- [<span data-ttu-id="7f616-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f616-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7f616-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7f616-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7f616-139">typeof</span><span class="sxs-lookup"><span data-stu-id="7f616-139">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
