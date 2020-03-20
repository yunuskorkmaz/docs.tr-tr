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
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181280"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Bu konu, .NET Framework 4'te tanıtılan Yönetilen Genişletilebilirlik Çerçevesi'ne genel bir bakış sağlar.

## <a name="what-is-mef"></a>MEF nedir?

Yönetilen Genişletilebilirlik Çerçevesi veya MEF, hafif ve genişletilebilir uygulamalar oluşturmak için bir kitaplıktır. Uygulama geliştiricilerin yapılandırma gerektirmeden uzantıları keşfetmesine ve kullanmasına olanak tanır. Ayrıca, uzantı geliştiricilerin kodu kolayca kapsüllemelerini ve kırılgan sert bağımlılıklardan kaçınmalarını sağlar. MEF uzantıların yalnızca uygulamalar içinde değil, uygulamalar arasında da yeniden kullanılmasına izin verir.

## <a name="the-problem-of-extensibility"></a>Genişletilebilirlik sorunu

Genişletilebilirlik için destek sağlaması gereken büyük bir uygulamanın mimarı olduğunuzu düşünün. Uygulamanız, potansiyel olarak çok sayıda küçük bileşen içermelidir ve bunları oluşturmak ve çalıştırmaktan sorumludur.

Soruna en basit yaklaşım, bileşenleri uygulamanıza kaynak kodu olarak eklemek ve bunları doğrudan kodunuzdan çağırmaktır. Bunun bariz dezavantajları vardır. En önemlisi, kaynak kodu değiştirmeden yeni bileşenler ekleyemezsiniz, örneğin bir Web uygulamasında kabul edilebilir bir kısıtlama, ancak istemci uygulamasında kullanılamaz. Aynı derecede sorunlu, bileşenlerin kaynak koduna erişiminiz olmayabilir, çünkü bunlar üçüncü taraflarca geliştirilebilir ve aynı nedenle sizinkine erişmelerine izin veremezsiniz.

Biraz daha karmaşık bir yaklaşım, uygulama ve bileşenleri arasında ayrıştırma izin vermek için bir uzantı noktası veya arabirim sağlamak olacaktır. Bu modelaltında, bir bileşenin uygulayabileceği bir arabirim ve uygulamanızla etkileşimkurmasını sağlamak için bir API sağlayabilirsiniz. Bu, kaynak kodu erişimi gerektiren sorunu çözer, ancak yine de kendi zorlukları vardır.

Uygulama bileşenleri kendi başına keşfetmek için herhangi bir kapasiteye sahip olmadığından, yine de hangi bileşenlerin kullanılabilir olduğu ve yüklenmesi gerektiği açıkça söylenmelidir. Bu genellikle kullanılabilir bileşenleri bir yapılandırma dosyasına açıkça kaydederek gerçekleştirilir. Bu, bileşenlerin doğru olduğundan güvence verilmesinin, özellikle güncelleştirmeyi yapması beklenen geliştirici değil, son kullanıcı ysa, bir bakım sorunu haline gelmesi anlamına gelir.

Buna ek olarak, bileşenler, uygulamanın kendisinin katı olarak tanımlanmış kanalları dışında birbirleriyle iletişim kuramaz. Uygulama mimarı belirli bir iletişim gereksinimini tahmin etmemişse, bu genellikle imkansızdır.

Son olarak, bileşen geliştiricilerin uyguladıkları arabirimi içeren derlemeye sıkı bir bağımlılık kabul etmesi gerekir. Bu, bir bileşenin birden fazla uygulamada kullanılmasını zorlaştırır ve bileşenler için bir test çerçevesi oluşturduğunuzda da sorun yaratabilir.

## <a name="what-mef-provides"></a>MEF'in sağladığı

