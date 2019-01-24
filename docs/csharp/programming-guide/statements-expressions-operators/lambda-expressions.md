---
title: Lambda ifadeleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 91d972f468f80c509a90ea293937b117d54a2e7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737526"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda ifadeleri (C# Programlama Kılavuzu)

Bir lambda ifadesi; bir [anonim işlev](anonymous-methods.md) oluşturmak için kullanabileceğiniz [Temsilciler](../delegates/using-delegates.md) veya [ifade ağacı](../concepts/expression-trees/index.md) türleri. Lambda ifadeleri kullanarak, bağımsız değişken yerine geçebilecek veya işlev çağrılarının değeri olarak döndürülebilecek, yerel işlevler yazabilirsiniz. Lambda ifadeleri LINQ sorgu ifadeleri yazmak için özellikle yararlıdır.
  
Bir lambda ifadesi oluşturmak için giriş parametrelerini (varsa) lambda işlecinin sol tarafında belirttiğiniz [ => ](../../../csharp/language-reference/operators/lambda-operator.md), ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirin. Örneğin, lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış. Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 Bir ifade ağacı türü oluşturmak için:  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 `=>` İşleci atamayla aynı önceliğe sahip (`=`) ve [sağdan birleşir](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (işleçler makalesindeki "Birleşme" bölümüne bakın).  
  
 Lambda ifadeleri yöntem tabanlı kullanılan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] gibi sorgularında standart sorgu işleci yöntemlerinin bağımsız değişkenleri olarak <xref:System.Linq.Enumerable.Where%2A>.  
  
 Çağırmak için yöntem tabanlı sözdizimi kullandığınızda <xref:System.Linq.Enumerable.Where%2A> yönteminde <xref:System.Linq.Enumerable> sınıfı (yaptığınız gibi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) parametre temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType>. Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur. Aynı yöntemi örneğin çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> sınıfı (yaptığınız gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) parametre türü bir <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> burada Func, on altı adede kadar giriş parametresi Func temsilcilerinden biridir. Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur. Lambdalar izin `Where` çağrılarının benzer görünmesine, aslında lambdadan oluşturulan nesnenin türü farklı olsa.  
  
 Önceki örnekte, temsilci imzasında örtük olarak dikkat edin giriş parametresi türü `int`ve döndüren bir `int`. Lambda ifadesi bu türden bir temsilciye dönüştürülebilir çünkü ayrıca bir giriş parametresi vardır (`x`) ve derleyicinin dolaylı olarak türüne çevirebildiği bir dönüş değeri `int`. (Tür çıkarımı, ilerleyen bölümlerde daha ayrıntılı bir şekilde tartışılmıştır.) Temsilci, giriş parametresi 5 kullanılarak çağrıldığında 25 sonucunu döndürür.  
  
 Lambda ifadeleri, sol tarafında verilmez [olduğu](../../../csharp/language-reference/keywords/is.md) veya [olarak](../../../csharp/language-reference/keywords/as.md) işleci.  
  
 Anonim yöntemler için uygulanan tüm kısıtlamalar lambda ifadeleri için de geçerlidir. Daha fazla bilgi için [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## <a name="expression-lambdas"></a>Expression lambdas

 Bir lambda ifadesi işlecin sağ tarafındaki bir ifadeyle = > işleci çağrıldığında bir *lambda ifadesi*. İfade lambdaları oluşumunu oluşturulurken sıkça kullanılır [ifade ağaçları](../concepts/expression-trees/index.md). Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:
  
```csharp
(input-parameters) => expression
```

 Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir. İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:  
  
```csharp
(x, y) => x == y
```

 Bazen derleyicinin giriş türlerini çıkarması zor veya imkansız olabilir. Bu durumda türleri aşağıdaki örnekte olduğu gibi açıkça belirtebilirsiniz:  
  
```csharp
(int x, string s) => s.Length > x
```
 Giriş parametre türlerinin tümü explicit veya tümü implicit olmalıdır; Aksi takdirde, C# oluşturur bir [CS0748](../../misc/cs0748.md) derleyici hatası.

 Boş ayraçlarla sıfır giriş parametrelerini belirtin:  
  
```csharp
() => SomeMethod()
```

 Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın. Ancak, .NET Framework dışında, örneğin SQL Server'da değerlendirilen ifade ağaçları oluşturuyorsanız, lambda ifadelerinde yöntem çağrısı kullanmamanız gerekir. Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.  
  
## <a name="statement-lambdas"></a>Deyim lambdaları

 Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:  
  
(giriş parametreleri) = > {deyimi;}

 Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.  
  
[!code-csharp[StatementLamba#1](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#2)]

 Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.  
  
## <a name="async-lambdas"></a>Async lambdas

 İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) ve [await](../../../csharp/language-reference/keywords/await.md) anahtar sözcükleri. Örneğin, aşağıdaki Windows Forms örneği, çağıran ve bekleyen zaman uyumsuz bir yöntem, bir olay işleyici içerir `ExampleMethodAsync`.  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için Ekle bir `async` aşağıdaki örnekte göründüğü gibi lambda parametre listesinden önce değiştiricisi.  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md).  
  
## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile lambda ifadeleri

 Standart sorgu işleçlerinin çoğu, türü bir giriş parametresine sahiptir, <xref:System.Func%602> Genel temsilci ailesinden olan. Bu temsilciler girdi parametrelerinin sayısını ve türünü ve temsilcinin döndürdüğü değerin türünü tanımlamak için tür parametreleri kullanır. `Func` Temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadelerin Kapsüllenmesi için son çok yararlı olur. Örneğin, aşağıdaki temsilci türünü göz önünde bulundurun:  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 Temsilci olarak oluşturulabilir `Func<int,bool> myFunc` burada `int` giriş parametresi, ve `bool` dönüş değeridir. Dönüş değeri her zaman son tür parametresinde belirtilir. `Func<int, string, bool>` iki giriş parametrelerini içeren bir temsilci tanımlar `int` ve `string`ve bir dönüş türü `bool`. Aşağıdaki `Func` temsilcisi çağrıldığında, true ya da giriş parametresinin 5'e eşit olup olmadığını belirtmek için false döndürür:  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Ayrıca bağımsız değişken türü bir lambda ifadesi sağlayabilirsiniz bir `Expression<Func>`, örneğin işleçlerinde tanımlı System.Linq.queryable standart sorgu işleçleri içinde. Belirttiğinizde bir `Expression<Func>` bağımsız değişkeni, lambda ifade ağacında derlenecek.  
  
 Standart sorgu işleci <xref:System.Linq.Enumerable.Count%2A> yöntemi burada gösterilmektedir:  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi tamsayıları sayar (`n`), ikiye bölündüğünde 1 kalan sahip.  
  
 Aşağıdaki kod satırını tüm öğelerini içeren bir dizi üretir `numbers` , dizisinde koşulu sağlamayan ilk sayı olduğundan 9 sol tarafına olan dizi:  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 Bu örnek birden fazla giriş parametrelerini paranteze alarak belirtmeyi gösterir. Yöntem, değeri konumundan daha az olan bir sayı ile karşılaşana dek sayı dizisindeki tüm öğeleri döndürür. Lambda işlecini karıştırmayın (`=>`) büyüktür veya eşittir işleciyle (`>=`).  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>Lambda içinde tür çıkarımı

 Lambda ifadeleri yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez; derleyici lambda gövdesine, parametrenin temsilci türüne ve C# Dil Belirtimi'nde açıklanan diğer etkenlere göre türü çıkarsayabilir. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Sorguluyorsanız bunu bir `IEnumerable<Customer>`, giriş değişkeni olması sorguluyorsanız bir `Customer` nesne erişim yöntemleri ve özellikleri iznine sahip olduğunuz anlamına gelir:  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 Lambdalar için genel kurallar şunlardır:  
  
-   Lambda temsilci türüyle aynı sayıda parametre içermelidir.  
  
-   Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.  
  
-   Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.  
  
 Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın. Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır. Bu gibi durumlarda, tür temsilci türüne başvuruyor. veya <xref:System.Linq.Expressions.Expression> , lambda ifadesinin dönüştürüldüğü yazın.  
  
## <a name="variable-scope-in-lambda-expressions"></a>Lambda ifadelerinde değişken kapsamı

 Lambdalar başvurabilir *dış değişkenlere* (bkz [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)), lambda işlevini tanımlayan yöntemin kapsamındaki ya da lambda ifadesini içeren türün kapsamındaki. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir:  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:  
  
-   Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.  
  
-   Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.  
  
-   Bir lambda ifadesini doğrudan yakalayamaz bir `in`, `ref`, veya `out` parametresi kapsayan bir yöntemden alınan.  
  
-   Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.  
  
-   Bir lambda ifadesi içeremez bir `goto` deyimi `break` deyimi veya `continue` varsa atlama bildiriminin hedefi blok dışındaysa lambda işlevi içinde deyimi. Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.  
  
## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>Özel Kitap bölümü

 [Temsilciler, olayları ve Lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) içinde [ C# 3.0 Cookbook, Third Edition: İçin 250'den fazla çözüm C# 3.0 programcıları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [LINQ (dil ile tümleşik sorgu)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [İfade Ağaçları](../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio 2008 C# örnekleri (bkz: LINQ örnek sorgular dosyalar ve XQuery programı)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Yinelemeli lambda ifadeleri](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
