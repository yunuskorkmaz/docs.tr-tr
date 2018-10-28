---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae3b72cb5a1281899cdfdb514bbf5a1dc289c949
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454505"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Bu konu, .NET Framework 4'te sunulan Yönetilen Genişletilebilirlik Çerçevesi'ne genel bakış sağlar.

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a>MEF nedir?

MEF ve Yönetilen Genişletilebilirlik Çerçevesi hafif Genişletilebilir uygulamalar oluşturmaya yönelik bir kitaplıktır. Bulmak ve yapılandırma gerektirmeden uzantıları kullanmak, uygulama geliştiricilerinin sağlar. Ayrıca, kolayca kod şifreleyebilir ve kırılgan sabit bağımlılıkları önlemek uzantı geliştiricileri sağlar. MEF değil yalnızca uygulama içinde ancak de uygulamalar arasında yeniden kullanılabilmeleri uzantılar sağlar.

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a>Genişletilebilirlik sorunu
 Genişletilebilirlik için destek sağlayan bir büyük uygulama Mimarı olduğunuzu varsayalım. Uygulamanızı daha küçük bileşenlerden büyük olasılıkla çok sayıda içermek zorundadır ve oluşturma ve bunları çalıştırmak için sorumludur.

 Sorun için en kolay yaklaşım, uygulamanızın kaynak kodunda olarak bileşenleri içerir ve doğrudan kodunuzdan çağırmaya sağlamaktır. Bu, birkaç belirgin dezavantajları vardır. En önemlisi, örneğin, bir Web uygulaması, kabul edilebilir, ancak bir istemci uygulamasında çalışmaz bir kısıtlama kaynak kodunda değişiklik yapmadan yeni bileşenler ekleyemezsiniz. Bunlar sizin erişmesine izin veremez aynı nedenden yanı sıra, üçüncü tarafların geliştirdiği eşit sorunlu, bileşenler için kaynak koduna erişim sahip.

 Bir uzantı noktası ya da arabirim uygulama ve bileşenlerinin bağlantıyı kesmeye izin vermek için biraz daha karmaşık bir yaklaşım olacaktır. Bu modelde, bir bileşen uygulayan bir arabirim ve uygulamanızla etkileşim sağlamak için bir API sağlayabilir. Bu kaynak koduna erişim gerektiren sorununu çözer, ancak yine de zorluklara sahiptir.

 Uygulama bileşenleri kendi bulmak için herhangi bir kapasite eksik olduğundan, bunu hala açıkça hangi bileşenlerin mevcut olduğu ve yüklenmesi gerektiğini söyledik gerekir. Bu genellikle, bir yapılandırma dosyasında açıkça kullanılabilir bileşenleri kaydederek da gerçekleştirilir. Özellikle son kullanıcı ve olmayan bir güncelleştirme yapmak için beklenen geliştiriciye ise kullanıcıysa doğru Bunun anlamı bir bakım sorunu haline gelir.

 Ayrıca, birbirleriyle etkileşime dışında uygulamanın kendisinin aracılığı tanımlanan kanallar iletişim kuramadığı bileşenlerdir. Uygulama Mimarı, belirli bir iletişim için gereken beklemiyorsa, genellikle mümkün değildir.

 Son olarak, bileşen geliştiricileri üzerinde uyguladıkları arabirimi hangi derlemeyi içeren sabit bir bağımlılık kabul etmeniz gerekir. Birden fazla uygulamada kullanılmak üzere bir bileşen zorlaştırır ve bir test çerçevesi bileşenleri için oluşturduğunuzda sorunları da oluşturabilirsiniz.

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a>MEF ne sağlar?
 Kullanılabilir bileşenleri yerine bu açık kaydı MEF örtülü olarak bulmak için bir yol sağlar. aracılığıyla *bileşim*. Adlı bir MEF Bileşeni bir *bölümü*, bildirimli olarak her iki bağımlılıklarını belirtir (olarak bilinen *alır*) ve hangi özellikleri (olarak bilinen *aktarır*) kullanılabilir hale getirir. Bir bölümü oluşturulduğunda, MEF bileştirme altyapısı diğer bölümlerden kullanılabilir olan aktarmaları karşılar.

 Bu yaklaşım önceki bölümde açıklanan sorunları çözer. MEF bölümleri yeteneklerini bildirimli olarak belirttiğinden, çalışma zamanında bulunabilir olmaları sabit kodlanmış başvuruları veya kırılgan yapılandırma dosyalarını olmadan parçalar kullanımını uygulama yapabilir anlamına gelir. MEF uygulamaları bulmak ve bölümleri meta verilerine göre bunları örnekleme veya hatta kendi derlemeleri yükleme incelemek sağlar. Sonuç olarak, dikkatli bir şekilde ne zaman ve nasıl uzantıları yüklenmesi gerektiğini belirtmek için gerek yoktur.

 Sağlanan aktarımlarından yanı sıra bir bölümünü başka parçalar tarafından doldurulacaktır tarafından içeri aktarılanlara belirtebilirsiniz. Bu yapar arasında iletişimi değil yalnızca olası ancak kolay bölümleri ve kodu iyi bir şekilde düzenlenmesini sağlar. Örneğin, birçok bileşen için ortak hizmetler ayrı bir bölüm içinde ve kolayca değiştirilebilir veya değiştirildi.

 MEF modelinin belirli uygulama derlemesine sabit hiçbir bağımlılığı gerektirdiğinden, uygulamadan uygulamaya yeniden kullanılabilmeleri uzantılar sağlar. Bu ayrıca, uygulamayı uzantı bileşenlerini test etmek, bağımsız bir test bandı geliştirmek kolaylaştırır.

 MEF kullanılarak yazılan, Genişletilebilir bir uygulama uzantıları için uygulama hizmetleri kullanıma sunmak için uzantı bileşenleri tarafından da doldurulabilir ve ayrıca bildirebileceği bir içeri aktarır bildirir. Her bir uzantı bileşeni bir dışarı aktarma bildirir ve içeri aktarmaları da bildirebilir. Bu şekilde, uzantı bileşenlerinin kendileri otomatik olarak genişletilebilir.

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a>MEF nerede kullanılabilir?
 MEF bir parçası olan [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], .NET Framework kullanılan her yerde kullanılabilir. Windows Forms, WPF veya diğer herhangi bir teknoloji kullanıp kullanmayacağınızı veya ASP.NET kullanan sunucu uygulamaları, MEF istemci uygulamalarınızda kullanabilirsiniz.

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a>MEF ve MAF
 .NET Framework'ün önceki sürümlerini yönetilen eklenti Framework (yalıtmak ve uzantıları yönetmek uygulamalara izin vermek üzere tasarlanmış MAF), kullanıma sunuldu. Odak noktası, MAF uzantısı yalıtım ve yükleme ve kaldırma MEF'ın odak bulunabilirliği, genişletilebilirlik ve taşınabilirlik ederken derleme odaklanarak, MEF değerinden biraz daha üst düzey. İki çerçeveleri sorunsuz çalışma ve tek bir uygulama hem de yararlanabilir.

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Bir örnek uygulama