Kullanılabilir bileşenlerin bu açık kaydı yerine, MEF *bunları kompozisyon*aracılığıyla dolaylı olarak keşfetmenin bir yolunu sağlar. Bir MEF bileşeni, bir *parçası*olarak adlandırılan, bildirimsel hem bağımlılıkları *(içeri aktarma*olarak bilinir) ve hangi yetenekleri *(dışa*aktarma olarak bilinir) o kullanılabilir hale belirtir. Bir parça oluşturulduğunda, MEF kompozisyon motoru diğer parçalardan elde edilebilecek lerle ithalatını karşılar.

Bu yaklaşım, önceki bölümde tartışılan sorunları çözer. MEF parçaları yeteneklerini bildirimsel olarak belirttiğinden, çalışma zamanında bulunabilirler, bu da bir uygulamanın sabit kodlanmış başvurular veya kırılgan yapılandırma dosyaları olmadan parçaları kullanabileceği anlamına gelir. MEF, uygulamaların parçaları meta verilerine göre, anlık olarak oluşturmadan ve hatta derlemelerini yüklemeden keşfetmelerine ve incelemelerine olanak tanır. Sonuç olarak, uzantıların ne zaman ve nasıl yüklenmesi gerektiğini dikkatlice belirtmenize gerek yoktur.

Sağlanan dışa aktarımlarına ek olarak, bir kısmı diğer parçalar tarafından doldurulacak olan ithalatını belirtebilir. Bu, parçalar arasındaki iletişimi yalnızca mümkün değil, aynı zamanda kolay hale getirir ve kodun iyi bir şekilde faktoringine olanak tanır. Örneğin, birçok bileşende ortak olan hizmetler ayrı bir parçaya ayrılabilir ve kolayca değiştirilebilir veya değiştirilebilir.

MEF modeli belirli bir uygulama derlemesine sabit bağımlılık gerektirmediği için, uzantıların uygulamadan uygulamaya yeniden kullanılmasına izin verir. Bu, uzantı bileşenlerini test etmek için uygulamadan bağımsız bir test kayışı geliştirmeyi de kolaylaştırır.

MEF kullanılarak yazılmış genişletilebilir bir uygulama, uzantı bileşenleri tarafından doldurulabilen bir alma işlemi bildirir ve uygulama hizmetlerini uzantılara maruz bırakmak için dışa aktarımlar da bildirebilir. Her uzantı bileşeni bir dışa aktarım bildirir ve ayrıca içeri aktarımlar da beyan edebilir. Bu şekilde, uzantı bileşenlerinin kendileri otomatik olarak genişletilebilir.

## <a name="where-mef-is-available"></a>MEF'in mevcut olduğu yerler

MEF ,NET Framework 4'ün ayrılmaz bir parçasıdır ve .NET Framework'ün kullanıldığı her yerde kullanılabilir. İstemci uygulamalarınızda, windows formlarını, WPF'yi veya başka bir teknolojiyi kullanıp kullanmadıklarını veya ASP.NET kullanan sunucu uygulamalarında MEF'i kullanabilirsiniz.

## <a name="mef-and-maf"></a>MEF ve MAF

.NET Framework'ün önceki sürümlerinde, uygulamaların uzantıları yalıtmalarına ve yönetmelerine olanak sağlamak üzere tasarlanmış Yönetilen Eklenti Çerçevesi (MAF) sunulmuştur. MAF'nin odak noktası MEF'ten biraz daha yüksektir, uzatma yalıtımı ve montaj yükleme ve boşaltma üzerine yoğunlaşırken, MEF'in odak noktası keşfedilebilirlik, genişletilebilirlik ve taşınabilirliktir. İki çerçeve sorunsuz bir şekilde çalışır ve tek bir uygulama her ikiden de yararlanabilir.

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Örnek bir uygulama

MEF'in neler yapabileceğini görmenin en basit yolu basit bir MEF uygulaması oluşturmaktır. Bu örnekte, SimpleCalculator adlı çok basit bir hesap makinesi oluşturursunuz. SimpleCalculator'ın amacı, temel aritmetik komutları "5+3" veya "6-2" şeklinde kabul eden ve doğru yanıtları döndüren bir konsol uygulaması oluşturmaktır. MEF kullanarak, uygulama kodunu değiştirmeden yeni işleçler ekleyebilirsiniz.

