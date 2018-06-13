---
title: Lambda İfadeleri (C# Programlama Kılavuzu)
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: f20ba6845a6a84a57fa7636355d08b2f4e5cea2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340651"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda İfadeleri (C# Programlama Kılavuzu)
Lambda ifadesi bir [anonim işlevi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) oluşturmak için kullanabileceğiniz [Temsilciler](../../../csharp/programming-guide/delegates/using-delegates.md) veya [ifade ağacına](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) türleri. Lambda ifadeleri kullanarak, bağımsız değişken yerine geçebilecek veya işlev çağrılarının değeri olarak döndürülebilecek, yerel işlevler yazabilirsiniz. Lambda ifadeleri LINQ sorgu ifadeleri yazmak için özellikle yararlıdır.  
  
 Lambda ifadesi oluşturma için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtmeniz [ => ](../../../csharp/language-reference/operators/lambda-operator.md), ve diğer tarafta ifade veya deyimin blok yerleştirin. Örneğin, lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış. Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:  
  
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
  
 `=>` Atama olarak aynı önceliğe sahip (`=`) ve [sağa ilişkilendirilebilir](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (işleçleri makalenin "Birleşim" bölümüne bakın).  
  
 Lambda'lar yöntemi tabanlı içinde kullanılan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleci yöntemlerinden bağımsız değişken olarak gibi sorgular <xref:System.Linq.Enumerable.Where%2A>.  
  
 Çağrılacak yöntem temelli sözdizimini kullandığınızda <xref:System.Linq.Enumerable.Where%2A> yönteminde <xref:System.Linq.Enumerable> sınıfı (yaptığınız gibi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) bir temsilci türü parametredir <xref:System.Func%602?displayProperty=nameWithType>. Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur. Aynı yönteminde, örneğin, çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> sınıfı (yaptığınız gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) parametre türü ise bir <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> Func olduğu herhangi bir Func temsilcileri en fazla altı giriş parametreleri ile. Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur. Lambda'lar izin `Where` çağrıları aslında lambda oluşturulan nesne türünü farklı olmasına rağmen benzer.  
  
 Önceki örnekte, temsilci imza bir örtük olarak yazılan sahip olmadığına dikkat edin giriş parametresi türü `int`ve döndüren bir `int`. Lambda ifadesi bir giriş parametresi de içerdiğinden bu tür bir temsilciye dönüştürülebilir (`x`) ve derleyici türüne örtük olarak dönüştürebilirsiniz bir dönüş değeri `int`. (Tür çıkarımı, ilerleyen bölümlerde daha ayrıntılı bir şekilde tartışılmıştır.) Temsilci, giriş parametresi 5 kullanılarak çağrıldığında 25 sonucunu döndürür.  
  
 Lambda'lar sol tarafında verilmez [olan](../../../csharp/language-reference/keywords/is.md) veya [olarak](../../../csharp/language-reference/keywords/as.md) işleci.  
  
 Anonim yöntemler için uygulanan tüm kısıtlamalar lambda ifadeleri için de geçerlidir. Daha fazla bilgi için bkz: [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## <a name="expression-lambdas"></a>Lambda İfadeleri  
 Bir lambda ifadesi ile sağ tarafında bir ifade = > işleci adlı bir *lambda ifadesi*. İfade lambdas yaygın yapımı içinde kullanılan [ifade ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b). Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:  
  
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

 Boş ayraçlarla sıfır giriş parametrelerini belirtin:  
  
```csharp
() => SomeMethod()
```

 Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın. Ancak, .NET Framework dışında, örneğin SQL Server'da değerlendirilen ifade ağaçları oluşturuyorsanız, lambda ifadelerinde yöntem çağrısı kullanmamanız gerekir. Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.  
  
## <a name="statement-lambdas"></a>Deyim Lambdaları  
 Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:  
  
(giriş parametreleri) = > {deyimi;}

 Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.  
  
## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar  
 Lambda ifadeleri ve kullanarak zaman uyumsuz işleme dahil deyimleri kolayca oluşturabilirsiniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) ve [await](../../../csharp/language-reference/keywords/await.md) anahtar sözcükler. Örneğin, aşağıdaki Windows Forms örnek çağırır ve bir zaman uyumsuz yöntem bekler bir olay işleyiciyi içeriyor `ExampleMethodAsync`.  
  
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

 Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyici eklemek için Ekle bir `async` lambda parametre listesi, aşağıdaki örnekte gösterildiği gibi önce değiştiricisi.  
  
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

 Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md).  
  
## <a name="lambdas-with-the-standard-query-operators"></a>Standart Sorgu İşlevleriyle Lambda İfadeleri  
 Birçok standart sorgu işleçleri türü olan bir giriş parametresi vardır, <xref:System.Func%602> genel temsilciler ailesi. Bu temsilciler girdi parametrelerinin sayısını ve türünü ve temsilcinin döndürdüğü değerin türünü tanımlamak için tür parametreleri kullanır. `Func` Temsilciler kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadeleri kapsüllemek için çok kullanışlıdır. Örneğin, aşağıdaki temsilci türünü göz önünde bulundurun:  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 Temsilci olarak oluşturulabilir `Func<int,bool> myFunc` nerede `int` giriş parametresidir ve `bool` dönüş değeri. Dönüş değeri her zaman son tür parametresinde belirtilir. `Func<int, string, bool>` iki girdi parametresi ile bir temsilci tanımlar `int` ve `string`ve dönüş türü `bool`. Aşağıdaki `Func` temsilci çağrıldığında, döndürecektir true veya false giriş parametresi 5'e eşit olup olmadığını belirtin:  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Bağımsız değişken türü olduğunda, aynı zamanda bir lambda ifadesi sağlayabilir bir `Expression<Func>`, örneğin System.Linq.Queryable içinde tanımlanan standart sorgu işleçleri içinde. Belirttiğinizde bir `Expression<Func>` bağımsız değişkeni, bir ifade ağacına lambda derlenecek.  
  
 Standart sorgu işleci <xref:System.Linq.Enumerable.Count%2A> yöntemi, burada gösterilmiştir:  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi bu tamsayılar sayar (`n`), iki tarafından ayrılmış 1 kalanı vardır.  
  
 Aşağıdaki kod satırını tüm öğeleri içeren bir dizisi üretir `numbers` 9 sol tarafına bu koşulu karşılamıyor sıradaki ilk sayı olduğundan olan dizi:  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 Bu örnek birden fazla giriş parametrelerini paranteze alarak belirtmeyi gösterir. Yöntem, değeri konumundan daha az olan bir sayı ile karşılaşana dek sayı dizisindeki tüm öğeleri döndürür. Lambda işleci karıştırmayın (`=>`) değerinden büyük veya eşit işleciyle (`>=`).  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>Lambda İçinde Tür Çıkarımı  
 Lambda ifadeleri yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez; derleyici lambda gövdesine, parametrenin temsilci türüne ve C# Dil Belirtimi'nde açıklanan diğer etkenlere göre türü çıkarsayabilir. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Bunu, sorgu oluşturuyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olarak algılanır sonra bir `Customer` erişiminiz yöntemleri ve özellikleri anlamına gelir nesnesi:  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 Lambdalar için genel kurallar şunlardır:  
  
-   Lambda temsilci türüyle aynı sayıda parametre içermelidir.  
  
-   Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.  
  
-   Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.  
  
 Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın. Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır. Bu durumlarda türü temsilci türüne başvuruyor veya <xref:System.Linq.Expressions.Expression> yazın lambda ifadesi dönüştürülen.  
  
## <a name="variable-scope-in-lambda-expressions"></a>Lambda İfadelerinde Değişken Kapsamı  
 Lambda'lar başvurabilir *dış değişkenleri* (bkz [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) lambda işlevi tanımlar yöntemi kapsamında olan ya da lambda ifadesi içeren kapsamında yazın. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir:  
  
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
  
-   Lambda ifadesi doğrudan yakalayamazsınız bir `in`, `ref`, veya `out` kapsayan bir yöntem parametresi.  
  
-   Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.  
  
-   Lambda ifadesi içeremez bir `goto` deyimi, `break` deyimi veya `continue` atlama deyiminin hedef dışında blok ise, lambda işlevinde deyimi. Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>Özel Kitap Bölümü  
 [Temsilciler ve olaylar Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Kılavuzu, üçüncü baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [LINQ (dil ile tümleşik sorgu)](../../../csharp/programming-guide/concepts/linq/index.md)  
 [Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [İfade Ağaçları](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Visual Studio 2008 C# örnekleri (bkz: LINQ örnek sorgular dosyaları ve XQuery program)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [Özyinelemeli lambda ifadeleri](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