MEF neler yapabileceğinizi görmek için en basit yolu, basit bir MEF uygulaması oluşturmaktır. Bu örnekte çok basit hesap makinesi SimpleCalculator adlı oluşturun. "5 + 3" biçiminde temel aritmetik komutları kabul eden bir konsol uygulaması oluşturmak için SimpleCalculator amacı olan veya "6-2" ve doğru yanıtları döndürür. MEF kullanarak, uygulamanın kodunu değiştirmeden yeni işleç eklemek mümkün olacaktır.

Bu örnek için tam kod indirmek için bkz [SimpleCalculator örnek](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).

> [!NOTE]
> MEF sözdizimi ve kavramları göstermek için yerine mutlaka gerçekçi bir senaryo için kullanımını sağlamak için SimpleCalculator amacı budur. Birçok avantaj elde edecektir MEF gücünü en iyi uygulamaları SimpleCalculator daha karmaşıktır. Daha kapsamlı örnekler için bkz: [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) GitHub üzerinde.

- Başlamak için Visual Studio'da yeni bir konsol uygulaması projesi oluşturun ve adlandırın `SimpleCalculator`.

- MEF bulunduğu System.ComponentModel.Composition derlemesine bir başvuru ekleyin.

- Module1.vb veya program.cs'i açın ve eklemek `Imports` veya `using` System.ComponentModel.Composition ve System.ComponentModel.Composition.Hosting deyimleri. Bu iki ad alanlarında, Genişletilebilir bir uygulama geliştirmek için ihtiyacınız olacak MEF türler bulunur.

- Visual Basic kullanıyorsanız, ekleyin `Public` anahtar sözcüğü bildiren satırına `Module1` modülü.

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a>Kapsayıcının ve katalogları