Bu örnek için tam kodu indirmek için [SimpleCalculator örneğine (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/)bakın.

> [!NOTE]
> SimpleCalculator amacı mutlaka kullanımı için gerçekçi bir senaryo sağlamak yerine, MEF kavramları ve sözdizimi göstermektir. MEF'in gücünden en çok yararlanacak uygulamaların çoğu SimpleCalculator'dan daha karmaşıktır. Daha kapsamlı örnekler için GitHub'daki [Yönetilen Genişletilebilirlik Çerçevesi'ne](https://github.com/MicrosoftArchive/mef) bakın.

- Başlamak için Visual Studio'da yeni bir Konsol `SimpleCalculator`Uygulaması projesi oluşturun ve adını adlandırın.

- MEF'in `System.ComponentModel.Composition` bulunduğu derlemeye bir başvuru ekleyin.

- *Open Module1.vb* veya *Program.cs* ve `System.ComponentModel.Composition` `System.ComponentModel.Composition.Hosting`eklemek `Imports` veya `using` ifadeler için ve . Bu iki ad alanı, genişletilebilir bir uygulama geliştirmek için gereken MEF türleri içerir.

- Visual Basic kullanıyorsanız, `Public` `Module1` modülü bildiren satıra anahtar kelimeyi ekleyin.

## <a name="composition-container-and-catalogs"></a>Kompozisyon konteyner ve kataloglar

MEF kompozisyon modelinin çekirdeği, mevcut tüm parçaları içeren ve kompozisyon gerçekleştiren kompozisyon kapsayıcısır. *composition container* Kompozisyon, ithalatın dışa aktarımla eşleştirilmesidir. Kompozisyon kapsayıcıen yaygın <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>türü, ve SimpleCalculator için bu kullanacağız.

Visual Basic kullanıyorsanız, `Program` *Module1.vb'de*adlandırılmış bir genel sınıf ekleyin.

*Module1.vb* veya `Program` *Program.cs*sınıfa aşağıdaki satırı ekleyin:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Kullanılabilir parçaları keşfetmek için, kompozisyon kapları bir *katalog*kullanır. Katalog, bazı kaynaktan kullanılabilir parçaları n için kullanılabilir kılan bir nesnedir. MEF, sağlanan bir tür, derleme veya dizin parçaları keşfetmek için kataloglar sağlar. Uygulama geliştiricileri, Web hizmeti gibi diğer kaynaklardan parçaları kolayca keşfetmek için yeni kataloglar oluşturabilir.

Sınıfa aşağıdaki oluşturucuekleyin: `Program`

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
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

Çağrı, <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> kompozisyon kapsayıcısına belirli bir parça kümesi oluşturmasını `Program`söyler, bu durumda geçerli durumda . Ancak bu noktada, hiçbir şey `Program` olmayacak, çünkü hiçbir ithalat doldurmak zorunda.

## <a name="imports-and-exports-with-attributes"></a>Öznitelikleri ile İthalat ve İhracat

İlk olarak, `Program` bir hesap makinesi alma var. Bu, kullanıcı arabirimi endişelerinin ayrılmasına olanak sağlar, örneğin `Program`konsol girişi ve hesap makinesi nin mantığından girecek çıktı.

`Program` Sınıfa aşağıdaki kodu ekleyin:

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

`calculator` Nesnenin bildiriminin olağandışı olmadığını, ancak öznitelik ile <xref:System.ComponentModel.Composition.ImportAttribute> süslenmiş olduğuna dikkat edin. Bu öznitelik bir şey bir alma olarak bildirir; diğer bir de, nesne oluşturulduğunda kompozisyon motoru tarafından doldurulacaktır.

Her ithalat, hangi ihracatile eşleşeceğini belirleyen bir *sözleşmeye*sahiptir. Sözleşme açıkça belirtilen bir dize olabilir veya otomatik olarak belirli bir tür MEF tarafından `ICalculator`oluşturulabilir, Bu durumda arayüzü . Eşleşen bir sözleşme ile beyan edilen herhangi bir ihracat bu alma yerine getirecektir. `calculator` Nesnenin türü aslında `ICalculator`olsa da, bu gerekli değildir unutmayın. Sözleşme, içe aktarma nesnesinin türünden bağımsızdır. (Bu durumda, dışarıda bırakabilirsiniz `typeof(ICalculator)`. MEF, açıkça belirtmediğiniz sürece sözleşmenin alma türüne göre otomatik olarak kabul edilecektir.)

Modüle veya `SimpleCalculator` ad alanına bu çok basit arabirimi ekleyin:

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

Artık tanımladığınız `ICalculator`için, bunu uygulayan bir sınıfa ihtiyacınız vardır. Modüle veya `SimpleCalculator` ad alanına aşağıdaki sınıfı ekleyin:

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

İşte ithalatla eşleşecek `Program`ihracat. İhracatın içe aktarılamasıyla eşleşebilmesi için, ihracatın aynı sözleşmeye sahip olması gerekir. Dayalı bir sözleşme kapsamında `typeof(MySimpleCalculator)` ihracat bir uyumsuzluk üretecek ve ithalat doldurulmaz; sözleşmetam olarak eşleşmesi gerekir.

Kompozisyon kapsayıcısı bu derlemede bulunan tüm parçalarla doldurulacağı için, `MySimpleCalculator` parça kullanılabilir olacaktır. Nesne üzerinde `Program` `Program` kompozisyon gerçekleştiren oluşturucu, içe aktarma bu `MySimpleCalculator` amaç için oluşturulacak bir nesne ile doldurulur.

Kullanıcı arabirimi`Program`katmanı ( ) başka bir şey bilmek gerekmez. Bu nedenle `Main` yöntemde kullanıcı arabirimi mantığının geri kalanını doldurabilirsiniz.

`Main` yöntemine aşağıdaki kodu ekleyin:

```vb
Sub Main()
    ' Composition is performed in the constructor.
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
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Bu kod sadece bir giriş satırı `Calculate` okur `ICalculator` ve konsola geri yazdığı sonucun işlevini çağırır. İhtiyacın olan tüm kod `Program`bu. İşin geri kalanı parçalarhalinde olacak.

## <a name="further-imports-and-importmany"></a>Diğer İthalat ve İthalatMany

SimpleCalculator'nin genişletilebilmesi için bir işlem listesi alması gerekir. Sıradan <xref:System.ComponentModel.Composition.ImportAttribute> bir öznitelik bir ve <xref:System.ComponentModel.Composition.ExportAttribute>yalnızca bir tarafından doldurulur. Birden fazla kullanılabilir varsa, kompozisyon motoru bir hata üretir. Herhangi bir sayıda dışa aktarılabilen bir alma <xref:System.ComponentModel.Composition.ImportManyAttribute> işlemi oluşturmak için özniteliği kullanabilirsiniz.

Sınıfa aşağıdaki işlemler `MySimpleCalculator` özelliğini ekleyin:

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<xref:System.Lazy%602>mef tarafından ihracata dolaylı referanslar tutmak için sağlanan bir türdür. Burada, dışa aktarılan nesnenin kendisine ek olarak, *dışa aktarma meta verileri*veya dışa aktarılan nesneyi açıklayan bilgiler de alırsınız. Her <xref:System.Lazy%602> biri, `IOperation` gerçek bir işlemi temsil `IOperationData` eden bir nesne ve meta verilerini temsil eden bir nesne içerir.

Modüle veya `SimpleCalculator` ad alanına aşağıdaki basit arabirimleri ekleyin:

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
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

 Bu durumda, her işlem için meta veri , +, -, \*, gibi bu işlemi temsil eden simgedir. Ekleme işlemini kullanılabilir hale getirmek için, modüle veya `SimpleCalculator` ad alanına aşağıdaki sınıfı ekleyin:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

Öznitelik <xref:System.ComponentModel.Composition.ExportAttribute> daha önce olduğu gibi çalışır. Öznitelik, <xref:System.ComponentModel.Composition.ExportMetadataAttribute> bu dışa aktarıma ad değeri çifti biçiminde meta verileri bağlar. `Add` Sınıf uygular `IOperation`ken, uygulayan `IOperationData` bir sınıf açıkça tanımlanmamıştır. Bunun yerine, bir sınıf örtülü mef tarafından sağlanan meta veri adlarını dayalı özellikleri ile oluşturulur. (Bu, MEF'deki meta verilere erişmenin birkaç yollarından biridir.)

MEF kompozisyon *özyinelemeli.* Açıkça bir tür `Program` `MySimpleCalculator`olduğu ortaya `ICalculator` çıktı bir içe aktarılan nesne, besteledi. `MySimpleCalculator`, sırayla, `IOperation` nesnelerin bir koleksiyon alır ve bu `MySimpleCalculator` alma oluşturulduğunda doldurulur, aynı `Program`zamanda ithalat olarak. `Add` Sınıf daha fazla alma beyan ederse, bu da doldurulması gerekir, ve benzeri. Doldurulmamış kalan tüm alma işlemi kompozisyon hatasına neden olabilir. (Ancak, içeri aktarımları isteğe bağlı olarak beyan etmek veya varsayılan değerler atamak mümkündür.)

## <a name="calculator-logic"></a>Hesap Makinesi Mantığı

Bu parçalar yerinde, geriye kalan tek şey hesap makinesi mantığının kendisidir. Yöntemi uygulamak için `MySimpleCalculator` sınıfa aşağıdaki kodu ekleyin: `Calculate`

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
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
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
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

İlk adımlar, giriş dizesini sol ve sağ operandlara ve bir işleç karakterine ayrışturur. Döngüde, `foreach` koleksiyonun `operations` her üyesi incelenir. Bu nesneler türündendir <xref:System.Lazy%602>ve meta veri değerleri ve dışa <xref:System.Lazy%602.Metadata%2A> aktarılan nesne <xref:System.Lazy%601.Value%2A> sırasıyla özellik ve özellik ile erişilebilir. `Symbol` Bu durumda, nesnenin `IOperationData` özelliği eşleşebilir olarak keşfedilirse, hesap `Operate` makinesi nesnenin yöntemini `IOperation` çağırır ve sonucu döndürür.

Hesap makinesini tamamlamak için, bir dizedeki ilk basamaksız karakterin konumunu döndüren bir yardımcı yöntemine de ihtiyacınız vardır. Sınıfa aşağıdaki yardımcı yöntemi `MySimpleCalculator` ekleyin:

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

Artık projeyi derleyip çalıştırabilmelisin. Visual Basic'te, anahtar kelimeyi `Public` ' `Module1`ye eklediğinizden emin olun Konsol penceresinde, "5+3" gibi bir ekleme işlemi yazın ve hesap makinesi sonuçları döndürür. Başka bir operatör "İşlem Bulunamadı!" iletisi döndürmektedir.

## <a name="extending-simplecalculator-using-a-new-class"></a>Yeni bir sınıf kullanarak SimpleCalculator'ı genişletme

Artık hesap makinesi çalıştığıiçin, yeni bir işlem eklemek kolaydır. Modüle veya `SimpleCalculator` ad alanına aşağıdaki sınıfı ekleyin:

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

Projeyi derle ve çalıştır. "5-3" gibi bir çıkarma işlemi yazın. Hesap makinesi artık çıkarmanın yanı sıra eklemeyi de destekler.

## <a name="extending-simplecalculator-using-a-new-assembly"></a>Yeni bir derleme kullanarak SimpleCalculator'ı genişletme

Kaynak koduna sınıf eklemek yeterince basittir, ancak MEF, bir uygulamanın kendi kaynağının dışına parçalar için bakma olanağı sağlar. Bunu göstermek için, bir dizin aramak için SimpleCalculator değiştirmek gerekir, yanı sıra kendi <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>derleme, parçalar için, ekleyerek .

SimpleCalculator projesine `Extensions` yeni bir dizin ekleyin. Çözüm düzeyinde değil, proje düzeyinde eklediğinizden emin olun. Ardından çözüme yeni bir Sınıf Kitaplığı projesi ekleyin. `ExtendedOperations` Yeni proje ayrı bir derleme halinde derlenecek.

Genişletilmiş İşlemler projesi için Proje Özellikleri Tasarımcısı'nı açın ve **Derleme** veya **Oluştur** sekmesini tıklatın. SimpleCalculator proje dizinindeki Uzantılar dizinine işaret etmek için **Çıktı Veya** Çıktı **yolunu** değiştirin (*... \SimpleCalculator\Uzantılar).\\*

 *Module1.vb* veya *Program.cs'* de, `Program` oluşturucuya aşağıdaki satırı ekleyin:

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

Örnek yolu Uzantılar dizininize giden yolile değiştirin. (Bu mutlak yol sadece hata ayıklama amacıyladır. Bir üretim uygulamasında, göreli bir yol kullanırsınız.) Şimdi <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> kompozisyon kapsayıcısına Uzantılar dizininde bulunan herhangi bir parça eklenecektir.

Genişletilmiş Operasyonlar projesinde, SimpleCalculator ve System.ComponentModel.Composition'a göndermeler ekleyin. ExtendedOperations sınıf dosyasında System.ComponentModel.Composition için bir `Imports` açıklama veya deyim `using` ekleyin. Visual Basic'te SimpleCalculator için bir `Imports` deyim de ekleyin. Ardından ExtendedOperations sınıf dosyasına aşağıdaki sınıfı ekleyin:

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
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

Sözleşmenin eşleşebilmesi için özniteliğin <xref:System.ComponentModel.Composition.ExportAttribute> . <xref:System.ComponentModel.Composition.ImportAttribute>

Projeyi derle ve çalıştır. Yeni Mod test edin (%) Işleç.

## <a name="conclusion"></a>Sonuç

Bu konu MEF'in temel kavramlarını kapsamaktadır.

- Parçalar, kataloglar ve kompozisyon konteyneri

     Parçalar ve bileşim konteyneri bir MEF uygulamasının temel yapı taşlarıdır. Bir parça, kendisine kadar ve kendisi de dahil olmak üzere bir değer içe aktaran veya dışa aktaran herhangi bir nesnedir. Katalog, belirli bir kaynaktan parçalar koleksiyonu sağlar. Kompozisyon kapsayıcıkompozisyon gerçekleştirmek için bir katalog tarafından sağlanan parçaları kullanır, dışa aktarımbağlama.

- İthalat ve ihracat

     İthalat ve dışaaklar, bileşenlerin iletişim kurma yoludur. Bir alma ile bileşen, belirli bir değer veya nesne için bir ihtiyaç belirtir ve bir dışa aktarma ile bir değerin kullanılabilirliğini belirtir. Her içe aktarım, sözleşmesi nin bir dışa aktarım listesiyle eşleşir.

## <a name="next-steps"></a>Sonraki adımlar

Bu örnek için tam kodu indirmek için [SimpleCalculator örneğine (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/)bakın.

 Daha fazla bilgi ve kod örnekleri için [Yönetilen Genişletilebilirlik Çerçevesi'ne](https://github.com/MicrosoftArchive/mef)bakın. MEF türlerinin listesi için <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanına bakın.