MEF bileşim modeli temel *kapsayıcının*, kullanılabilir tüm parçaları içerir ve oluşturma işlemini gerçekleştirir. Birleşim eşleşen dışarı aktarır, çalışıyor. Kapsayıcının en yaygın türü <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ve bu SimpleCalculator için kullanacaksınız.

Visual Basic kullanıyorsanız Module1.vb adlı bir ortak Sınıf Ekle `Program`.

Aşağıdaki satırı ekleyin `Program` Module1.vb veya Program.cs sınıfında:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Bunun için bileşim kapsayıcılar kullanılabilir bölümleri bulmak için kullanır bir *Kataloğu*. Katalog bölümleri bazı kaynaklardaki kullanılabilir hale getiren bir nesnedir. MEF bölümleri sağlanan türü, bir derleme veya dizin keşfetmenizi sağlar. Uygulama geliştiricileri, bir Web hizmeti gibi diğer kaynaklardan kısımlarını keşfetmek için yeni katalog kolayca oluşturabilirsiniz.

Aşağıdaki oluşturucuyu ekleyin `Program` sınıfı:

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

Çağrı <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> geçerli örneği bu durumda, bölümleri belirli bir dizi oluşturmak için kapsayıcının söyler `Program`. Bu noktada, ancak hiçbir şey, beri olacağını `Program` aktarımlara doldurmak için sahip değildir.

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a>İçeri ve dışarı aktarmalar özniteliklerine sahip
 İlk olarak `Program` hesap makinesi içeri aktarın. Bu kullanıcı ayrımı gibi konsol girdi ve çıktı olacak arabirimi konuları sağlar `Program`, hesaplayıcı mantığından.

 Aşağıdaki kodu ekleyin `Program` sınıfı:

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 Dikkat bildirimi `calculator` nesne olağan dışı değildir ancak ile donatılmış <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği. Bu öznitelik bir bir içe aktarım olarak bildirir; diğer bir deyişle, bir nesne oluşturulduğunda bileşim motoru tarafından doldurulur.

 Her bir içe aktarması yok bir *sözleşme*, eşleştiği ile hangi dışarı belirler. Sözleşmeyi açıkça belirtilen bir dize olabilir ve bu durumda arabirimi belirli bir türden MEF tarafından otomatik olarak da oluşturulabilir `ICalculator`. Eşleşen bir anlaşma ile bildirilen herhangi bir dışarı aktarma, bu içeri aktarma karşılar. Türü unutmayın `calculator` nesnedir, aslında `ICalculator`, bu gerekli değildir. Sözleşmenin alma nesnenin türünden bağımsızdır. (Bu durumda, dışlamayı `typeof(ICalculator)`. MEF otomatik olarak içeri aktarma türüne açıkça belirtmediğiniz sürece alan sözleşme varsayar.)

 Bu çok basit bir arabirim modüle ekleyin veya `SimpleCalculator` ad alanı:

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 Tanımladığınız göre `ICalculator`, onu uygulayan bir sınıf gerekir. Aşağıdaki sınıf modüle ekleyin veya `SimpleCalculator` ad alanı:

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

 Alma eşleşen dışarı aktarma işte `Program`. İçeri aktarma eşleşecek şekilde dışarı aktarma, dışarı aktarma aynı anlaşmaya olması gerekir. Bir sözleşme çerçevesinde verme temel alarak `typeof(MySimpleCalculator)` bir uyumsuzluk oluşturur ve içeri aktarma olmayan doldurulur; sözleşmenin tam olarak eşleşmesi gerekir.

 Bu derlemede, kullanılabilir tüm bölümleri içeren kapsayıcının doldurulur beri `MySimpleCalculator` bölümünü, kullanıma sunulacaktır. Zaman Oluşturucusu `Program` üzerinde birleştirme gerçekleştirir `Program` nesnesi, içeri aktarma ile doldurulur bir `MySimpleCalculator` bu amaç için oluşturulan nesne.

 Kullanıcı arabirim katmanı (`Program`) başka bir şey bilmek gerekmez. Bu nedenle kullanıcı arabirimi mantığı, rest doldurabilirsiniz `Main` yöntemi.

 Aşağıdaki kodu ekleyin `Main` yöntemi:

```vb
Sub Main()
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Bu kod yalnızca bir satır girişi ve iletileriniz okur `Calculate` işlevi `ICalculator` sonucuna konsola geri yazar. İhtiyacınız olan tüm kod `Program`. İşin tüm rest bölümlerinde gerçekleşir.

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a>İçeri aktarmalar ve ImportMany daha iyi
 SimpleCalculator Genişletilebilir olmak üzere, bu işlemlerin bir listesini almak gerekir. Sıradan <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği bir ve yalnızca bir tarafından doldurulur <xref:System.ComponentModel.Composition.ExportAttribute>. Bileşim motoru, birden fazla varsa bir hata oluşturur. Herhangi bir sayıda dışarı aktarmaları doldurulmuş bir içeri aktarma oluşturmak için kullanabileceğiniz <xref:System.ComponentModel.Composition.ImportManyAttribute> özniteliği.

 Aşağıdaki işlemleri özelliği Ekle `MySimpleCalculator` sınıfı:

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <xref:System.Lazy%602> bir türü MEF dışarı aktarma dolaylı başvuruları tutmak için tarafından sağlanır. Burada, dışarı aktarılan nesnenin kendisinin yanı sıra, ayrıca Al *meta verileri dışarı aktarma*, ya da dışarı aktarılan nesnenin açıklayan bilgiler. Her <xref:System.Lazy%602> içeren bir `IOperation` gerçek bir işlemi temsil eden bir nesne ve bir `IOperationData` meta verilerini temsil eden nesne.

 Aşağıdaki basit arabirimleri modüle ekleyin veya `SimpleCalculator` ad alanı:

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 Bu durumda, her işlem için meta veriler gibi bu işlemi temsil eden semboldür +, -, * ve benzeri. Toplama işlemi kullanılabilir yapmak için aşağıdaki sınıf modüle ekleyin veya `SimpleCalculator` ad alanı:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

 <xref:System.ComponentModel.Composition.ExportAttribute> Önce yaptığınız gibi işlevleri özniteliği. <xref:System.ComponentModel.Composition.ExportMetadataAttribute> Özniteliği bu dışarı aktarma için bir ad-değer çiftinin biçiminde meta veriler ekler. Sırada `Add` sınıfının Implements `IOperation`, uygulayan bir sınıf `IOperationData` açıkça tanımlı değil. Bunun yerine, bir sınıf sağlanan meta verilerin adlarına göre özellikleriyle örtük olarak MEF tarafından oluşturulur. (Bir MEF meta verilerinde erişmenin birkaç yolu budur.)

 MEF birleşimde olan *özyinelemeli*. Siz açıkça oluşan `Program` içe nesne, bir `ICalculator` türünde olmasını açık `MySimpleCalculator`. `MySimpleCalculator`, sırasıyla bir koleksiyonunu alır `IOperation` nesneleri ve içeri aktarma ne zaman doldurulur `MySimpleCalculator` aktarımlarının aynı zamanda oluşturulan `Program`. Varsa `Add` sınıfı bildirilen çok doldurulması ve böyle devam etmesi gereken bir başka alma. Herhangi bir birleştirme hatası sol dolgusuz sonuçları alın. (Ancak, isteğe bağlı olacak şekilde veya bunları varsayılan değer atamak için içeri aktarmalar bildirmek için mümkündür.)

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a>Hesaplayıcı mantığı
 Bu bölümleri yerinde, kalan tek şey hesaplayıcı mantığı. Aşağıdaki kodu ekleyin `MySimpleCalculator` uygulamak için sınıfı `Calculate` yöntemi:

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(String input)
{
    int left;
    int right;
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

 İlk adımlarında, sol ve sağ işlenen uygulamasına giriş dizesi ile bir işleç karakter ayrıştırılamıyor. İçinde `foreach` döngü, her üyesi `operations` koleksiyon incelenir. Bu nesnelerin türündedir <xref:System.Lazy%602>, meta veri değerleri ve dışarı aktarılan nesne ile erişilebilir <xref:System.Lazy%602.Metadata%2A> özelliği ve <xref:System.Lazy%601.Value%2A> özelliği sırasıyla. Bu durumda, `Symbol` özelliği `IOperationData` nesne hesaplayıcı çağrıları bir eşleşme olarak bulunursa `Operate` yöntemi `IOperation` nesne ve sonucu döndürür.

 Hesaplayıcı tamamlamak için ayrıca bir dizede ilk basamak olmayan karakterle konumunu döndürür bir yardımcı yöntem gerekir. Eklemek için aşağıdaki yardımcı yöntemini `MySimpleCalculator` sınıfı:

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 Şimdi projeyi derlemek ve çalıştırmak mümkün olması gerekir. Visual Basic'te, eklediğiniz emin `Public` anahtar `Module1`. Konsol penceresinde türü "5 + 3" ve hesap makinesi gibi ek bir işlem sonuçlarını döndürür. Herhangi bir işleç "işlemi bulunamadı!" sonuçları İleti.

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a>Yeni bir sınıf kullanarak SimpleCalculator genişletme
 Hesaplayıcı çalışır, yeni bir işlem eklemek kolaydır. Aşağıdaki sınıf modüle ekleyin veya `SimpleCalculator` ad alanı:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

 Projeyi derlemek ve çalıştırmak. "5-3" gibi bir çıkarma işlemi yazın. Hesaplayıcı, ayrıca yanı sıra çıkarma artık desteklemektedir.

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Yeni bir derleme kullanmakla SimpleCalculator genişletme
 Sınıf ekleme kaynak kod yeterli basittir, ancak MEF bölümleri için bir uygulamanın kendi kaynak dışında görme olanağı sağlar. Bunu göstermek için ekleyerek bölümleri, kendi derleme yanı sıra, bir dizini aranacak SimpleCalculator değiştirmeniz gerekecektir bir <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.

 Adlı yeni bir dizin eklemek `Extensions` SimpleCalculator projeye. Proje düzeyinde ve çözüm düzeyinde eklediğinizden emin olun. Ardından yeni bir sınıf kitaplığı projesi adlı çözüme ekleyin `ExtendedOperations`. Yeni projeyi ayrı bir derleme içine derlenir.

 ExtendedOperations projesi için proje özellikleri Tasarımcısı'nı açın ve tıklayın **derleme** veya **derleme** sekmesi. Değişiklik **yapı çıkış yolu** veya **çıkış yolu** uzantı dizini SimpleCalculator proje dizinine işaret edecek şekilde (.. \SimpleCalculator\Extensions\\).

 Module1.vb veya Program.cs içinde aşağıdaki satırı ekleyin `Program` Oluşturucusu:

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 Örnek yol uzantıları dizininize yoluyla değiştirin. (Yalnızca hata ayıklama için bu mutlak bir yol içindir. Bir üretim uygulamasında, göreli bir yol kullanabilirsiniz.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Uzantı dizini bileştirme kapsayıcısı için tüm derlemelerde bulunan tüm bölümler artık ekleyeceksiniz.

 ExtendedOperations projesinde SimpleCalculator ve System.ComponentModel.Composition başvurular ekleyin. ExtendedOperations sınıf dosyasında, ekleme bir `Imports` veya `using` System.ComponentModel.Composition bildirimi. Visual Basic'te de eklemeniz bir `Imports` SimpleCalculator deyimi. Ardından aşağıdaki sınıf ExtendedOperations sınıfı dosyaya ekleyin:

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

 Bu da sipariş sözleşmesiyle eşleşecek şekilde unutmayın <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği, aynı türde olmalıdır <xref:System.ComponentModel.Composition.ImportAttribute>.

 Projeyi derlemek ve çalıştırmak. Yeni Mod (%) işleci test edin.

<a name="conclusion"></a>
## <a name="conclusion"></a>Sonuç
 Bu konuda, MEF temel kavramlarını ele.

-   Bölümleri ve Katalog bileşim kapsayıcı

     Bölümleri ve kapsayıcının MEF uygulamasının temel yapı taşları şunlardır. Alır ya da en fazla kendisi de dahil bir değer verir herhangi bir nesne bir parçasıdır. Katalog, belirli bir kaynaktan bölümleri koleksiyonu sağlar. Kapsayıcının Kataloğu tarafından sağlanan bölümleri oluşturmak, içeri dışarı aktarmalar bağlaması için kullanır.

-   İçeri ve dışarı aktarmalar

     İçeri ve dışarı aktarmalar bileşenleri tarafından iletişim yoludur. Bir içeri aktarma ile bileşenin belirli bir değer veya nesne için bir gereksinim belirtir ve isteğe bağlı olarak dışa kullanılabilirliğini bir değer belirtir. Her bir içeri aktarma, dışarı aktarmaları sözleşmesi yoluyla listesiyle eşleştirilir.

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a>Burada artık gitmeliyim?
 Bu örnek için tam kod indirmek için bkz [SimpleCalculator örnek](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).

 Daha fazla bilgi ve kod örnekleri için bkz. [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). MEF türlerinin bir listesi için bkz. <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanı.
